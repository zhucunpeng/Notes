## SQL小demo
## 1. 创建表格
- create table 系表
(
系号 int primary key,
系名 varchar(20) unique,
系主任 varchar(10) 
)

- create table 学生表
(
学号 char(4) primary key,
姓名 varchar(10),
性别 char(2) check(性别 in ('男','女')), 
年龄 int check(年龄 between 10 and 50),
入学年份 int,
籍贯 varchar(20),
手机号码 char(11),
系号 int,
班长学号 char(4) references 学生表(学号),
foreign key (系号) references 系表(系号) 
) 

- create table 课程表
(
课程号 char(3) primary key,
课程名 char(10) unique,
先修课 char(3),
学分 float check(学分> 0 and 学分<5) 
)

- create table 选课表
(
学号 char(4) references 学生表(学号),
课程号 char(3) references 课程表(课程号),
成绩 float check(成绩 between 0 and 100),
primary key(学号,课程号) 
)

2.
导入“学生表”时出错，原因为定义属性列“性别”时设其长度为char(1),在sql server中一个汉字占两个字符。 

3.
insert
into 学生表
values('0026','李四','女',20,2008,'广东','10010001000',null,'0105');

ps：
sql server2012 支持insert子查询结果
如insert into 学生表（学号）values（’0001’），可指定插入基本表的列。
另外，子查询可使用如select 姓名,(select 课程名 from 课程表 where 课程号='c01') from 学生表 where 学号='0105';这样的形式，在此例中子select结果应唯一，否则报错。
以及
insert 
into Student
values ('0002','美女',(select 成绩 from 选课表 where 学号='0101' and 课程号='c01'));
这样的形式。


insert 
into Student
select 学号,姓名,90 from 学生表;

90；表示新插入的这一列值均为90


4.
delete
from 学生表
where 学号='0026';

5.
alter table 学生表
alter column 姓名 char(12);

6.
alter table 学生表
add 电子邮件 char(20);

7.
alter table 课程表
drop constraint CK__课程表__学分__300424B4;

alter table 课程表
add constraint CK__课程表__学分 check(学分>0 and 学分<6);

8.
create clustered index INDEX__学生表__学号 on 学生表(学号);

PS：导入数据时系统已自动建立了相关clustered索引。


9.
方法一：
create view 课程名_成绩
as
select 课程名,成绩
from 选课表,课程表
where 选课表.课程号=课程表.课程号;


create view 课程名_最高分(课程名,最高分)
as
select 课程名,max(成绩)
from 课程名_成绩
group by 课程名;

方法二：
create view 课程_最高分(课程号,最高分)
as
select 课程号,max(成绩)
from 选课表
group by 课程号;


create view 课程__最高分
as
select 课程名,最高分
from 课程表,课程_最高分
where 课程表.课程号=课程_最高分.课程号;

PS：
Create view 课程名___最高成绩（课程名，最高成绩）
select 课程名,max(成绩)
from
(
select 课程名,成绩
from 选课表,课程表
where 选课表.课程号=课程表.课程号
)
group by 课程名;
无法执行：关键字 'group' 附近有语法错误。

但赋予内层查询一个临时表名即可成功’tmp’：
create view 课程名___最高成绩(课程名,最高成绩)
as
select 课程名,max(成绩) 成绩
from
(
select 课程名,成绩
from 选课表,课程表
where 选课表.课程号=课程表.课程号
)tmp 
group by 课程名;


10.
select 学生表.学号,姓名,总成绩,平均成绩
from 学生表,
(select 学号,sum(成绩),avg(成绩)
from 选课表
group by 学号)temp(学号,总成绩,平均成绩)
where 学生表.学号=temp.学号;

11.
update 学生表
set 年龄= (select avg(年龄)
		   from 学生表
		   where 系号=8)
where 系号=6;

12.
update 选课表
set 成绩=62
where 学号=(select 学号 from 学生表 where 姓名='曹洪') 
	  and 课程号=(select 课程号 from 课程表 where 课程名='操作系统');

13.
select 姓名,入学年份,籍贯 from 学生表;

14.
select * from 学生表 where 籍贯='山东';

15.
select 学号,姓名 from 学生表 where 年龄=(select min(年龄)from 学生表); 

16.
select 学号 from 选课表 where 课程号=  (select 课程号 from 课程表 where 课程名='数据库');
17.
select 学号,姓名 from 学生表 where 学号 in (select 学号 from 选课表 where 课程号= (select 课程号 from 课程表 where 课程名='编译技术' )) and 性别='女';

18.
select 课程号 from 选课表 where 学号= (select 学号 from 学生表  where 学号=(select 班长学号 from 学生表 where 姓名='典韦'))
19.
select 学号,姓名,系名 from 学生表,系表 where 姓名 like '%侯_' and 系表.系号=学生表.系号;

20.
select 课程名 from 课程表 where 课程名 like 'P%L__';

21.
select sum(成绩)
from 选课表
where 学号 = 
			(
			select 学号
			from 学生表
			where 姓名='甘宁'
			);

22.
select *
from 学生表
where 学号 in
			(
			select t1.学号
			from 选课表 t1,选课表 t2
			where t1.课程号 = 
							(
							select 课程号
							from 课程表
							where 课程名='数据库'
							) 
				 and t2.课程号 =
							   (
							   select 课程号
							   from 课程表
							   where 课程名='操作系统'
							   )
			     and t1.学号 = t2.学号
			);

23. select 学号,姓名
from 学生表
where 学号 not in
			(
			select 学号
			from 选课表
			where 课程号 = 
							(
							select 课程号
							from 课程表
							where 课程名='数据库'
							) 
			);
24.
select 学号,姓名
from 学生表
where 学号 in
			(
			select t1.学号
			from 选课表 t1,选课表 t2
			where t1.课程号 = 
							(
							select 课程号
							from 课程表
							where 课程名='数据库'
							) 
				 and t2.课程号 =
							   (
							   select 课程号
							   from 课程表
							   where 课程名='操作系统'
							   )
			     and t1.学号 = t2.学号
				 and t1.成绩 >=60 and t2.成绩 < 60
			);
25.
select 学号,姓名
from 学生表
where 学号 in(select 学号 from 选课表 where 成绩 < (select avg(成绩) from 选课表 where 课程号=(select 课程号 from 课程表 where 课程名='数据库')) and 课程号 = (select 课程号 from 课程表 where 课程名='数据库'));

26.
select 学号,姓名
from 学生表 s1
where not exists (select * from  选课表 sc1 where 课程号 not in (select 课程号 from 选课表 sc2 where 学号= ( select 学号 from 学生表 s2  where s2.姓名='貂蝉' )) and s1.学号=sc1.学号 ) and 姓名!='貂蝉' and (
	select count(*)
	from 选课表
	where 选课表.学号=s1.学号)=
	(select count(*)
	from 选课表
	where 学号=(select 学号 from 学生表 where 姓名='貂蝉')
	);

27.
select 学号,姓名
from 学生表 s1
where not exists  (select * from 选课表 sc2 where sc2.学号=(select 学号 from 学生表 where 姓名='貂蝉') and (sc2.课程号 not in (select 课程号
from 选课表 sc3 where sc3.学号=s1.学号)))and ((select count(*) from 选课表 where 选课表.学号=s1.学号) > (select count(*) from 选课表 where 学号=(select 学号 from 学生表 where 姓名='貂蝉')));
28.

