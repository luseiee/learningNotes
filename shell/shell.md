Package : ctex
Title         : Classic Shell Scripting Notes
Author        : Lu, Phil

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

## grep命令
`
-v 反向选取，输出选不满足条件的
`

## printf命令
- 用法与C语言非常接近

## tr命令

tr命令可以对来自标准输入的字符进行替换、压缩和删除

```
  -c或——complerment：取代所有不属于第一字符集的字符；
  -d或——delete：删除所有属于第一字符集的字符；
  -s或--squeeze-repeats：把连续重复的字符以单独一个字符表示；
  -t或--truncate-set1：先删除第一字符集较第二字符集多出的字符
  
  echo aa.,a 1 b#$bb 2 c*/cc 3 ddd 4 | tr -cd '0-9 \n' 
  1 2 3 4
  
  tr 'A-Z' 'a-z'
```

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
一般写在脚本里

## .profile .bashrc区别
.profile是每次登陆时运行  
.bashrc是每次运行bash时运行

# 查找与替换

## 正则表达式与BRE，ERE

BRE是基本正则表达式(Basic Regular Expression)  
ERE是扩展正则表达式子(Extended Regular Expression)  
BRE是grep的默认，而程序中一般使用ERE，如python神马的，+就属于ERE的meta符号  
grep -E 表示ERE  
grep 则表示BRE  

## 一些小笔记

- `.` 用来匹配任意一个字符
- `+` 是之前的字符一个或多个 **ERE**
- `*` 是之前的字符0个或多个
- `？` 是之前的字符有或没有 **ERE**
- `[abc]` abc中的一个
- `[a-f0-9]` 16进制字符
- `(abc)` 连续的abc,代表一个整体，后面可以以加入\*+之类的 **ERE**
- `{a,b}` 表示前面的字符出现a,b次，或者可以不写b精确a次，有逗号表示没有上限
- 一些字符集`[:alnum:], [:alpha:]`
- `[^]`匹配不在指定字符组内的任一字符

## sed命令
> sed用来处理文本里的每一行，可以查找，替换，删除，显示等等等等，其功能完全包含grep，tr等命令  

- 它的最为常用的功能就是s:  
```
  sed 's/要匹配的字符/要替换成的字符/g' file  
```
- 其中/代表分界符，可以用其他符号代替；g代表搜索全文件，不写则找到第一个就结束了  

举个例子: 
```
  find /home/tolstoy -type d -print |    -type d表示类型为directory
  sed 's;/home/tolstoy/;/home/lt/;' |
  sed 's/^/mkdir /' |                    插入mkdir指令
  sh -x                                  -x表示指令追踪
```

这里开始是我后面补上的笔记：

```
  sed
  -n 取消默认的输出
  -e 进行多项编辑，即进行多次sed命令
  sed -e '.....' -e '.....'
  -f 指定sed脚本的文件名，就是说sed命令可以写在一个脚本里的
  
  p命令，不加-n的话选中的行会输出两遍
  sed -n '3,5p' a.txt  # 打印第3～5行
  sed -n '3,4d' a.txt  # 删除第3～4行
  d命令
  sed '/My/,/You/d' a.txt #删除包含"My"的行到包含"You"的行之间的行
  sed '/My/,10d' a.txt #删除包含"My"的行到第十行的内容
  s命令
  sed -n '1,20s/My$/You/gp' datafile
  1～20行中，文末的My替换为You并输出
```

## cut命令

> cut 命令从文件的每一行剪切字节、字符和字段并将这些字节、字符和字段写至标准输出。  
如果不指定 File 参数，cut 命令将读取标准输入。必须指定 -b、-c 或 -f 标志之一。

```
  cut
  -b ：以字节为单位进行分割。这些字节位置将忽略多字节字符边界，除非也指定了 -n 标志。  
  -c ：以字符为单位进行分割。  
  -d ：自定义分隔符，默认为制表符。  
  -f ：与-d一起使用，指定显示哪个区域。   
  -n ：取消分割多字节字符。仅和 -b 标志一起使用。如果字符的最后一个字节落在由 -b 标志的 List 参数指示的<br />范围之内，该字符将被写出；否则，该字符将被排除。  
```

举2个例子：
```
  cut -d : -f 1,5 /etc/passwd     该命令以:分割，取每行的第1,5列
  ls -l | cut -c 1-10             该命令取第1~10个字符，正好是文件的读写执行权限
```

## join命令
> 将两个文件中，指定栏位内容相同的行连接起来。 

## awk命令
> awk是一种“单命令行程序”  
> 它的使用模式为:
```
  awk 'program' [ file ]
```
> 和sed命令很像  
> 其中program的基本格式为 pattern \{ action }

举个例子：
```
  awk -F : '{print $1, $5 }' /etc/passwd    以:作为分隔符，输出第一字段第五字段
```

# 文本处理工具

## sort命令
`
-r 反转
-n 以数值排序，比如10就要排在2的后面
-k 选择按第几个字段排序，当有多个-k的时候就优先左边再右边
-k 1.2,2.3 从第一个字段的第二个字符比较到第二个字段的第三个字符
-t 选择字段的分隔符，默认以空白分隔
-f 忽略大小写
-u 去重
`
举几个例子:
```
  sort -t: -k4n -k3n /etc/passwd 以:作为分隔符，先按照第四字段数值排序再按第三字段数值排序
```

## uniq命令
> sort中的-u选项虽然会删除重复，但是它知识按照键值进行排序而不是按照整行内容，因此我们需要uniq命令

`
uniq -c 在输出上加上计数
`

举个例子：
```
  sort a.txt | uniq
```

## fmt命令

常常用在管道中，用来重新格式化段落，嘴馋工的功能就是规定输出宽度

```
  cat a.txt | fmt -w 50
```

## wc命令

输出行数，字数，字节数

```
  cat a.txt | wc
  输出: 18 155 960
  -c 字节数
  -l 行数
  -w 字数
```

## head命令, tail命令

```
  head -n8 显示前八行
  tail -n9 显示后九行
  tail -f -n2 监视最后两行，这时tail命令永远不会结束
```

## file命令

file将参数文件内容的前几个字节与样式数据库进行比对，再输出一份简短报告
```
  file a.txt
  输出: a.txt: ASCII text
```

# 管道的神奇魔力

## umask命令

```
  umask 077  这条命令使得之后创建的文件只有当前用户有读写权限
```

> 默认情况下的umask值是022(可以用umask命令查看），此时你建立的文件默认权限是644(6-0,6-2,6-2)，
建立的目录的默认权限是755(7-0,7-2,7-2)，可以用ls -l验证一下哦　现在应该知道umask的用途了吧，
它是为了控制默认权限，不要使默认的文件和目录具有全权而设的

> 文件用6减，目录用7减

## chmod命令
```
  chmod 755 file  数字命名法
  chmod a+x file  文字设定法
```

```
<权限范围>+<权限设置> 使权限范围内的目录或者文件具有指定的权限
<权限范围>-<权限设置> 删除权限范围的目录或者文件的指定权限
<权限范围>=<权限设置> 设置权限范围内的目录或者文件的权限为指定的值

权限范围：
u ：目录或者文件的当前的用户
g ：目录或者文件的当前的群组
o ：除了目录或者文件的当前用户或群组之外的用户或者群组
a ：所有的用户及群组,默认

权限代号：
r ：读权限，用数字4表示
w ：写权限，用数字2表示
x ：执行权限，用数字1表示
- ：删除权限，用数字0表示
s ：特殊权限 
```
## 本章内容

本章讲了很多脚本的实例，可以把它写到脚本里，一般用法就是

```
script < infile > outfile
```

# 变量、判断、重复动作

## export, readonly, env, unset命令
```
  LXC=zhu    普通变量，注意不要加空格
  export LXC
  export LXC=zhu
  export -p
  export命令是把变量放到环境里，可供应所有执行中的程序使用，-p是显示所有环境变量
  unset LXC    unset命令会删除变量
  readonly LXC=zhu     创建只读变量
  readonly -p
  env LXC=dazhu command 这样会在command中使用新的LXC变量，但是shell中原来的LXC不变
```

## $:变量展开
```
  $LXC    最普通的
  ${LXC}   复杂脚本中最好这样写
  ${LXC:-word} 存在则返回LXC，否则返回word
  ${LXC:=word} 存在则返回LXC，否则返回word且把LXC赋值为word
  ....类似的还有不少
```

## `$1, $2, ... ${10}`位置参数

有一些特殊变量表示特殊的参数, `$`表示把它们显示出来：
`$#, $*, $@.......`

这些都是用在脚本里的

## shell脚本中的内置变量
```
  #     目前进程的参数个数
  @     传递给当前进程的命令行参数
  *     当前进程的命令行参数
  ?     前一命令的推出状态
  $     shell程序的进程编号
  0     shell程序的名称
  HOME  根目录
  PPID  父进程编号
```

## 算术运算

算数运算与C语言几乎一模一样，但是一定要放在`$((...))`
```
  $((2 + 3))
  $((3 && 4)) #1
```

## 退出状态

每条shell命令都有一个退出状态  
0表示进程成功，其他数字都是失败  
可以用`$?`来查看上一条命令的退出状态

## if-elif-else-fi
shell的if语句比较特殊它接受一个命令，如果执行成功则相当于if判断成功
```
  if grep pattern myfile > /dev/null
  then
    ...    grep成功
  else
    ...    grep失败
  fi
```
`! && ||`可以被用于脚本中  
有一点比较特殊，`a && b`, a失败了就不会执行b，`a || b`，a成功了不会执行b

## `$1, $2, ... ${10}`位置参数

有一些特殊变量表示特殊的参数, `$`表示把它们显示出来：
`$#, $*, $@.......`

这些都是用在脚本里的

## shell脚本中的内置变量
```
  #     目前进程的参数个数
  @     传递给当前进程的命令行参数
  *     当前进程的命令行参数
  ?     前一命令的推出状态
  $     shell程序的进程编号
  0     shell程序的名称
  HOME  根目录
  PPID  父进程编号
```

## 算术运算

算数运算与C语言几乎一模一样，但是一定要放在`$((...))`
```
  $((2 + 3))
  $((3 && 4)) #1
```

## 退出状态

每条shell命令都有一个退出状态  
0表示进程成功，其他数字都是失败  
可以用`$?`来查看上一条命令的退出状态

## if-elif-else-fi

shell的if语句比较特殊它接受一个命令，如果执行成功则相当于if判断成功
```
  if grep pattern myfile > /dev/null
  then
    ...    grep成功
  else
    ...    grep失败
  fi
```
`! && ||`可以被用于脚本中  
有一点比较特殊，`a && b`, a失败了就不会执行b，`a || b`，a成功了不会执行b

## test命令

```
  test [ expression ]
  [ [ expression ] ]
  这两种写法都是可以的
  
  test string   返回string是不是null
  test -b file  file是块设备文件
  test -d file  file是目录
  ...
  test s1 = s2  字符串s1与s2相同
  test n1 -lt n2  n1小于n2
  ...
```
用来返回真伪，可以用在脚本的if语句中
```
  一般脚本里会这样写
  if [ "X$1" = "X-f" ]    X防止字符串是空的
  then
    ...
```

## case语句
语法有点特殊，用到再查吧

后面有用到

## for循环
```
  第一种：
  for i in atl*.xml
  do
    echo $i
    mv $i $i.old
    sed '.....' < $i.old >$i
  done
  第二种
  for i     # 循环命令行参数
  do
    case $i in
    -f)   ...
          ;;
    ...
    esac
  done
```

## while和until循环
```
while(until) condition
do
  statements
done

while是condition成功返回就继续执行，until是反之
```
> shell也有break和continue

## shift命令
```
shift让所有参数顺移  
原来的$1没了, 原来的$2变成$1, ...
配合
while [ $# -gt 0 ]
do
  shift
done
可以对一个个参数进行处理！  
```

## getops命令

简化脚本的参数处理
```
  #!/bin/bash
  while getopts "a:bc" arg #选项后面的冒号表示该选项需要参数,即必选
  do
          case $arg in
              a)
                  echo "a's arg:$OPTARG" #参数存在$OPTARG中
                  ;;
              b)
                  echo "b"
                  ;;
              c)
                  echo "c"
                  ;;
              ?)  #当有不认识的选项的时候arg为?
              echo "unkonw argument"
          exit 1
          ;;
          esac
  done
```

## 函数
```
  wait_for_user () {
    until who | grep "$1" > /dev/null
    do
      sleep ${2:-30}
    done
  }

用法
  wait_for_user phil
  wait_for_user phil 60
```

- 在函数中，`$1, $2`变成了传递给函数的参数而不是脚本的参数，函数之行完毕就恢复
- 函数可以使用return来返回执行状态，不写的话就默认为 `return $?`
- 函数里并没有局部变量，和全局都是共享的 
