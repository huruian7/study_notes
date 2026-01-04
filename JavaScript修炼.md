# 第一章 新手村
## 1.1 法宝
### 1.1.1 github同步云端
- [x] obsidian连接github，实现本地和云端同步存储
方法一：插件Git，可以自动提交同步
方法二：在本地文件夹目录下输入cmd
```bash
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
### 1.2.1概念
1. var的定义
	- var是一个什么数据类型都能装的变量。注意：var是老一代的声明方式，ES6标准更喜欢用let（变量），const（常量）
	- var&&let&&const
		![[var和let&&const.png]]
2. 三种输出
	- alert（）  弹出警告框
	- document.writr（）  把内容输出到网页上
	- console.log（）  在控制台打印信息
3. JavaScript特点
	- 解释型
4. 作用域（scope）
	- 分为全局作用域和函数作用域
### 1.2.2 Array数组
1. JS数组和传统数组的区别
	- JS里的数组相当于大杂烩，长度可变，类型不限；传统数组固定大小，且只能装同一钟数据
2. 常见方法
```js
	var arr = ["A", "B", "C"];

// 1. push(): 往屁股后面塞
arr.push("D");  // 结果：["A", "B", "C", "D"]

// 2. pop(): 把屁股后面的拿出来
arr.pop();      // 结果：["A", "B", "C"]

// 3. splice(): 乾坤大挪移（最强法术）
// 语法：splice(开始位置, 删几个, 插入啥)
arr.splice(1, 1, "M"); // 从索引1开始，删1个(B)，换成"M" -> ["A", "M", "C"]

// 4. join(): 合体
var str = arr.join("-"); // 把数组连成字符串 -> "A-M-C"
```
### 1.2.3 函数
