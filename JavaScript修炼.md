# 第一章 初入新手村
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


如果连接github失败
#### ⚠️ 网络连接排错 (Port 443)
1. **排查端口**：通过 `系统设置 > 代理` 查看。
2. **确认监听**：使用 `netstat -ano | findstr "LISTENING"` 确认端口号（如 10810）是否活动。
3. **配置 Git**：
   - 开启代理：`git config --global http.proxy http://127.0.0.1:10810`
   - 关闭代理：`git config --global --unset http.proxy`
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
# 第二章 筑基
## 2.1闭包
```js
## 1.3 闭包 (Closure)
* **定义**：函数嵌套函数，内部函数使用了外部函数的变量，且内部函数被返回到了外部。
* **三大好处**：
    1. **私有化**：外部无法直接访问变量，必须通过特定接口。
    2. **持久化**：变量不会在函数执行后消失，能记住状态。
    3. **防污染**：避免使用全局变量，让代码更整洁安全。
       
function test(){
	let a = 0;
	return function(increment){
		a+=increment;
		console.log(a);
	}	
}
let inner = test();
inner(1);//第一次调用
inner(1);//第二次调用
//该函数可以实现计数效果

inner = null;//需要垃圾回收
inner(1);    //报错，this is not a function
```
垃圾回收机制
1. 执行inner=null；断开连接，变量inner不再指向那个内部函数对象
2. 内部函数不再被变量引用，函数被孤立，变量a也会随之消失
3. JavaScript的垃圾回收扫描到这些不可达的变量会自动销毁

## 2.2自执行函数
1. 定义：在定义后便立刻执行的函数，没有名字，一般配合闭包使用
```js
let inner = (function(){
	let a=0;
	return function(increment){
		a+=increment;
		console.log(a);
	}
})()
inner(1);
```

2. 提问：为什么要写的这么奇怪？
	- 核心目的是用完即丢，不留痕迹！！！第一个括号包裹函数体，第二个括号立即执行，定义即运行
	- 匿名保护，直接承接，避免全局污染，访问变量a只有inner这一个外部接口