# bower 小知识
## 安装 
- ` npm i -g bower `

## 使用小命令
- cache:bower缓存管理
- help:显示Bower命令的帮助信息
- home:通过浏览器打开一个包的github发布页
- info:查看包的信息
- init:创建bower.json文件
- install:安装包到项目
- link:在本地bower库建立一个项目链接
- list:列出项目已安装的包
- lookup:根据包名查询包的URL
- prune:删除项目无关的包
- register:注册一个包
- search:搜索包
- update:更新项目的包
- uninstall:删除项目的包

## 使用小贴士
- 初始化项目`bower init`
  + 会出现一些基本信息
  ```
  {
  "name": "bb_boot",
  "version": "0.0.1",
  "authors": [
    "savokiss <jaynaruto@qq.com>"
  ],
  "moduleType": [
    "amd"
  ],
  "license": "MIT",
  "ignore": [
    "**/.*",
    "node_modules",
    "bower_components",
    "js/lib",
    "test",
    "tests"
  ],
  "dependencies": {
  }
}
  ```
  
- 包的信息 `bower info jquery`
 + 会看到jquery可用的版本信息
- 安装指定版本`bower i jquery#1.9.0
 
 
