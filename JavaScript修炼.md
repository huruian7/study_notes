# 第一章 新手村
## 1.1 法宝
### 1.1.1 github同步云端
- [x] obsidian连接github，实现本地和云端同步存储
方法一：插件Git，可以自动提交同步
方法二：在本地文件夹目录下输入cmd
```
git add .                               //把该目录下的所有文件都添加到箱子里
git commit -m "新增了JavaScript修炼文件"  //-m是告诉git这次提交的注释，必须有，方便回溯
git push origin JavaScript              //origin是远程仓库代号，JavaScript是当前分支

补充：
git init   把普通的文件夹变为受git保护的文件夹
git status 可以看当前的状态（发生了哪些变化）
```
### 1.1.2  obsidian快捷操作
1. ctrl家族
	- ctrl+数字  切换标题
	- ctrl+p     打开命令面板    
	- ctrl+l     无序列表/有序列表/待办
	- ctrl+e     切换编辑/阅读模式
2. 符号
	- [[]]       输入双中括号可以链接另一份笔记
---

## 1.2 基础语法
### 1.2.1变量
1. var的定义
   - var是一个什么数据类型都能装的变量（注意：var是老一代的声明方式，ES6标准更喜欢用le）
- alert（），document.write（），consol.log()方法
### 1.2.2数组
1. JS里和传统编程语言数组的区别
	- JS里的数组相当于大杂烩，什么数据类型，都可以装
- 数组的使用，join，splice，push，pop

