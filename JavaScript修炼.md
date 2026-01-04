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
	- 解释型语言
4. 作用域（scope）
	- 分为全局作用域和函数作用域和块级作用域
	- if，for，while是块级作用域(块级作用域必函数作用域更节省cpu和内存资源)。块级作用域起作用的条件：必须要用let和const；必须要在if，for，while控制流语句里（不是函数）
```js
		// 1. var 容易逃逸（不推荐）
if (true) {
    var secret = "我知道了"; 
}
console.log(secret); // 依然能打印出 "我知道了"，不安全

// 2. let 完美锁定（推荐）
if (true) {
    let lockedSecret = "你看不见我";
}
// console.log(lockedSecret); // 这里会报错，变量被安全地锁在块里了

---


// 场景：在 if 块中使用变量
if (true) {
    var escapee = "我是 var，我逃出去了"; 
    let prisoner = "我是 let，我被关住了";
    const guard = "我是 const，我也被关住了";
    
    console.log(prisoner); // 块内访问：正常
}

console.log(escapee);  // 块外访问：正常
// console.log(prisoner); // 块外访问：报错！ReferenceError
// console.log(guard);    // 块外访问：报错！ReferenceError
```
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
1. function（）一般写法
- var a = function（）{……}，实际上是创建了一个函数对象，把这个对象的地址交给了a
	- 即使函数定义里没写参数，但是也有个隐形参数arguments来存储
	- 不需要声明返回值类型和参数类型，变量可以指向任何类型的值，类型由运行时决定
	- function（）的两个写法
```js
let a = function(){
	let sum = 0;
	for(let i = 0;i<arguments.length;i++){
		sum+=arguments[i];
	}
	return sum;
}
let a1 = a(1,2,3,4);
console.log(a1);	   //10
console.log(a);	  //打印匿名函数的代码块

function add(){
	let sum = 0;
	for(let i=0;i<arguments.length;i++){
		sum+=arguments[i];
	}
	return sum;
}
let a2 = add(1,2,3,4);
console.log(a2);
```
2. 闭包
	- 