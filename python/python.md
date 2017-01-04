Title         : Python
Author        : Lu, Phil
Package       : xeCJK

[TITLE]

** http://www.liaoxuefeng.com/ **

# Day One: Basics
## 输入输出
```python
  name = input('please enter your name: ')
  print('hello,', name)
```

## 变量类型
```python
  n = 123               #整数
  f = 456.789         #浮点
  a = True and False or True #布尔
  b = None              #空
  s1 = 'Hello, world'   #字符串
  s3 = r'Hello, "Bart"'    #r为默认不转义
  s4 = r'''Hello,         
  Lisa!'''              #```内为自动加上换行符
```

## 编码
一般脚本前加上这两行
```python
  #!/usr/bin/env python3
  # -*- coding: utf-8 -*-
```

## list & tuple
```python
  classmates = ['Michael', 'Bob', 1.23, ['asp', 'php']]     #list数据类型
  len(classmates)      
  classmates[0]
  classmates[-1]
  classmates.append('Adam')     #加在末尾
  classmates.insert(1, 'Jack')    #加在指定位置
  classmates.pop(1)       #删除制定元素并返回，默认为最后一个
  
  t = (1, 2)      #tuple数据类型,一旦指定不能改变
  t = ('a', 'b', ['A', 'B'])    #指向一个list，就不能改成指向其他对象
  t[2][0] = 'X'    #但指向的这个list本身是可变的
```

## if
```python
  age = 20              #nothing special
  if age >= 6:
      print('teenager')
  elif age >= 18:
      print('adult')
  else:
      print('kid')
```

## 循环
```python
  names = ['Michael', 'Bob', 'Tracy']#第一种, for只有for...in...这种写法
  for name in names:
      print(name)
      
  while n > 0:#第二种
    sum = sum + n
    n = n - 2
```

## dict & set
```python
  d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}  #dict数据类型
  d['Michael'] = 80 #修改
  'Thomas' in d  #返回False
  d.get('Thomas')  #返回None
  d.pop('Bob')   #删除元素并返回
```
和list比较，dict有以下几个特点：

- 查找和插入的速度极快，不会随着key的增加而变慢；
- 需要占用大量的内存，内存浪费多
- 要保证hash的正确性，作为key的对象就不能变
- 在Python中，字符串、整数等都是不可变的，因此，可以放心地作为key。而list是可变的，就不能作为key

> 还有一种数据类型set，类似于数学中的集合，反正我没用过

## 函数
- 一些内置函数

```python
  abs(-20)
  int('123')
  str(1.23)
  a = abs # 变量a指向abs函数
  a(-1)
```

- 定义函数

```python
  import math

  def move(x, y, step, angle=0):
      nx = x + step * math.cos(angle)
      ny = y - step * math.sin(angle)
      return nx, ny       #实际上是返回了一个tuple
```
> 定义函数时，需要确定函数名和参数个数；  
> 如果有必要，可以先对参数的数据类型做检查；  
> 函数体内部可以用return随时返回函数结果；  
> 函数执行完毕也没有return语句时，自动return None。  
> 函数可以同时返回多个值，但其实就是一个tuple。  

- 函数参数

参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。
```python
  d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}  #dict数据类型
  d['Michael'] = 80 #修改
  'Thomas' in d  #返回False
  d.get('Thomas')  #返回None
  d.pop('Bob')   #删除元素并返回
```

```python
  def f2(a, b, c=0, *args, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
  f2(1, 2, d=99, ext=None)
  a = 1 b = 2 c = 0 d = 99 kw = {'ext': None}  #output
```

- *args是可变参数，args接收的是一个tuple；

- **kw是关键字参数，kw接收的是一个dict。