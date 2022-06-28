---
title: Day12:知识点记录
date: 2020-9-29
categories:
- web前端
tags:
- javascript
---

# JSON方法

 JSON.stringify()可以应用于原始数据(primitive)类型

JSON支持以下数据类型

- Objects()
- Arrays()
- strings
- numbers
- boolean
- null

```txt
 JSON是语言无关的纯数据规范,因此一些特定于JavaScript的对象属性会被JSON.stringify跳过。
 - 函数属性(方法)
 - Symbol类型的属性
 - 存储undefined的属性。
```

> JSON.stringify() 不得有循环引用


包装对象？
将对象转换为JSON再转换回

```javascript
let user = {
  name: "John Smith",
  age: 35
};

let sJion = JSON.parse(JSON.stringify(user))
console.log(sJion)

```

示例:排除反向引用

```javascript
let room = {
  number:23
};
let meetup = {
  title:"conference",
  occupiedBy:[{name:"John"},{name:"John"}],
  place:room
};

//循环引用
room.occupiedBy = meetup,
meetuo.self = meetup

let o = JSON.stringify(meetup,function replacer(key,value){
 
return (key != 0 && value == meetup)

})

```

- 算法
```javascript
// 123 456 789
  var rotate = function(maxrix){
    for(let i = 0;i<maxrix.length;i++){
      for(let j =i;j<maxrix.length;j++){
        let temp = maxrix[i][j]     
        maxrix[i][j] = maxrix[j][i]  
        maxrix[j][i] = temp
      }

      //交换得到  147 258 693
    }
    //每个数组倒序排列  // 741 852 963
    return maxrix.map(item => item.reverse())

  }


第一个参数  第二个参顺
回忽略值
三个参数值   
```