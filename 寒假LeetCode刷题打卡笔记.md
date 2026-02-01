# 11/31
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

### 解法2 哈希：