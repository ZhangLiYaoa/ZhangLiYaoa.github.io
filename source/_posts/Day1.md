---
title: Day1:知识点记录
date: 2020-9-18
categories:
- web前端
tags:
- Javascript

---
 ## 函数声明方式
 
```javascript
/**
     * 函数声明方式1：直接声明方式
     */
    function func1(a, b, c) {
        console.log(a + b + c);
    }
    func1(2,3,4);//9
 
    /**
     * 函数定义方式二：函数表达式
     */
    var func2 = function (a, b, c) {
        console.log(a + b + c);
    };
    func2(1, 2, 3);//6
 
    /**
     * 函数定义三：通过构造函数方式
     * var 变量名 = new Function('形参1','形参2'....,'函数体');
     * 注意:参数可以有多个
     */
    var func3 = new Function('a', 'b', 'c', 'console.log(a+b+c)');
    func3(2, 23, 2);//27

```

## babel 的作用
- 第一种 比如你写了个箭头函数，但是ie不支持，babel就能够把你的箭头函数转化成 function
- 第二种 polyfill (corejs)

 ## 动态类型转换

Boolean类型
- "0" 转成 boolean是 true
- 0转成boolean是false

 js中的循环 
- for;forEach;map; while;for in ;for of

## 逗号表达式
```javascript

let a = 1;
let b = (a, 1); // 1

```

```javascript
let a = 2;
let b = (a, 1) ;// b = 1

```

# 算法题 删除排序数组中的重复项

- 遍历移除法  array.splice(index,howmamg)








