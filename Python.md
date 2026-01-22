# 第一章 Python介绍

包管理工具
Python优点：
- 代码简单，提升了开发效率
- 胶水语言，可以轻松调用，衔接，组合其他语言，如c/cpp
- 解释型语言，容易跨平台（缺点：但执行效率低）
- 能做的事情很多，适应性强

Python语法：
不用以分号结尾 
动态语言，变量的类型检查是在运行时进行的，且同一个变量名可以先后指向不同类型的值

## 第二章 基础语法
## 2.1 注释
- 文档注释""" """
- 单行注释#
## 2.2 输入函数input
```python
name,age = input("请输入您的年龄和姓名")
```

## 2.3 输出函数print
```python
print("English","Chinese","Mysql",sep="|",end="\n")
# sep是分隔符；end是结束符，默认为换行符
```

## 2.4 格式符号
最常用的是%，但已经逐渐被f-string取代
```python
#常用格式化符号
%d
%s
%f

age = int(input("age:"))  
name = input("name:")  
print("age=%d,name=%s" % (age, name))  #注意中间没有逗号
```
```python
#f-string格式
```

input如何多个赋值