---
title: Day11:知识点记录
date: 2020-9-28
categories:
- web前端
tags:
- javascript
---



格式化日期
```javascript
function formatDate(date: Date, pattern: string): string {
    const data = new Date();
    let month:number|string = data.getMonth()+1;
    let day:number|string = data.getDay();
    return `${data.getFullYear()}-${month}-${day} ${data.getHours()}:${data.getMinutes()}:${data.getSeconds()}`
}
```

```javascript
function formatDate(date: Date, pattern: string = "yyyy年MM月dd日"): string {
  
  let nDate = new Date()
  if(typeof date === 'string' || typeof date === 'number'){
     nData = new Date(+date)
  }else{
      nDate = date
  }
  const o = {
    'M+': nDate.getMonth() + 1,
    'd+': nDate.getDate(),
    'h+': nDate.getHours(),
    'm+': nDate.getMinutes(),
    's+': nDate.getSeconds(),
  }

  if (/(y+)/.test(pattern)) {
    pattern = pattern.replace(
      RegExp.$1,
      (nDate.getFullYear() + '').substr(4 - RegExp.$1.length)
    )
  }
 for(const k in o){
   if(new RegExp(`(${k}`).test(pattern)){
     cosnt str =  o[k] +''
     frm = frm.replace(
        RegExp.$1,
         RegExp.$1.length === 1 ? str: (('00'+str).substr(str.length))
     )
   }
 }
  return pattern
}
console.log(formatDate(1601364446000,"yyyy年MM月dd日"))
```