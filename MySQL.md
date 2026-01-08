# 第一章 SQL语句
## DDL（新增，修改，删除表结构）
 alter table student add/modify/change/drop/rename（修改表结构）
[[ddl语句总结.png]]
注意：
1. 均可以多行，比如add s_age int,add s_name varchar(50);(modify,change,drop同理)
2. FIRST  和AFTER 字段名可以用来控制字段位置
3. DDL语句还有create table，记住是小括号

## DML
update student set 字段1 = 值，字段2 = 值（ 修改满足条件的行）

联系记忆：
1. DDL是alter table student,DML是update student ,因为DDL是修改表结构，所以多一个table修饰符
2. 添加多个字段，DDL中的add/modify/change/drop都需要再写一个add,而update/insert不需要。比如insert into student  (s_name)  values ("hrx"),("dingdang");  --不需要写两个value
	  比如update student set s_name ="hrx",s_age = 18 where id =1;  --不需要写两个set