---
title: Day4:知识点记录
date: 2020-9-21
categories:
- web前端
tags:
- Javascript
---

- for of 的原理？
- Iterable object 迭代器如何实现，怎么写的？
- 字面量为什么循环不了？
- 0.1+0.2   为什么会有不等于0.3,怎么解决这个问题？
- 字符串为啥是不变得？
- 双精度64位?

# Map and Set(映射和集合)

## Map   类似数组

Map 是一个带键的数据项的集合，就像一个 Object 一样。 但是它们最大的差别是 Map 允许任何类型的键（key）。

属性和方法

- new Map()  创建map
- map.set(key,value) 根据键存储值
- map.get(key) 根据键来返回值，如果map中不存在对应的key,则返回undefined。
- map.has(key) 如果key存在返回true，否则返回false。
- map.delete(key) 删除指定键的值
- map.clear(key) 清空map
- map.size 返回当前元素的个数

> Map和对象不同，Map键不会转换为字符串,键可以是任何类型
> Map 可以将对象作为键

```txt 
Map 是怎么比较键的？
Map 使用SameValueZero 算法来比较键是否相等,它和严格相等 === 差不多，区别是NaN被看成是等于NaN,所以NaN也可以作为键

```

### Map 的迭代

如果要在Map里使用循环，可以使用三个方法:

- map.keys() 遍历并返回所有的键值
- map.value() 遍历并返回所有的值
- map.entries()遍历并返回所有的实体 [key,value] ,for...of 在默认情况下使用的就是这个。

```javascript
let recipeMap = new Map([
  ['cucumber',500],['tomatoes',350],['onion',50]
])
//遍历多有的实体[key,value]

for(let entry of recipeMap){ //recipeMap.entries()相同
   console.log(entry); //["cucumber", 500] ["tomatoes", 350]["onion", 50]
}

```

#### 普通对象如何创建一个Map  使用Object.entries()

如果我们想要从一个已有的普通对象来创建一个Map,我们可以使用内建方法Object.entries(obj),该返回对象的键/值对数组。

从一个对象创建一个Map:

```javascript
let obj = {
  name:'zhang',
  age:30
}
let map = new Map(Object.entries(obj));

console.log(map.set('name')) //zhang

```

这里，Object.entries 返回键/值对数组：[ ["name","zhang"], ["age", 30] ]。这就是 Map 所需要的格式。

#### 从Map创建对象  使用Object.fromEntries()

Object.entries() 给定一个具有[key,value] 键值对的数组，它会根据给定的数组创建一个对象

 ```javascript
 let prices = Object.fromEntries([  //从Map得到一个普通对象
   ['banana',1],
   ['orange',2],
   ['meat',3],
 ])  

 // 现在 {banana: 1, orange: 2, meat: 3}

  console.log(prices.orange) //2
 ```

## Set  

Set 是一个特殊类型的集合  "值"的集合(没有键)，它的每一个值只能出现一个

方法如下:

- new Set(iterable) 创建一个set,如果提供了一个interable对象 (通常是数组) ，将会从数组里面复制值到set中。
- set.add(value) 添加一个值,返回set本身   重复调用一个值只会出现一次
- set.delete(value) 删除值如果 value 在这个方法调用的时候存在则返回 true ，否则返回 false。
- set.has(value) 如果value在set中,返回true,否则返回false
- set.clear() 清空set
- set.size 返回数组长度

#### Set迭代(iteration)

我们可以使用for..of 或者forEach 来遍历Set


```javascript
let set = new Set(["oranges","apples","bananas"])
for(let value of set) console.log(value)
set.forEach((value,set) =>{
  console.log(value)
  console.log(set)
})
```

> Map 中用于迭代的方法在 Set中也同样支持.
> 在Map和Set中迭代总是按照值插入的顺序进行的,所以我们不能说这些集合是无序的,但是我们不能对元素进行重新排序.也不能直接按其标号来获取元素.

 例子

##### 过滤数组中的唯一元素

定义一个数组arr
创建一个函数unique(arr),该函数返回一个由arr中所有元素所组成的数组

```javascript
function unique(arr){
  return Array.from(new Set(arr))  // return [...new Set(arr)]
}

let values = ["A","B","C","D","B"]

alert(unique(values))  //Hare,Krishna,:-O

```




# 对象包装器

# 217 存在重复元素(数组去重,比较长度)

给定一个重复数组,判断是否出现重复元素。

- 如果任意一值在数组中出现至少两次,函数返回true
- 如果数组中每个元素都不相同,则返回false
 
```typescript
//方法一
function containsDuplicata(){
   return nums.some((el,index) =>nums.indexOf(el) !== index)
}
//方法二

const containsDuplicata = nums => {
  let set = new Set(nums)
  return set.size !== nums.length 
}


//方法三

function containsDuplicata(nums:number[]):boolean {
    return [...new Set(nums)].length !== nums.length
}
```


