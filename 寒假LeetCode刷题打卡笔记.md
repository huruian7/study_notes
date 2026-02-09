# 2/7

## 一，random模块（python）
### 1,1 随机生成整数
randint(a,b)                       返回[a,b]之间的随机整数
randrange(a,b,step)          返回[a ,b)步长为step的随机整数

1. 思考题1：和range()有什么区别？
回答：range()是python的内置函数，有三种调用方式，用来控制循环次数，返回的是一个左闭右开的Range对象

range的三种调用方式:
range(n)
range(a,b)
range(a,b,step)

 2. 思考题2：随机生成取值边界如何界定？
 回答：range，randrange，random都是左闭右开；randint，uniform都是闭区间
### 1,2 随机生成浮点数
random()                       返回[0.0,1.0)之间的随机浮点数
uniform(a,b)                  返回[a,b]之间的随机浮点数

### 1,3 随机选择序列中的一个元素
choice(seq)                                                 等概率返回一个元素
choices(seq, weights=weights, k=?)          有放回抽样，通过k参数返回多个元素(可能重复)，可通过weights参数控制权重
```python
def choices_demo():
	students = ["hrx","gjw","xxy","zht"]
	# weights权重特点是不需要和为1或100，python会自动处理数据
	# weights必须是浮点数或整数，且必须与列表一直
	weights = [1,1,1,7]   
	for i in range(5):
		print(random.choices(students, weights=weights, k=2))
		time.sleep(0.5)
```

sample(seq, k)                                           无返回抽样，返回的k个列表元素无重复
shuffle(seq)                                               打乱顺序

### 1.4 随机种子
种子是输入给算法的初始数字，只要初始种子相同，在同一算法下，得到的结果也相同。只要在调用random模块函数前设置seed值，那么后续随机的结果就会被固定，所以也叫伪随机
random.seed(10)
```python
#固定序列（循环外）
def seed_demo1():
	random.seed(10)
	for i in range(100):
		print(random.randint(1,7))
		time.sleep(0.5)
		
#固定值（循环内）
def see_demo2():
	for i in range(100):
		random.seed(10)
		print(random.randint(1,7))
		time.sleep(0.5)
```


### 1.5 import和from import
![[Pasted image 20260207145556.png]]

# 2/8

## 题目1 两数之和
### 题目描述：
给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出 **和为目标值** _`target`_  的那 **两个** 整数，并返回它们的数组下标。你可以假设每种输入只会对应一个答案，并且你不能使用两次相同的元素。你可以按任意顺序返回答案

### 解法1 暴力求解：
使用双重for循环，i遍历记录第一个数字，j遍历记录第二个数字,if判断两数之和是否等于target。判断成功返回索引，失败返回0
代码如下：
```java
class Solution{
	public int[] twoSum(int [] nums, int target){
		for(int i = 0; i <nums.length; i++){
			for(int j=i+1; j<nums.length; j++){
				if(nums[i] + nums[j] == target){
					return new int []{i,j};
				}
			}
		}
		return new int[0];
	}
}
//时间复杂度为O(n^2)
```

## 题目1 两数之和
### 题目描述：
两数之和，暴力求解在数据繁杂的情况下时间复杂度太高，引入哈希表寻求更优解

### HashMap知识点：
1. HashMap,使用泛型，必须要用包装类（Integer,String等），因为泛型的类型擦除要求必须是Object对象
```java
Set                                                   Map
仅存储单个对象                                          存储键值对
不允许元素重复                                          key不允许重复，value允许

Ps:Set,Map均为接口，ta的实现类HashSet,HashMap均无序
```

2. HashMap具体使用
```java
构造器：
Map<key,value> 哈希表名 = new HashMap<>();//向上转型的写法
//其中，key具有唯一性；不可更改性；且如果value为自己构造的对象，必须重写hashCode(),equal()方法
```

```java
成员方法：
Map<String,String> studentID = new HashMap<>();
1.put() 向表中添加元素
studentId.put("6020221970","hrx");
2.get() 通过key找到value并返回
String value = studentID.get(6020221970"");
3.size() 返回表的大小
注意数组的length不是方法，不用加小括号
4.keySet() 返回Map中所有的Key,返回形式是Set
Set<String> keySet = studentID.keySet();
5.containsKey 判断HashMap是否包含该key
if(hashMap.containsKey(key))
{...}
```

```java
遍历：
通过get方法和keySet方法以及增强for循环（也叫for-each）实现遍历
假设现在已经拥有了一个HashMap，名字为studentID，则遍历代码如下：
Set<String> keySet = studentID.keySet();
for(String key : keySet){
	System.out.println("key:"+key+"\t"+"value:"+studentID.get(key));
}
```

### 解法2 哈希表
```java
import java.util.Map;

class Solution {

    public int[] twoSum(int [] nums, int target) {
        //HashMap<数字，索引>
        Map<Integer,Integer> hashMap = new HashMap<>();
        for(int i = 0; i < nums.length; i++){
            int complement = target -nums[i];
            //如果补数在哈希表中就代表找到了两个数，通过哈希表可以直接找到两个数的索引
            if(hashMap.containsKey(complement)){
                return new int[]{hashMap.get(complement),i};
            }
            //如果补数不在哈希表中则添加补数进哈希表，哈希表就是一个关于target的补数表
            hashMap.put(nums[i],i);
        }
        return new int[0];
    }
}
//时间复杂度为O(n),平均情况为O(1)，n/n==1
```

# 2/9
## 一，selenium模块
## 1.1 Options (浏览器配置类)
### 1.1.1 常用函数
1. add_argument("") 
向浏览器添加命令行开关
```python
--headless  无头模式
--no-sandbox  禁用沙盒模式，牺牲安全性换取兼容性
--start-maximized  启动最大化
```
2. add_experimental_option("","") 
添加实验性选项，深度控制浏览器，格式为键值对
```python
("detach",True)  运行脚本结束后不退出浏览器
("excludeSwitches",["enable-automation"])   排除开关，value为列表，这行代码的意思是取消“正受自动测试软件控制”提示
```
## 1.2 webdriver对象
### 1.2.1 常用函数
1. get()  打开网页
2. close()  关闭当前标签页
3. quit()    退出浏览器
4. maximize_window  最大化
5. minimize_window  最小化
6. refresh   刷新当前页面
7. 