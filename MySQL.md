# 第一章 SQL语句
## 1.1 DDL（新增，修改，删除表结构）
 alter table student add/modify/change/drop/rename（修改表结构）
[[ddl语句总结.png]]
注意：
1. 均可以多行，比如add s_age int,add s_name varchar(50);(modify,change,drop同理)
2. FIRST  和AFTER 字段名可以用来控制字段位置
3. DDL语句还有create table，记住是小括号

## 1.2 DML
update student set 字段1 = 值，字段2 = 值（ 修改满足条件的行）
insert into student (s_name,s_age) values (),();   (插入多行值)
delete from student where id =1;                      (删除指定行)

联系记忆：
1. DDL是alter table student,DML是update student ,因为DDL是修改表结构，所以多一个table修饰符
2. 添加多个字段，DDL中的add/modify/change/drop都需要再写一个add,而update/insert不需要。比如insert into student  (s_name)  values ("hrx"),("dingdang");  --不需要写两个value
	  比如update student set s_name ="hrx",s_age = 18 where id =1;  --不需要写两个set

区分：truncate（ddL）和delete from（DML）
truncate清空后主键自增也会清除，delete from 不会！

思考：为什么insert into 不能和alter add一样可以指定位置
1. 在关系型数据库里，数据库将表视作集合，集合内的元素是没有物理顺序的，ta在哪个位置并不重要
2. 性能考虑，如果要指定插入的话，那数据库每插入一个元素都要往后挪动，会极大地影响运行速度
3. 我们最后可以通过select统一解决，不需要多此一举

# 1.3 DQL
## 1.3.1 where过滤：
1. =,!=,<,>             精准查询，比如select * from student where s_id =1;
2. %，_                   模糊查询，比如select * from student where s_id like "2%";(记住要加“”)
3. in,between and  范围查询,   比如select * from student where s_id in (1,2,3);(记住in要加小括号)
4. is null,is not null 判断为空，比如select * from student where s_id is not null;
5. and,or,not,xor    逻辑组合,  比如select * from student where s_age<20 and score >80;
xor  异或（互斥筛选），可以运用于礼券发放场景，假设一个电商活动，规定“新注册用户”或“消费满 1000 元的用户”可以领券，但“既是新用户又消费满 1000 元”的人不能重复领

## 1.3.2 order by排序：
1. 多字段排序   order by s_age desc,score asc;
2. 限制查询       order by score desc limit 2;(取成绩最高的两位)     
             order by score desc limit 10,2(取成绩第十一和十二位)
3. desc为降序，asc为升序（默认asc），如果排序字段为字符串，则按a-z排序

## 1.3.3 聚合函数&&分组：
1. count()  统计行数
   select count( * ) from student ;    统计所有行，含null
   select count(s_name) from student;     统计s_name不为空的行
2. sum()   求和
3. avg（）  取平均值
4. max()  min()    取最大值，最小值
5. round()   四舍五入 
 select round(85.6);    --85
 select round(85.6,2)   --85.00

注意：group by分组后，select查询只能查询分组的字段，否则没有实际意义会报错
比如select class_id,count( * ) from student group by class_id;   (按谁分组查询谁)

having则是过滤分组后的数据

# 第二章 约束
## 2.1 字段约束
### 2.1.1 外键约束
1. 学生表建表时候引入外键
```mysql
create table if not exists student(
	…………
	foreign key (class_id) references class(class_id)
) ;

--注意：一般都是用alter table增加外键，因为一般是先建表再连线（解耦的原理）
```
2. alter table add引入外键
```mysql
alter table student
add class_id int,                    --增加字段
add constraint fk_student_class      --增加约束
foreign key(class_id) references class(class_id);

--级联选项（负责的是外键字段，即id,其他字段可以任意修改）
on delete set null --班级删除，学生表置空
on delete cascade  --班级删除，学生表跟着自动删除
on delete restrict --只要班级里还有学生，就不准删除该班级（默认）

--update同理
on update set null
on update set cascade
on update restrict(默认)
```

2.1.2 字段属性
![[key属性.png]]
MUL一般为外键
# 第三章 查询
分为多表查询，子查询（都属于DQL语句，单独划为一章是因为这个知识点比较杂乱）
## 3.1 多表查询
先找连接条件on，再选择拼法（inner join / left join / right join）
### 3.1.1 inner join(等同于join)
```mysql
SELECT 
    s.s_name, c.class_name  -- 选出你想要的列
FROM 
    student AS s            -- 主表，起个别名 s
INNER JOIN 
    class AS c              -- 连上的表，起个别名 c
ON 
    s.class_id = c.class_id; -- 连接条件：两个 ID 必须相等
```
### 3.1.2 right join和left join
![[left jon 和right join.png]]