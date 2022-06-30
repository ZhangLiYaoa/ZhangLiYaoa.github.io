<!--
 * @Author: zhangliyao 15822532109@163.com
 * @Date: 2022-06-30 16:03:00
 * @LastEditors: zhangliyao 15822532109@163.com
 * @LastEditTime: 2022-06-30 16:58:51
-->
---
title: linux学习
date: 2022-6-30
categories:
- liunx
tags:
- 
---

# linux 


## 目录操作

`[mkdir]` 创建目录
`[cp]` 拷贝文件
`[mv]`移动文件
`[rm]`删除文件

1.基本操作

`
# 创建目录和父目录a、b、c、d

mkdir -p a/b/a/d

# 拷贝文件夹a 到/tmp目录
cp -rvf a//tmp

# 移动文件a到 /tmp目录，并重命名未b

mv -vf a /tmp/b

# 删除机器上的所有文件

rm -rvf /

`
2.漫游

`
ls 命令能够看到当前目录的所有内容。 ls -l 能够看到 更多信息，判断你是谁

pwd 命令能够看到终端所在的目录。告诉你在哪

cd 假如你去错了地方有，cd 命令能够切换到对的目录

find find命令通过筛选一些条件，能够找到已经被遗忘的文件

`

## 文本处理

3、查看文件

`[cat]` 

如果文件很大，cat命令会疯狂在终端上输出，可以多次按`ctrl + c`终止


`
# 查看文件大小

du -h file

# 查看文件内容

cat flie

`

[less]

针对比较大的文件，可以使用less命令打开某个文件，类似 vim 、less可以在输入/ 后进入查找模式，然后按n （N）向下(上)查找

[tail]

查看nginx的滚动日志

`tail -f access.log`

tail 命令可以静态的查看某个文件的最后n行，与之对应的head 命令查看文件头n行。head没有滚动功能。

`
tail -n100 access.log
head -n100 access.log
`




