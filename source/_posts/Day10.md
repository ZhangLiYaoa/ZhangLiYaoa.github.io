---
title: Day10:知识点记录
date: 2020-9-27
categories:
- web前端
tags:
- Javascript
---
# 1. 清除定时器

就这？不是哟，我其实表达的是批量清除定时器，一般我们会在定时器调用的时候将它赋值给一个变量，然后将在需要清除定时器的时候使用 clearTimeout 或者 clearInterval 就可以清除定时器了。那么如果你想批量清除定时器又该如何清除呢？
其实很简单，小伙伴们在控制台打印一下使用 setTimeout 或者 setInterval 的返回值可能就知道改怎么做了。啥？你没 get 到，好吧，让我细细道来。
每个定时器调用的时候都会返回一个数字值 id，这个 id 值是递增的，每次你调用定时器后，id 值都会加一，如果后面你想清除全局的定制器，你可以再设一个定制器，用它的返回值来个 for 循环即可，代码如下：

```javascript
function clearAllTimer() {
  let timer = setInterval(() => {});
  for (let i = 1; i <= timer; i++) {
    clearInterval(i);
    clearTimeout(i);
  }
}
```

```txt
如果你只想清除特定范围或者特定的几个定时器的话，
可以将它们的值传到一个数组里面去，再进行一个 for 循环即可
```

```txt
注：谷歌浏览器的定时器返回数值ID以1为起，
fireFox要在原定时器的序位的基础上加1，我试了一下，起始值确实是2。
```

# 2.获取当前月份的最后一天

乍一看，好像挺简单的。但是一般的小伙伴都是一看就会，一用就废，认真想一下感觉好像实现起来有点难，其实就一行代码，挺简单的。

```javaascript
function getFirstDay(year, month) {
  return new Date(year, month, 0).getDate()
}

```

# 3.获取变量的数据类型

如何获取变量的数据类型？很常见的问题了，很多同学都会遇到，有挺多靠谱和不靠谱的回答，在这里我找了一种比较靠谱的回答，源码看下面：

```javascript
function getType(val) {
  return Object.prototype.toString.call(val).replace(/^\[object (.+)\]$/, "$1");
}
```

# 4. calc 的使用

calc 是一个 css3 新增的功能，可以用来指定元素的长度，动态计算长度值。写个小案例如下。以下只是小试牛刀，后面你需要自行百度 calc 的具体使用。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
       
    <meta charset="UTF-8" />
      
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      
    <title>Document</title>
      
    <style> 
       .parent {  
          width: 200px; 
          height: 200px;  
          background-color: lightblue;   
       }  
        .son {     
            width: calc(100% - 20px);     
            height: calc(100% - 20px);     
            background-color: lightpink;  
          }  
    </style>
  </head>
  <body> 
    <div class="parent">    
      <div class="son"> </div> 
    </div>
  </body>
</html>
```
```txt
注：calc在使用的时候需要注意它的运算符，
- 和 + 在使用的时候前后都必须要有空格，* 和 / 倒是没有这个要求
```
