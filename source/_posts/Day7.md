---
title: Day7:知识点记录
date: 2020-9-24
categories:
- web前端
tags:
- Javascript
---
# 结构赋值

可以立即将一个对象或者数组映射到多个变量上。

## 数组结构优雅写法

```javascript
const [firstName,surName] = "lily Kantor".split(' ')
console.log(firstName,surName) //lily Kantor
console.log("lily Kantor".split(' ')) //["lily", "Kantor"]
```

## 数组的结构

- 将结构中的各个元素复制到变量中达到结构的目的,`数组本身并没有被修改`
- 对于不想要的元素,可以通过`逗号`来把它丢弃
- 可以是任何迭代的对象，不仅仅是数组。

```javascript
let [a,b,c] = "abc"    //["a", "b", "c"]
let [one,two,three] = new Set([1,2,3])
console.log([one,two,three])  //[1, 2, 3]
```

- 可以赋值给等号左侧的任何内容

```javascript
let user = {};

[user.name,user.surName] = "lily Kantor".split(' ')

console.log(user.name) //lily
```

- 与entries() 方法进行循环操作

```javascript
let user = {
  name:"Join",
  age:20
}

//循环遍历键值 (同样适用于Map)

for (let [key, value] of Object.entries(user)) {
  console.log(`${key}:${value}`); // name:John, then age:30
}

```

- 交换变量的值(技巧)

```javascript
let guest = "jane";
let admin = "Pete";

[guest, admin] = [admin, guest];

console.log(`${guest} ${admin}`) //Pete jane
```

### 剩余参数  

...

### 默认值

默认值可以是复杂的表达式,也可以是函数调用

## 对象的结构

- 如果使用已有的变量,而不是用let ,我们需要用括号() ,
  把它括起来,否则js会将主代码流当作一个代码块,进行语句分组。


```javascript
let salaries = {
  "Join":100,
  "Pete":200,
  "Mary":30
}

topSarays(salaries){
  let max = 0;
  let maxName = null;
  for(let [key,value] of Object.entries(salaries)){
    if(max < value){
      max = value
      maxName = key
    }
    return maxName
  }
}
topSarays({})

```

# 算法题 加一

- 给定一个由整数组成的非空数组所表示的非负整数,在该数的基础上加一。
- 最高位数字存放在数组的首位，数组中每个元素只存储单个数字。
- 你可以假设除了整数0之外,这个整数不会以零开头。

示例一 

```txt
输入:[1,2,3]
输出:[1,2,4]
解释：输入数组表示数字123。
```
```javascript
/**
 * @param {number[]} digits
 * @return {number[]}
 */
const plusOne = (digits) => {  
    for(let i = digits[i].length;i >= 0;i--){
      if(digits[i] !== 9){
        digits[i]++;
        return digits[i]
      }else{
        digits[i] = 0
      }
    }
     const result = [1,...digits]
     return result
}

```
