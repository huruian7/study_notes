# 第一章 Python介绍

## 1.1 包管理工具

## 1.2 Python优点：
- 代码简单，提升了开发效率
- 胶水语言，可以轻松调用，衔接，组合其他语言，如c/cpp
- 解释型语言，容易跨平台（缺点：但执行效率低）
- 能做的事情很多，适应性强

## 1.3 Python语法：
不用以分号结尾 
动态语言，变量的类型检查是在运行时进行的，且同一个变量名可以先后指向不同类型的值
解包：将一个包裹拆开，把里面的元素分别赋值给不同的变量

## 第二章 基础语法
## 2.1 注释
- 文档注释""" """
- 单行注释#
## 2.2 输入函数input
```python
#split()默认以空格作为分隔符，将用户输入的一整行字符串拆分成一个列表
name,age = input("请输入您的年龄和姓名").split()

#input默认接受的全部都是字符，map()可以强制转换
age，height = map(int,input("请输入您的年龄和身高")).split()
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