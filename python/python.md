Title         : Python
Author        : Lu, Phil

[TITLE]

# Python基础

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

# 面向对象高级编程

## 给类和实例绑定方法

```python
  s = Student()  
  s.name = 'Michael' # 给实例绑定属性
  def set_age(self, age): # 定义一个函数作为实例方法
    self.age = age
  from types import MethodType
  s.set_age = MethodType(set_age, s) # 给实例绑定一个方法
  def set_score(self, score):
    self.score = score
  Student.set_score = set_score # 给对象绑定方法
```

## 使用__slots__

```python
  class Student(object):
      __slots__ = ('name', 'age') # 用tuple定义允许绑定的属性名称
```

## 使用@property

```python
    class Student(object):

    @property
    def score(self):
        return self._score

    @score.setter
    def score(self, value):
        if not isinstance(value, int):
            raise ValueError('score must be an integer!')
        if value < 0 or value > 100:
            raise ValueError('score must between 0 ~ 100!')
        self._score = value
    >>> s = Student()
    >>> s.score = 60 # OK，实际转化为s.set_score(60)
    >>> s.score # OK，实际转化为s.get_score()
    60
    >>> s.score = 9999
    error
```

## python允许多重继承

## 定制类

- 打印得漂亮一些
```python
    def __str__(self):
        return 'Student object (name: %s)' % self.name
    __repr__ = __str__ # 这是在直接输入s的时候输出的东西
>>> print(Student('Michael'))
Student object (name: Michael)
```

- 可以被for..in..调用
```python
  class Fib(object):
    def __init__(self):
        self.a, self.b = 0, 1 # 初始化两个计数器a，b

    def __iter__(self):
        return self # 实例本身就是迭代对象，故返回自己

    def __next__(self):
        self.a, self.b = self.b, self.a + self.b # 计算下一个值
        if self.a > 100000: # 退出循环的条件
            raise StopIteration();
        return self.a # 返回下一个值
  
```

- 可以被下标和切片访问

```python
  class Fib(object):
    def __getitem__(self, n):
        if isinstance(n, int): # n是索引
            a, b = 1, 1
            for x in range(n):
                a, b = b, a + b
            return a
        if isinstance(n, slice): # n是切片
            start = n.start
            stop = n.stop
            if start is None:
                start = 0
            a, b = 1, 1
            L = []
            for x in range(stop):
                if x >= start:
                    L.append(a)
                a, b = b, a + b
            return L
```

- 动态返回属性或者方法
```python
class Student(object):

    def __init__(self):
        self.name = 'Michael'

    def __getattr__(self, attr):
        if attr=='score':
            return 99
        # 一个非常有用的用法，就是不判断attr，然后操作attr返回一个东西
```

- __call__,直接调用实例
```python
class Student(object):
    def __init__(self, name):
        self.name = name

    def __call__(self):
        print('My name is %s.' % self.name)
调用方式如下：

>>> s = Student('Michael')
>>> s() # self参数不要传入
My name is Michael.
```

## 使用元类

- type()函数既可以返回一个对象的类型，又可以创建出新的类型，比如，我们可以通过type()函数创建出Hello类，而无需通过class Hello(object)...的定义

- 正常情况下，我们都用class Xxx...来定义类，但是，type()函数也允许我们动态创建出类来

```python
  >>> def fn(self, name='world'): # 先定义函数
...     print('Hello, %s.' % name)
...
>>> Hello = type('Hello', (object,), dict(hello=fn)) # 创建Hello class
>>> h = Hello()
>>> h.hello()
Hello, world.
>>> print(type(Hello))
<class 'type'>
>>> print(type(h))
<class '__main__.Hello'>
```

- 如果我们想创建出类呢？那就必须根据metaclass创建出类，所以：先定义metaclass，然后创建类。连接起来就是：先定义metaclass，就可以创建类，最后创建实例。

```python
# metaclass是类的模板，所以必须从`type`类型派生：
class ListMetaclass(type):
    def __new__(cls, name, bases, attrs):
        attrs['add'] = lambda self, value: self.append(value)
        return type.__new__(cls, name, bases, attrs)
```

# 进程和线程

## 多进程

- multiprocessing模块就是跨平台版本的多进程模块。

- 一种方法是os.fork(),一种方法如下

```python
from multiprocessing import Process
import os

# 子进程要执行的代码
def run_proc(name):
    print('Run child process %s (%s)...' % (name, os.getpid()))

if __name__=='__main__':
    print('Parent process %s.' % os.getpid())
    p = Process(target=run_proc, args=('test',))
    print('Child process will start.')
    p.start()
    p.join()
    print('Child process end.')
```

- 大量进程时用进程池
```python
from multiprocessing import Pool
import os, time, random

def long_time_task(name):
    print('Run task %s (%s)...' % (name, os.getpid()))
    start = time.time()
    time.sleep(random.random() * 3)
    end = time.time()
    print('Task %s runs %0.2f seconds.' % (name, (end - start)))

if __name__=='__main__':
    print('Parent process %s.' % os.getpid())
    p = Pool(4)
    for i in range(5):
        p.apply_async(long_time_task, args=(i,))
    print('Waiting for all subprocesses done...')
    p.close()
    p.join()
    print('All subprocesses done.')

- 如果子进程不是自身，而是一个外部进程，则需要`import subprocess`

- 进程间通信

- Process之间肯定是需要通信的，操作系统提供了很多机制来实现进程间的通信。Python的multiprocessing模块包装了底层的机制，提供了Queue、Pipes等多种方式来交换数据。我们以Queue为例，在父进程中创建两个子进程，一个往Queue里写数据，一个从Queue里读数据。


## 多线程
- 在Python中，可以使用多线程，但不要指望能有效利用多核。如果一定要通过多线程利用多核，那只能通过C扩展来实现，不过这样就失去了Python简单易用的特点。

- Python虽然不能利用多线程实现多核任务，但可以通过多进程实现多核任务。多个Python进程有各自独立的GIL锁，互不影响。

## ThreadLocal

- 一个ThreadLocal变量虽然是全局变量，但每个线程都只能读写自己线程的独立副本，互不干扰。ThreadLocal解决了参数在一个线程中各个函数之间互相传递的问题。

## 分布式

- Python的multiprocessing模块不但支持多进程，其中managers子模块还支持把多进程分布到多台机器上。一个服务进程可以作为调度者，将任务分布到其他多个进程中，依靠网络通信。由于managers模块封装很好，不必了解网络通信的细节，就可以很容易地编写分布式多进程程序。

- 举个例子：如果我们已经有一个通过Queue通信的多进程程序在同一台机器上运行，现在，由于处理任务的进程任务繁重，希望把发送任务的进程和处理任务的进程分布到两台机器上。怎么用分布式进程实现？

- 原有的Queue可以继续使用，但是，通过managers模块把Queue通过网络暴露出去，就可以让其他机器的进程访问Queue了。



# 错误处理

## 单元测试

- 为了编写单元测试，我们需要引入Python自带的unittest模块。

## 文档测试

- 就是将测试直接写在类的定义中，又可以当示例，又可以直接运行测试。

- doctest非常有用，不但可以用来测试，还可以直接作为示例代码。通过某些文档生成工具，就可以自动把包含doctest的注释提取出来。用户看文档的时候，同时也看到了doctest。

# 科学计算

## numpy

```python
# 多维数组切片
a = np.array([[11, 12, 13, 14, 15],
              [16, 17, 18, 19, 20],
              [21, 22, 23, 24, 25],
              [26, 27, 28 ,29, 30],
              [31, 32, 33, 34, 35]])
              
print(a[0, 1:4]) # >>>[12 13 14]
print(a[1:4, 0]) # >>>[16 21 26]
print(a[::2,::2]) # >>>[[11 13 15]
                  #     [21 23 25]
                  #     [31 33 35]]
print(a[:, 1]) # >>>[12 17 22 27 32]
# 数组属性
print(type(a)) # >>><class 'numpy.ndarray'>
print(a.dtype) # >>>int64
print(a.size) # >>>25
print(a.shape) # >>>(5, 5)
print(a.itemsize) # >>>8
print(a.ndim) # >>>2
print(a.nbytes) # >>>200
```

## scipy

- SciPy是一款方便、易于使用、专为科学和工程设计的Python工具包.它包括统计,优化,整合,线性代数模块,傅里叶变换,信号和图像处理,常微分方程求解器等等

```python
from scipy.optimize import leastsq
plsq = leastsq(residuals, p0, args=(y1, x))
```

## theano快速入门

### 常用的数据类型
```
数值：iscalar(int类型的变量)、fscalar(float类型的变量)
一维向量：ivector(int 类型的向量)、fvector(float类型的向量)、
二维矩阵：fmatrix(float类型矩阵)、imatrix（int类型的矩阵）
三维float类型矩阵：ftensor3  
四维float类型矩阵：ftensor4
```

### 定义函数，求偏导数

```python
# -*- coding: utf-8 -*-
import theano
import numpy as np
x = theano.tensor.fscalar('x')#声明一个int类型的变量x  
y = theano.tensor.pow(x,3)#定义y=x^3  
f = theano.function([x],y)#定义函数的自变量为x（输入），因变量为y（输出）  
print f(2)#计算当x=2的时候，函数f(x)的值
dx = theano.grad(y,x) # 偏导数函数
f2 = theano.function([x],dx) # 定义函数f，输入为x，输出为s函数的偏导数  
```

### 共享变量

- 在程序中，我们一般把神经网络的参数W、b等定义为共享变量，因为网络的参数，基本上是每个线程都需要访问的。

```python
  import theano  
  import numpy  
  A=numpy.random.randn(3,4);#随机生成一个矩阵  
  x = theano.shared(A)#从A，创建共享变量x  
  print x.get_value() #通过get_value()、set_value()可以查看、设置共享变量的数值。
  
  #coding=utf-8  
  import theano  
  w= theano.shared(1)#定义一个共享变量w，其初始值为1  
  x=theano.tensor.iscalar('x')  
  f=theano.function([x], w, updates=[[w, w+x]]) #定义函数自变量为x，因变量为w，当函数执行完毕后，更新参数w=w+x  
  print f(3)#函数输出为w  
  print w.get_value()#这个时候可以看到w=w+x为4 
```

# 分类算法

## 决策树

- [决策树](http://www.cnblogs.com/leoo2sk/archive/2010/09/19/decision-tree.html)

![1_3]

[1_3]: images/1_3.png "1_3" { width:auto; max-width:90% }

- 决策树（decision tree）是一个树结构（可以是二叉树或非二叉树）。其每个非叶节点表示一个特征属性上的测试，每个分支代表这个特征属性在某个值域上的输出，而每个叶节点存放一个类别。使用决策树进行决策的过程就是从根节点开始，测试待分类项中相应的特征属性，并按照其值选择输出分支，直到到达叶子节点，将叶子节点存放的类别作为决策结果。

- 当构建决策树的时候，上层节点要有最大的信息增益，如果叶子结点不纯净，则选出现次数多的那个

## 随机森林

- [随机森林](http://blog.csdn.net/holybin/article/details/25653597)

- 随机森林由许多的决策树组成，因为这些决策树的形成采用了随机的方法，所以叫做随机森林。

- 当测试数据进入随机森林时，其实就是让每一颗决策树进行分类看看这个样本应该属于哪一类，最后取所有决策树中分类结果最多的那类为最终的结果（每棵树的权重要考虑进来）。所有的树训练都是使用同样的参数，但是训练集是不同的，分类器的错误估计采用的是oob（out of bag）的办法。

- 随机森林可以既可以处理属性为离散值的量，如ID3算法，也可以处理属性为连续值的量，比如C4.5算法。

## kNN

- k-近邻(kNN，k-Nearest Neighbors)算法是一种基于实例的分类方法。该方法就是找出与未知样本x距离最近的k个训练样本，看这k个样本中多数属于哪一类，就把x归为那一类。k-近邻方法是一种懒惰学习方法，它存放样本，直到需要分类时才进行分类，如果样本集比较复杂，可能会导致很大的计算开销，因此无法应用到实时性很强的场合

## 朴素贝叶斯

- 就好比这么个道理，你在街上看到一个黑人，我问你你猜这哥们哪里来的，你十有八九猜非洲。为什么呢？因为黑人中非洲人的比率最高，当然人家也可能是美洲人或亚洲人，但在没有其它可用信息下，我们会选择条件概率最大的类别，这就是朴素贝叶斯的思想基础。

-       第一阶段——准备工作阶段，这个阶段的任务是为朴素贝叶斯分类做必要的准备，主要工作是根据具体情况确定特征属性，并对每个特征属性进行适当划分，然后由人工对一部分待分类项进行分类，形成训练样本集合。这一阶段的输入是所有待分类数据，输出是特征属性和训练样本。这一阶段是整个朴素贝叶斯分类中唯一需要人工完成的阶段，其质量对整个过程将有重要影响，分类器的质量很大程度上由特征属性、特征属性划分及训练样本质量决定。

- 第二阶段——分类器训练阶段，这个阶段的任务就是生成分类器，主要工作是计算每个类别在训练样本中的出现频率及每个特征属性划分对每个类别的条件概率估计，并将结果记录。其输入是特征属性和训练样本，输出是分类器。这一阶段是机械性阶段，根据前面讨论的公式可以由程序自动计算完成。

- 第三阶段——应用阶段。这个阶段的任务是使用分类器对待分类项进行分类，其输入是分类器和待分类项，输出是待分类项与类别的映射关系。这一阶段也是机械性阶段，由程序完成。

## linear regression

- 最优解，突优化
- 做拟合，x对y
- 找到那条线

## k-means

- unsupervised learning
- EM:k-means是特例
- EML

## 高斯混合模型

- 一堆数据，两个高斯组成了现在的数据。然后去分离出来这两个峰

## Bias Varience Tradeoff

- 模型简单，varaince低，不容易overfit，bias
- 复杂模型，bias低，variance高

## SVM

- 分类，与逻辑回归区别是，它即使分类对了，还要使得分类的margin最平均。

- 点到超平面的距离分布要好

## Kernel SVM
- 线性不可分
- 大量数据也没啥用

## boosting

- 弱分类器合成强分类器，每个可以做到80%，可以合起来分90%
- training data，弱分类器

## 神经网络

## 总结

- 如果是小训练集，高偏差/低方差的分类器（例如，朴素贝叶斯NB）要比低偏差/高方差大分类的优势大（例如，KNN），因为后者会发生过拟合（overfiting）

- 复杂模型需要大量训练数据，不然容易过拟合。在一些特征明确，或者概率明确的时候，可以使用简单的模型，如朴素贝叶斯，逻辑回归。kNN在样本数据数量不一样的情况下效果不好。

- 决策树容易发生过拟合

- 线性回归不能解决非线性问题，SVM也不行，但是kernelSVM则可以。

- 朴素贝叶斯需要决定一些先验概率（这些先验概率往往是不知道的）

# 深度学习内容

## 主动学习

- 在某些情况下，没有类标签的数据相当丰富而有类标签的数据相当稀少，并且人工对数据进行标记的成本又相当高昂。在这种情况下，我们可以让学习算法主动地提出要对哪些数据进行标注，之后我们要将这些数据送到砖家那里让他们进行标注，再将这些数据加入到训练样本集中对算法进行训练。这一过程叫做主动学习。

## 半监督学习

- 部分有标签，用无标签数据加强有标签学习

## 增强学习

- 类似alphago

## loss function的选择

- 当我们用sigmoid函数作为神经元的激活函数时，最好使用交叉熵代价函数来替代方差代价函数，以避免训练过程太慢。因为sigmoid会产生一个求导后代入激活值的项，这一项会比较小。然后交叉熵代价函数就不会有这个缺点。

- 收敛速度与激活函数，代价函数都有很大的关系。

- 通过添加一个权重衰减项来修改代价函数，使得代价函数是凸函数

## validation data

- Validation set: a set of examples used to tune the parameters of a classifier In the MLP case, we would use the validation set to find the “optimal” number of hidden units or determine a stopping point for the back-propagation algorithm

## SGD算法的比较

### GD是最naive的

### SGD

### Momentum

就是当前下降的方向要与之前下降的方向加权平均。这里的\gamma一般取0.9就行了。直观上可以减少震荡，能更快的收敛

![quicklatex.com-b0cd988df959c1d76670dccf1a8a2a35_l3]

[quicklatex.com-b0cd988df959c1d76670dccf1a8a2a35_l3]: images/quicklatex.com-b0cd988df959c1d76670dccf1a8a2a35_l3.svg "quicklatex.com-b0cd988df959c1d76670dccf1a8a2a35_l3" { width:auto; max-width:90% }

### NAG

NAG(Nesterov accelerated gradient)核心思想就是利用Momentum预测下一步的梯度，而不是使用当前的\Vtheta。

### Adagrad

通过算法让学习速率的选择更加容易

其学习率是单调递减的，训练后期学习率非常小

其需要手工设置一个全局的初始学习率

### rmsprop，adadelta

是基于adagrad的，两者差不多

### Adam

神器，首先Adam利用了AdaGrad和RMSProp在稀疏数据上的优点。对初始化的偏差的修正也让Adam表现的更好。

### 总结

虽然针对不同的任务，应该尝试不同的优化算法。我觉得实在不知道用什么就试试Adam。但是在训练过程中自己调整一下学习速率对于复杂优化目标是必要的（个人观点），比如一个epoch乘以0.5啥的。这就得靠经验了。别以为最普通的SGD不行，还是会被很多人使用，因为谁都不知道训练复杂模型的过程中会发生什么，而SGD是最能保证收敛的

