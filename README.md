Package : ctex
Title         : Classic Shell Scripting Notes
Author        : Lu, Phil
Logo          : True

[TITLE]

# 背景知识
- POSIX
> POSIX，Portable Operating System Interface。  
是UNIX系统的一个设计标准，很多类UNIX系统也在支持兼容这个标准，如Linux。  
遵循这个标准的好处是软件可以跨平台。所以windows也支持就很容易理解了，那么多优秀的开源软件，支持了这个这些软件就可能有windows版本，就可以完善丰富windows下的软件。

# 入门
## #! 
``` 
  cat > nursers
  #! /bin/bash -
  
  who | wc -l
```
  
之后每条命令都会用bash运行
所以，如果是py文件可以在第一行加上#! /bin/python, 这样就可以使用./来运行它
## printf
- printf 命令
用法与C语言非常接近
dafshf

## 重定向与管道
### <\ 改变标准输入
> tr命令  
translate charactors  
```
  tr -d '0-9'
```
可以将标准输入中的数字全都删除
```
  tr -d '0-9' < mytext.txt
```
这就改变了标准输入而是将txt文件中的内容进行修改

### \>\ 改变标准输出
### \>\>\ 输出到文件时不覆盖文件而是附加
### |\ 建立管道
```
  program1 | program2
```
将program1的标准输出修改为program2的标准输入
```
  tr -d '\r' < mytext.txt | sort > mytext2.txt
```
过程:

1. tr的标准输入改成mytext.txt  
2. tr的标准输出变为sort的标准输入  
3. sort的标准输出重定向到mytext2.txt  

### /dev/null和/dev/tty
/dev/null是一个垃圾桶，所有输出到这里的数据都会被扔掉  
```
    echo 12321 > /dev/null
```
/dev/tty将重定向一个终端，键盘输入maybe，所以这个是用来作为输入的
```
  read password < /dev/tty
```
将会强制从/dev/tty中读取数据，一般情况下不写问题也不大貌似
> stty -echo  
可以将输入不显示在屏幕上  
stty echo  
重新显示  

## Shell脚本的参数
\$1代表第一个参数
\$2代表第二个参数
```
  cat > finduser
  #! /bin/sh
  
  who | grep $1
  ^D
```
使用的时候就可以./finduser lxc

## 简单的执行跟踪
set -x可以设置是否跟踪命令，跟踪命令是指每条命令执行时候在前面价一个 + 并显示出来

## .profile .bashrc区别
.profile是每次登陆时运行  
.bashrc是每次运行bash时运行

# 查找与替换

## 正则
