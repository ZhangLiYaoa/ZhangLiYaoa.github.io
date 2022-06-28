---
title: Day5:知识点记录
date: 2020-9-22
categories:
- web前端
tags:
- Javascript
---

# 136 只出现一次的数字(位运算的妙用)

给定一个非空整数数组，
除了某个元素只出现一次以外，
其余每个元素均出现两次。
找出那个只出现了一次的元素。

 - 具有线性时间复杂度，最好不会使用额外空间

示例
```txt
输入: [4,1,2,1,2]
输出: 4
```

-  n ^ n == 0 ; n ^ 0 = n; 
- 遵循交换律

```javascript
4 ^ 1 ^ 2 ^ 1 ^ 2
1 ^ 1 ^ 2 ^ 2 ^ 4   //交换律
    0 ^ 2 ^ 2 ^ 4
       2 ^ 2 ^ 4
           0 ^ 4     //==4
```
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
   let result = nums[0]  //获取数组的第一位
   for(let i = 1;i<nums.length;i++){
       result = result ^ nums[i]  //异或运算
   }
   return result
};

```
weakMap和weakSet 用来解决什么问题？Map和Set 有什么区别

 
