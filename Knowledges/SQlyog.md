##　SQLyog的一些基本操作语句
- 详情参考一：http://blog.csdn.net/github_35033182/article/details/52050150
- 详情参考二：http://www.linuxidc.com/Linux/2016-01/127757.htm
- 详情参考三：http://blog.csdn.net/a88055517/article/details/6736284

-- 删除数据
DELETE FROM USER WHERE username='lisi';

-- 查询所有列
SELECT * FROM stu;

-- 查询指定列
SELECT sname,age FROM stu;

-- 查询性别为女，并且年龄为50的记录
SELECT * FROM stu WHERE gender='female' AND age=50;

-- 查询学号为S_1001，或者姓名为liSi的记录
SELECT * FROM stu WHERE sid='s_1001' OR sname='lisi';

-- 查询学号为S_1001，S_1002，S_1003的记录
SELECT * FROM stu WHERE sid IN ('s_1001','s_1002','s_1003' );

-- 查询学号不是S_1001，S_1002，S_1003的记录
SELECT * FROM stu WHERE sid NOT IN ('s_1001','s_1002','s_1003' );

-- 查询年龄为null的记录
SELECT * FROM stu WHERE age IS NULL;

-- 查询年龄在20到40之间的学生记录
SELECT * FROM stu WHERE age BETWEEN 20 AND 40; -- 或者
SELECT * FROM stu WHERE age>=20 AND age<=40;

-- 查询性别非男的学生记录
SELECT * FROM stu WHERE gender !='male'; -- 或者
SELECT * FROM stu WHERE gender <>'male';

-- 查询姓名不为null的学生记录
SELECT * FROM stu WHERE sname IS NOT NULL; -- 或者
SELECT * FROM stu WHERE NOT sname IS NULL;

-- 查询姓名由5个字母构成的学生记录
SELECT * FROM stu WHERE sname LIKE '_____';

-- 查询姓名由5个字母构成，并且第5个字母为“i”的学生记录
SELECT * FROM stu WHERE sname LIKE '____i';

-- 查询姓名以“z”开头的学生记录
SELECT * FROM stu WHERE sname LIKE 'z%';

-- 查询姓名中第2个字母为“i”的学生记录
SELECT * FROM stu WHERE sname LIKE '_i%';

-- 查询姓名中包含“a”字母的学生记录
SELECT * FROM stu WHERE sname LIKE '%a%';

-- 去除重复记录
SELECT DISTINCT * FROM stu;
