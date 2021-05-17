---
title: Day6:知识点记录
date: 2020-9-23
---
# Object.keys、Object.values、Object.entries

# 普通函数和Map 有什么区别

调用语法 和返回值的不同
1)
Map 调用语法 `map.keys()`  
Object 调用语法是 `Object.keys(obj)`，而不是obj.keys()
2)
Map的返回值是`可迭代项` 
Object 的返回值是`"真正的数组"`
Why?
其一：

> 因为灵活性,在javascript中,对象是所有复杂结构的基础。

```txt
  比如我们有一个自己创建的对象data,并可以实现它自己的data.values()方法,同时我们依然可以调用Object.values(data)方法
```
其二：

> Object.* 返回的是真正的数组对象，而不是迭代项,这主要是历史原因

```javascript
let user = {
  name:"join",
  age:30
};
console.log(Object.keys(user))  //["name","age"]
console.log(Object.values(user)) //["join",30]
console.log(Object.entries(user)) //[["name":"join"],["age":30]]
```

使用`Object.values`来遍历属性的值

```javascript
let user = {
  name:"join",
  age:30
};

for(let value of Object.values(user)){
  console.log(value) // join,then 30
}
 
```

>>  Object.keys/values/entries 会忽略 symbol 属性
>>  就像 for..in 循环一样，这些方法会忽略使用 Symbol(...) 作为键的属性。

   通常这很方便。但是，如果我们也想要 Symbol 类型的键，那么这儿有一个单独的方法 Object.getOwnPropertySymbols，它会返回一个只包含 Symbol 类型的键的数组。另外，还有一种方法 Reflect.ownKeys(obj)，它会返回 所有 键。

### 转换对象

因为对象缺少数组的方法比如map、filter。所以我们需要使用
Object.entries() ，然后再使用Object.fromEntries()

- 使用Object.entries(obj) ,从中获取obj的键/值对组成的数组。
- 对该数组适应数组的方法,比如map
- 对结果数组使用Object.fromEntries(array)方法,将结果转换为对象。

一个带有价格的对象,进行加倍

```javascript
let prices = {
  banana: 1,
  orange: 2,
  meat: 4,
};

let doublePrices = Object.fromEntries(
  // 转换为数组，之后使用 map 方法，然后通过 fromEntries 再转回到对象
  Object.entries(prices).map(([key, value]) => [key, value * 2])
);

console.log(doublePrices.meat); // 8
```

#### exercise

属性求和

有一个带有任意数量薪水的 salaries 对象。

编写函数 sumSalaries(salaries)，该函数使用 Object.values 和 for..of 循环返回所有薪水的总和。

如果 salaries 是空对象，那么结果必须是 0。


```javascript
 
 let salaries = {
     "John":100,
     "Pete":200,
     "Mary":300,
 }
//方案一
function sunSararies(salaries){
  let num = 0;
  for(let value of Object.values(salaries)){
    num += value
  }
  return num;  //600
}
//方案二
function sunSararies(salaries){
  return Object.values(salaries).reduce((sum,item) => sum+item,0)
}

sunSararies(salaries)

```

计算属性数量

计算一个函数count(obj),该函数返回对象中属性数量的数量:

```javascript
let user = {
  name:'zhang',
  age:30,
}

function count(user){
  return Object.keys(user).length
}

count(user)  //2

```

# 解构赋值

对象: 通过键来存储数据项的单个实体
数组：将数据收集到一个有序的集合中

# 350 两个数组的交集 II  (indexOf检查是否另一个数组存在，哈希表记录元素出现的个数、序列优化循环)

- indexOf 检查是否在另一个数组中存在
```txt
遍历其中一个数组nums1,在另一个数组nums2 中是否存在该元素
- 存在放入到结果中，并在nums2中删除
- 不存在则不做任何操作
```
```javascript
//方法一
const intersect = (nums1,nums2) => {
  let _result = [] //定义一个空数组
  for(let i = 0; i<nums1.length;i++>){
    let j =  nums2.indexOf(nums1[i])  //判断当前元素是否在nums2中出现 ,如果出现用j进行过存储索引
   //如果不出现为-1
   if(j >= 0 ){  //如果大于等于0证明出现了进行push
      _result.push(nums1[i]) 
      nums2.splice(j,1)  //删除nums2 中的数据 避免重复
   }
   return _result
  }
}
//方法二
function intersect(nums1:number[],nums2:number[]):number[]{
   return nums1.filter(el => {
     const index = nums2.indexOf(el)
     if(index > -1) nums2 = [...nums2.slice(0,index),...nums.slice(index + 1)]
     return index > -1;
   })
}
```

