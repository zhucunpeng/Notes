# Nginx反向代理工作原理简介与配置详解
- 参考资料1：http://blog.sina.com.cn/s/blog_13cc013b50102wbpw.html
- 参考资料2：http://blog.csdn.net/jethai/article/details/52345302
- 参考资料3：http://www.cnblogs.com/crazyacking/p/5138146.html
- 参考资料4：http://www.open-open.com/lib/view/open1417488526633.html

## 1. 下载 nginx
- 现在最新版的是nginx-1.10.0
- 下载地址：http://nginx.org/en/download.html
- 下载地址：http://pan.baidu.com/s/1skNT7zv
 
## 2. 配置核心文件
nginx -t -c  /etc/nginx/nginx.conf检测配置文件是否有语法错误
ps aux|grep nginx

### 设置工作进程数,一般与cpu的核数一致
work_processes 2;
events ｛
### 单个进程最大连接数，超过就等待在队列排队
worker_connections 1024;
｝
http｛
### 日志格式定义
log_format main '$remote_addr - $remote_user [$time_local]  "$request" '
                '$status $body_bytes_sent "$http_refer" '
                '"$http_user_agent" "$http_x_forward_for"';

### Linux内存 操作系统和驱动程序运行在内核层，应用程序运行在用户层
sendfile on;

keepalive_timeout 65;


### 启用压缩功能
gzip on;


### 反向代理缓存目录
proxy_cache_path /data/proxy/cache levels=1:2 keys_zone=cache_one:500m inactive=1d max_size=1g;



### 负载均衡
upstream my_server_pool {
server 192.168.1.109:80 weight=1 max_fails=2 fail_timeout=30;
server 192.168.1.10:80 weight=2 max_fails=2 fail_timeout=30;
}



### 虚拟主机配置
server ｛
listen 192.168.1.1:80  default_server;
server_name   www.example.org;
root /var/www/web1;
｝



server{
listen 80;
server_name   www8.example.org;
root /var/www/web2;

### 根据不同的浏览器URL重写
if($http_user_agent ~ Firefox){
rewrite ^(.*)$  /firefox/$1 break; 
}
if($http_user_agent ~ MSIE){
rewrite ^(.*)$  /msie/$1 break; 
}

### 实现域名跳转
location / {
rewrite ^/(.*)$ https://web8.example.com$1 permanent;
}

index index.html;
### 日志缓冲区
access_log /var/log/nginx/www8.example.com-access.log main buffer=32k;
error_log /var/log/nginx/www8.example.com-error.log warn;
### 什么样的日志文件描述符放到缓存中
open_log_file_cache max=1000 inactive=20s min_uses=2 valid=1m;
### 防止盗链
location ~* \.(gif|jpg|png|swf|flv)$ {
valid_referers none blocked www.test.com*.test.com;
if($invalid_refer) {
rewrite ^/(.*) http://www.test.com/block.html;
}
}

### 浏览器本地缓存设置
### 静态页面
location ~ .*\.(gif|jpg|jpge|png|bmp|swf|flv)$ {
expires 30d;
}
### 动态页面
location ~ .*\.(js|css)$ {
expires 1h;
}

location /data {
### 自动索引开启，列出目录下的文件
autoindex on;
### 将/data目录重写为/bbs
rewrite ^/data/?$ /bbs permanent;
### 控制访问，相当于防火墙
deny 192.168.0.132；
allow 192.168.0.0/24;
allow 192.168.1.1;
deny all;
### 只允许.htpasswd文件中的用户访问
### 账号生成口令htpasswd -c /home/test1/a/.htpasswd username 
### 系统会要求输入两遍该用户的密码。
### 修改密码也是同样 htpasswd -c /home/test1/a/.htpasswd username
auth_basic "AwstatAuth";
auth_basic_user_file /etc/nginx/.htpasswd;
}

location /bbs {
index index.html
}
location /b {
### uri别名，路径过长简写
alias /var/www/web2/data/redhat;
}

location /nginx_status {
### nginx状态检查，用于监控nginx状态
stub_status on;
### 不记录日志
access_log off;
}


### 自定义错误页面
error_page 403 404  /40x.html;
location /40x.html {
root /var/www/error;
}

}

### https访问 https://
server {
listen 443;
server_name web8.example.com;

ssl on;
ssl_certificate  /etc/pki/tls/certs/httpd.crt;
ssl_certificate_key /etc/pki/tls/private/httpd.key;

ssl_session_timeout 5m;

ssl_protocols SSLv2 SSLv3 TLSv1;
ssl_ciphers HIGH:!aNULL:!MD5;
ssl_prefer_server_cihers on;

location / {
root /var/www/web3;
index index.html index.htm
}

### url重写和反向代理同时进行
location /sports/ {
proxy_pass http://192.168.0.2;
}

location /news/ {
proxy_pass http://192.168.0.109:8080/bbs;
proxy_cache_valid 200 10m;
proxy_cache_valid 304 1m;
proxy_cache_valid 301 302 1h;
proxy_cache_valid any 1m;
proxy_cache_key $host$uri$is_args$args;
proxy_set_header Host $host; //后端日志记录的是远端地址而不是代理服务器本身
proxy_cache cache_one;//引用cache
proxy_set_header X-Forwarded-For $remote_addr;
}

### 流媒体限速
location /downlod {
limit_rate_after 20m;//前20M不限速
limit_rate 256K;
}

### 反向代理加负载均衡
location /sms {
proxy_pass http://my_server_pool；
}
}
｝


### nginx uri匹配规则(location)

语法：location [=|~|~*|^~]  /uri/  {...}

=:精确匹配
~:区分大小写
~*:不区分大小写
^~:禁止正则表达式匹配

地址重写rewrite
if指令\return 指令\set rewrite 指令


301 permanent 永久重定向，新网址完全继承旧网址，旧网址的排名等完全清零
302 redirect 临时重定向 对旧网址没有影响，但新网址没有排名
304 代表页面来自缓存

rewrite 最后一项参数为flag标记
1.last 浏览器URL地址不变
2.break 浏览器URL地址不变
3.redirect 浏览器会显示跳转后的url
4.permanent 浏览器会显示跳转后的url

last会对server标签重新发起一个新的请求，再次进入server块，重试location匹配

break 直接使用当前location的资源来访问，不再执行location里余下的语句，完成本次请求

一般在根location或server标签中推荐使用last标记，在非根location中，使用break 

nginx日志管理(缓存）
日志分割脚本(防止日志文件变得很庞大)，每天分割一次
vim /data/logs.sh
#! /bin/bash
### Nginx日志存放位置
logs_path="/data/logs/"
### 将日志改名
mkdir -p ${logs_path}${date -d "yesterday" +"%Y"}/${date -d "yesterday" +"%m"}/
mv ${logs_path}access.log  ${logs_path}${date -d "yesterday" +"%Y"}/${date -d "yesterday" +"%m"}/access_${date -d "yesterday" +"%Y%m%d"}.log
### 重启Nginx服务，重新生成access.log文件
service nginx reload


### 创建计划任务
### crontab -|
01 01 * * * /bin/bash /data/logs.sh

负载均衡
upstream my_server_pool {

}

把指定的输入文件拷贝到指定的输出文件中，并且在拷贝的过程中可以进行格式转换
dd if=/dev/zero of=test bs=1M count=100
