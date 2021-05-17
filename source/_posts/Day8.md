---
title: Day8:知识点记录
date: 2020-9-25
---
# 日期和时间

283 移动零

```javascript
const moveZeroes = (nums) =>{
   let j = 0;
   for(let i =0;i<nums.length;i++>){
     if(nums[i]!== 0){
       nums[j] = nums[i];
       j++;
     }//非零元素处理
   }
   for(i=j;i<nums.length;i++>){
     nums[i] = 0;
   }
   return nums;
}


### new Date()
我们通过时间戳来创建日期
并且可以使用data.getTime() 将现有的Date对象转换为时间戳

>01.01.1970之前的日期带有负的时间戳  new Date(-24 * 3600 * 1000);

- 如果只有一个参数,并且是字符串,那么他会被自动解析。
- 使用当前时区中给定的组件创建日期，只有前两个参数是必须的
- 时间度量精确到1毫秒(1/1000秒)

## 访问日期组件
 从 Date 对象中访问年、月等信息有多种方式：
- getFullYear() 获取年份(4位数)
- getMonth() 获取月份,从0到11
- getDate() 获取当月的具体日期，从1到31
- getHours()
- getMinutes()
- getSeconds()
- getMilliseconds()


- getDay() 获取一周中的第几天

​```txt
UTC(协调世界时) UTC时区知名之一，比如UTC(协调世界时)提前0个小时,它被用作标准时间。
```

- getTime() 返回日期的时间戳 从1970-1-1 00:00:00 UTC+0开始到现在所经过的毫秒数

- getTimezoneOffset() 返回  UTC与本地时区之间的时差,以分钟为单位。

## 设置日期组件

- setFullYear() 
- setMouth()
- setDate()
- setHours()
- setMinutes()
- setSeconds()
- setMilliseconds()
- setTime() 使用自1970-01-01 00:00:00 UTC+0以来的毫秒数来设置整个日期

## 日期转化为数字,日期差值

> 日期可以相减,相减的结果是以毫秒为单位时间差。这个作用可用于时间测量。

### Date.now()

测量时间间隔

返回当前的时间戳 相当于new Date().getTime() 
许多天之前是哪个月几号

