# 1、初识Python





# 2、Python语言基础



## 2.1、Python语法特点

### 2.1.3、编码规范

1. 使用小括号隐式连接字符串

   代码1：小括号隐式连接字符串

   ```python
   #以下是隐式链接写法
   string=("我是"
       "菜鸡"
       "啊")
   print(string)
   ```

   输出1：

   ```txt
   我是菜鸡啊
   ```

   总结1：

   - 小括号中可以不用加连接符”+”就能够实现连接，但写代码的时候尽量不要这么做。

### 2.2.3、定义变量

1. 什么是可变数据类型，什么是不可变数据类型？

   以下所有的内容都是基于内存地址来说的。

   不可变数据类型： 当该数据类型的对应变量的值发生了改变，那么它对应的内存地址也会发生改变，对于这种数据类型，就称不可变数据类型。

   可变数据类型  ：当该数据类型的对应变量的值发生了改变，那么它对应的内存地址不发生改变，对于这种数据类型，就称可变数据类型。

   总结：不可变数据类型更改后地址发生改变，可变数据类型更改地址不发生改变



# 3、运算符与表达式

## 3.1、运算符

### 3.1.5、位运算符

1. 为什么Java和Python中-1取反是0？

   答：因为一个整数是以二进制补码的形式存储在计算机中，假设计算机是4位，那么-1的补码是1111，由于Java和Python的位运算是有符号位参与的，所以1111包括符号位取反的结果是0000，对应的真值就是0。

## 3.2、运算符的优先级

## 3.3、条件表达式



# 4、流程控制语句

## 4.2、选择语句

### 4.2.3、if...elif...else语句

1. Python中的判断语句可以写成连续不等式

   代码1：判断可以写成“18 < your_age <= 30”

   ```python
   your_age=int(input("请输入您的年龄："))
   if your_age <= 18:
       print("您的年龄还小，要努力学习哦！")
   elif 18 < your_age <= 30:
       print("您现在的阶段正是努力奋斗的黄金阶段！")
   elif 30 < your_age <=50:
       print("您现在的阶段正是人生的黄金阶段！")
   else:
       print("最美不过夕阳红！")
   ```

   输出1：

   ```txt
   请输入您的年龄：22
   您现在的阶段正是努力奋斗的黄金阶段！
   ```

   总结1：

   - Python和Java以及C不同，它可以写成连续不等式的形式也不会报错。

## 4.3、循环语句

1. Python迭代器使用

   - 可迭代对象：

     Python中有一类工具叫做迭代工具，他们能从左至右扫描对象。迭代工具包括了for循环、列表解析、in成员关系测试以及map内置函数等。而可迭代对象，顾名思义就是可以用在上述迭代工具环境中，通过一次次迭代不断产生结果的对象。

     可迭代对象分为两大类，一种是实际保存的序列，即列表、元组，字符串；另一种就是“不一次性产生所有结果列表，而是可以在for循环中按需一次产生一个结果的对象”。如：range函数返回值、zip函数返回值、enumerate函数返回值等等，与实际序列相对应，这个叫做按需产生对象的虚拟序列。

   - 迭代器：

     迭代器与可迭代对象的关系：可迭代对象支持内置函数iter，通过对可迭代对象调用iter函数，会返回一个迭代器，而“迭代器”支持内置函数next，通过不断对其调用next方法，会依次前进到序列中的下一个元素并将其返回，最后到达一系列结果的末尾时，会引发StopIteration异常。补充说明一点，对迭代器调用iter方法，则会返回迭代器自身。

     代码1：
     
     ```python
     L = [2,3,4]
     I = iter(L)
     print(iter(L))
     print(I is L)
   print(I is iter(I))
     ```

     输出1：
     
     ```txt
     <list_iterator object at 0x0000020D95C53640>
     False
   True
     ```

     总结1：

     - 从以上例子可看出，通过iter函数将迭代对象转化成迭代器，而对迭代器调用iter函数，依然返回迭代器。

     ***

     迭代演示过程：当任何可迭代对象传入到for循环或其他迭代工具中进行遍历时，迭代工具都是先通过iter函数获得与可迭代对象对应的迭代器，然后再对迭代器调用next函数，不断的依次获取元素，并在捕捉到StopIteration异常时确定完成迭代，这就是完整的迭代过程。这也称之为“迭代协议”。

     代码1：手动演示迭代协议
     
     ```python
     # 定义一个列表
     L = [2,3,4]
     # 通过iter()方法获取L的迭代器
     I = iter(L)
     # 通过next()方法依次取值
     print(next(I))
     print(next(I))
     print(next(I))
   print(next(I))
     ```

     输出1：
     
     ```txt
     2
     3
     4
     Traceback (most recent call last):
      File "E:/12homework/12homework.py", line 6, in <module>
     print(next(I))
   StopIteration
     ```

     总结1：

     - 在这个手动模拟迭代的过程中，先把可迭代对象转换成迭代器，然后用next方法进行手动迭代，迭代到最后出现StopIteration异常退出。

     代码2：实际的自动迭代过程
     
     ```python
     L = [2,3,4]
     for x in L:
       print(x)
     ```

     输出2：
     
     ```txt
     2
     3
   4
     ```

     总结2：

     - XXX

     ---

     典型对象迭代举例：

     迭代文件对象：

     代码1：open函数返回的已打开的文件对象，也是可以一行一行的读取，直至文件结束，那很显然，他也是可迭代对象（也就是下面代码的文件对象f）。
     
     ```python
     f = open(r'D:\VisualStudio_source\Python 从入门到精通\test\myfile.txt')
     // 输出f是否为迭代器
   print(f is iter(f))
     ```

     输出1：
     
     ```txt
   True
     ```

     总结1：

     - 从这个例子中我们可以看出，文件对象的迭代器就是他自己。即文件对象既是迭代器，又是可迭代对象。

     代码2：手动模拟文件对象迭代
     
     ```python
     f = open(r'D:\VisualStudio_source\Python 从入门到精通\test\myfile.txt')
     print(next(f))
     print(next(f))
     print(next(f))
   print(next(f))
     ```

     输出2：
     
     ```txt
     hello text file
     goodbyt text file
     hahahahah
     Traceback (most recent call last):
      File "E:/12homework/12homework.py", line 5, in <module>
     print(next(f))
   StopIteration
     ```

     总结2：

     - XXX

     代码3：上面代码2也可以用for循环来迭代
     
     ```python
     f = open(r'D:\VisualStudio_source\Python 从入门到精通\test\myfile.txt')
     # end=''使得最后的输出不会有一个空行
     for line in f:
       print(line, end='')
     ```

     输出3：
     
     ```txt
     hello text file
     goodbyt text file
   hahahahah
     ```

     总结3：

     - 这是读取文件的最佳方式，首先是简单、运行速度快，并且从内存使用情况而言也是最好的。

     代码4：用较为原始的readlines方法与代码3相比较
     
     ```python
     f = open(r'D:\VisualStudio_source\Python 从入门到精通\test\myfile.txt')
     # 使用readlines()方法
     for line in f.readlines():
       print(line, end='')
     ```

     输出4：
     
     ```txt
     hello text file
     goodbyt text file
   hahahahah
     ```

     总结4：

     - 对比来看，虽然readlines方法在功能上可用，但从内存上来看，非常糟糕，他是一次性把整个文件加载到内存，如果文件太大，以至于计算机内存不够，甚至不能够工作。而我们的迭代器版本则不然，迭代器是按需，一次只读取一行，因此对内存爆炸问题有了很好的免疫。

     迭代字典对象：文件和列表对象都是实际的序列，他所迭代的就是他的实际内容，那字典呢？字典也是一种可迭代对象，但是他的迭代器却比较特殊。

     代码1：手动模拟字典迭代过程
     
     ```python
     D = {'a':1, 'b':2, 'c':3}
     # 获取字典D的迭代器
     I = iter(D)
     # 利用迭代器依次取值
     print(next(I))
     print(next(I))
     print(next(I))
   print(next(I))
     ```

     输出1：
     
     ```txt
     a
     b
     c
     Traceback (most recent call last):
      File "E:/12homework/12homework.py", line 6, in <module>
     print(next(I))
   StopIteration
     ```

     总结1：

     - XXX

     代码2：for循环中自动迭代的例子
     
     ```python
     D = {'a':1, 'b':2, 'c':3}
     for k in D:
       print(k)
     ```

     输出2：
     
     ```txt
     a
     b
   C
     ```

     总结2：

     - 因此不难看出，字典也是一个可迭代对象，字典有一个迭代器，在迭代环境中，会每次自动地返回一个键。执行到最后会检测是否出现了StopIteration的异常，如果存在就结束for循环。

     代码3：需要补充的是，字典拥有不同视图的可迭代对象，这里就不详细一一展开了，看看几个例子，分别是各自不同视图下的可迭代对象和迭代器，他们也是一次产生一个结果项，而不是在内存中一次产生全部结果列表。
     
     ```python
     D = {'a':1,'b':2,'c':3}
     print(D.keys())
     print(iter(D.keys()))
     print(D.values())
     print(iter(D.values()))
     print(D.items())
   print(iter(D.items()))
     ```

     输出3：
     
     ```txt
     dict_keys(['a', 'b', 'c'])
     <dict_keyiterator object at 0x000001BA51A22130>
     dict_values([1, 2, 3])
     <dict_valueiterator object at 0x000001BA51A22130>
     dict_items([('a', 1), ('b', 2), ('c', 3)])
   <dict_itemiterator object at 0x000001BA51A22130>
     ```

     总结3：

     - XXX

     迭代range函数返回对象：

     代码1：range函数的返回值是一个可迭代对象，同理利用iter方法也可以得到他的迭代器
     
     ```python
     R = range(5)
     I = iter(R)
     print(R)
   print(I)
     ```

     输出1：
     
     ```txt
     range(0, 5)
   <range_iterator object at 0x000001F70B03F2D0>
     ```

     总结1：

     - Range方法返回的是一个迭代对象，但不是一个迭代器。

     迭代enumerate函数返回对象：

     代码1：enumerate方法返回的对象既是可迭代对象，又是迭代器
     
     ```python
     E = enumerate('spam')
     print(E)
   print(iter(E))
     ```

     输出1：
     
     ```txt
     <enumerate object at 0x000001AFF056BCC0>
   <enumerate object at 0x000001AFF056BCC0>
     ```

     总结1：
     
     - 可迭代对象按照需求，一次只返回一个结果，而不是一口气一次性的返回一个对象列表，因此我们必须把可迭代对象包裹在一个list调用中，从而才能一次性看到它们所有的值。

2. 迭代背后的原理

   序列可以迭代的原因：iter 函数。解释器需要迭代对象 x 时，会自动调用 iter(x)。内置的 iter 函数有以下作用：

   - 检查对象是否实现了 iter 方法，如果实现了就调用它，获取一个迭代器。
   - 如果没有实现 iter 方法，但是实现了 getitem 方法，而且其参数是从零开始的索引，Python 会创建一个迭代器，尝试按顺序（从索引 0 开始）获取元素。
   - 如果前面两步都失败，Python 抛出 TypeError 异常，通常会提示“C objectis not iterable”（C 对象不可迭代），其中 C 是目标对象所属的类。

   由此我们可以明确知道什么是 可迭代的对象： 使用 iter 内置函数可以获取迭代器的对象。即要么对象实现了能返回迭代器的 iter 方法，要么对象实现了 getitem 方法，而且其参数是从零开始的索引。

# 5、列表与元组

## 5.2、列表

### 5.2.2、访问列表元素

1. 类方法、实例方法和静态方法的区别

   实例方法，必须要创建实例才能调用，里面有self关键字，有初始化函数必须对初始化函数进行传参。

   类方法，可以直接类名.方法名直接调用，也可以创建实例调用。里面有cls关键字，调用时，直接类名.方法名，可以绕过实例方法的初始化函数，类方法不能访问实例属性。

   静态方法，可以直接类名.方法名直接调用，也可以创建实例调用。没有关键字，就像调用函数一样方便，调用时，直接类名.方法名，可以绕过实例方法的初始化函数，静态方法不能访问实例属性。

   代码1：关于实例方法、类方法和静态方法的例子

   ```python
   import requests
   
   class HttpRequest():
   
       def __init__(self,url,data):
           self.url = url
           self.data = data
   
       # todo 实例方法
       def send_post(self,url,data):   # todo 实例方法，只能通过实例来调用
           res = requests.post(url,data)
           print(res.status_code)
   
       @classmethod
       def add(cls,x,y):
           print('我是类方法')
           return x+y
   
       @staticmethod
       def print_msg():
           print('我是静态方法')
   ```

2. datetime.datetime.now().weekday()的解释

   首先第一个datetime实际上是指的datetime模块，第二个datetime是指datetime模块中的datetime类，而now()方法是datetime类中的类方法，而weekday()是datetime类中的实例方法，因为now()方法可以返回一个datetime对象，所以now()方法可以直接调用datetime类的实例方法weekday()，从而获取当前日期是星期几。

### 5.2.3、遍历列表

1. 关于内置函数enumerate()的说明

   enumerate(iterable, start=0)方法会返回一个enumerate对象。 iterable必须是序列，迭代器或其他支持迭代的对象。 由enumerate（）返回的迭代器的（下划下划next下划下划()）方法返回一个元组，该元组包含一个计数（从起始处开始，默认为0）以及通过对iterable进行迭代而获得的值，即索引和值。

   代码1：enumerate()的作用等同于以下代码

   ```python
   def enumerate(sequence, start=0):
       n = start
       for elem in sequence:
           yield n, elem
           n += 1
   ```

   说明1：关于yield关键字的说明，参见接下来的问题2。

2. 关于yield关键字说明

   首先我们得了解一个东西叫迭代器，通常的for…in…循环中，in后面是一个数组，这个数组就是一个可迭代对象，类似的还有链表，字符串，文件。它可以是mylist = [1, 2, 3]，也可以是mylist = [x*x for x in range(3)]。  它的缺陷是所有数据都在内存中，如果有海量数据的话将会非常耗内存。他们可以从内容从中一个一个的读取，这就是迭代。

   接着我们需要了解迭代器里的一个特殊——生成器，生成器也是一个可以迭代的对象，但是生成器每个只能迭代一次（至于为什么后面会讲），这是他特殊的原因。因为用的时候才生成。比如 mygenerator = (x*x for x in  range(3))，注意这里用到了()，它就不是数组，而上面的例子是[]。生成器这里用的是小括号，而迭代器用的是中括号。

   好了接下来得讲下他们的方法，不管是生成器还是迭代器，都可以使用他的方法，就是next（这个方法在python2里面是使用的时候是方法c.next()，在python3里面变为了函数next(c)），但是由于迭代器可以自动进行，相当于里面已经内嵌了这个方法，生成一个迭代器他可以自动往后迭代，但是生成器不一样，生成一个生成器的时候，他是定在初始状态的，这就需要我们的next来一步一步推动他们。他们还有一种方法是send()，这个相当于在next功能的基础上，再加了一个传递的功能，他可以传递参数给yield表达式，所以send(None)就相当于next参数。

   现在我们可以来谈谈yield了，其实yield就相当于一个return，不过区别就是return返回一个值，而且存在return的函数只要在主函数的某个地方调用它，那么就会马上被执行。而yield则不同，如果一个函数中有yield关键字，那么如果在主函数的某处调用这个函数，并不会马上执行，而是会先返回一个生成器，之后当调用生成器的内置函数（下划下划next下划下划()）才会真正的执行存在yield的函数，执行到yield语句的时候停止，由于yield类似于return所以可以利用yield返回一些值。

   代码1：Python中的内置函数enumerate()返回的就是一个生成器，原因就是其内部代码实现中含有yield语句，下面是对内置函数enumerate()的测试

   ```python
   def test_enumerate(sequence, start=0):
       n = start
       for elem in sequence:
           yield n, elem
           n += 1
   
   sequence=["tga", "sdfds", "sinig"]
   test=test_enumerate(sequence)
   # 查看test的类型
   print(type(test))
   idx, val=test.__next__();
   # 输出第一次使用__next__()方法，函数中yield返回的值
   print(idx, val)
   idx, val=test.__next__();
   # 输出第二次使用__next__()方法，函数中yield返回的值
   print(idx, val)
   idx, val=test.__next__();
   # 输出第三次使用__next__()方法，函数中yield返回的值
   print(idx, val)
   ```

   输出1：

   ```txt
   <class 'generator'>
   0 tga
   1 sdfds
   2 sinig
   ```

   建议1：

   - 当不是很记得含有yield函数的运行机制的时候可以通过单步调试的方法进行测试。

   代码2：以上代码可以等价于以下代码

   ```python
   def test_enumerate(sequence, start=0):
       n = start
       for elem in sequence:
           yield n, elem
           n += 1
   
   sequence=["tga", "sdfds", "sinig"]
   test=test_enumerate(sequence)
   # 查看test的类型
   print(type(test))
   # for循环可以自动迭代生成器
   for idx, val in test:
       print(idx, val)
   ```

   输出2：

   ```txt
   <class 'generator'>
   0 tga
   1 sdfds
   2 sinig
   ```

   建议2：

   - 当不是很记得含有yield函数的运行机制的时候可以通过单步调试的方法进行测试。

   代码3：由以上代码1和代码2，就有了下面用enumerate书写的版本

   ```python
   sequence=["tga", "sdfds", "sinig"]
   for idx, val in enumerate(sequence):
       print(idx, val)
   ```

   输出3：

   ```txt
   0 tga
   1 sdfds
   2 sinig
   ```


## 5.3、元组

### 5.3.3、修改元组

1. 能否对元组进行连接运算

   代码1：

   ```python
   tuple1=(1, 2, 3)
   print("连接操作之前元组的地址：" + str(id(tuple1)))
   tuple1 += (4,)
   print("连接操作之后元组的地址：" + str(id(tuple1)))
   ```

   输出1：

   ```txt
   连接操作之前元组的地址：1288959994816
   连接操作之后元组的地址：1288959940384
   ```

   总结1：

   - 使用连接运算符进行元组的连接相当于更改了元组变量的索引，并不算修改单个元素值，所以元组是允许连接操作的。

### 5.3.4、元组推导式

1. 使用元素推导式生成的是否为一个元组

   代码1：

   ```python
   import random as rd
   random_number=(rd.randint(10, 100) for i in range(10))
   print("输出random_number的数据类型：" + str(type(random_number)))
   randnum=tuple(random_number)
   print("输出randnum的数据类型：" + str(type(randnum)))
   randnum1=list(random_number)
   print("输出randnum1的数据类型：" + str(type(randnum1)))
   ```

   输出1：

   ```txt
   输出random_number的数据类型：<class 'generator'>
   输出randnum的数据类型：<class 'tuple'>
   输出randnum1的数据类型：<class 'list'>
   ```

   总结1：

   - 从以上代码可以看出使用元组推导式生成的是一个生成器，可以通过（下滑下滑next下滑下滑）函数进行迭代取值。
   - 可以通过Python中的tuple()方法和list()方法转换成元组或者列表。

# 6、字典与集合

## 6.1、字典

### 6.1.1、字典的创建和删除

1. 关于zip()函数的说明

   为传入的可迭代对象列表参数创建一个迭代器，以聚合每个可迭代对象中的元素。返回一个元组的迭代器，其中第i个元组包含每个参数序列或可迭代对象中的第i个元素。 当最短的可迭代输入耗尽时，迭代器将停止。 r如果传入一个可迭代参数，它将返回一个元组的迭代器。 如果没有参数，它将返回一个空的迭代器。 

   代码1：对zip()源代码的测试

   ```python
   def zip(*iterables):
       # zip('ABCD', 'xy') --> Ax By
       # 设置一个哨兵
       sentinel = object()
       '''
           通过列表解析为每一个可迭代对象列表iterables（传入的参数）中的元素创建迭代器。
           并将这些迭代器放入一个新的列表iterators中。
       '''
       iterators = [iter(it) for it in iterables]
       while iterators:
           result = []
           # 遍历生成的迭代器列表
           for it in iterators:
               # 每次用内置函数next获取每个迭代器的值
               elem = next(it, sentinel)
               # 结束的标志
               if elem is sentinel:
                   return
               result.append(elem)
           '''
               一个函数中有yield的语句，第一次调用此函数不会马上执行，而是会
               先返回一个生成器。之后使用__next__()方法的时候会返回一个元组。
           '''
           yield tuple(result)
   
   list1=['abc', 'edf', 'lkj', 'jiji']
   list2=[1, 2, 4, 5]
   list3=['a', 'b', 'c', 'd']
   list4=[1, 2, 3, 4, 5, 6]
   zipped1=zip(list1)
   zipped2=zip(list1, list2)
   zipped3=zip(list1, list2, list3)
   zipped4=zip(list3, list4)
   zipped5=zip()
   print("zip有一个参数时返回的数据类型：\n"+str(type(zipped1))+"\n")
   print("zip没有参数时返回的数据类型：\n"+str(type(zipped5))+"\n")
   print("zip有一个列表参数时，由list生成的结果集为：\n"+str(list(zipped1))+"\n")
   print("zip有两个等长列表参数时，由list生成的结果集为：\n"+str(list(zipped2))+"\n")
   print("zip有三个等长列表参数时，由list生成的结果集为：\n"+str(list(zipped3))+"\n")
   print("zip有两个不等长列表参数时，由list生成的结果集为：\n"+str(list(zipped4))+"\n")
   print("zip没有参数时，由list生成的结果集为：\n"+str(list(zipped5))+"\n")
   ```

   输出1：

   ```txt
   zip有一个参数时返回的数据类型：
   <class 'generator'>
   
   zip没有参数时返回的数据类型：
   <class 'generator'>
   
   zip有一个列表参数时，由list生成的结果集为：
   [('abc',), ('edf',), ('lkj',), ('jiji',)]
   
   zip有两个等长列表参数时，由list生成的结果集为：
   [('abc', 1), ('edf', 2), ('lkj', 4), ('jiji', 5)]
   
   zip有三个等长列表参数时，由list生成的结果集为：
   [('abc', 1, 'a'), ('edf', 2, 'b'), ('lkj', 4, 'c'), ('jiji', 5, 'd')]
   
   zip有两个不等长列表参数时，由list生成的结果集为：
   [('a', 1), ('b', 2), ('c', 3), ('d', 4)]
   
   zip没有参数时，由list生成的结果集为：
   []
   
   ```

   总结1：

   - zip函数接受的参数是一个可迭代对象的列表。

   - 用户手册上面说zip返回的是一个迭代器，不过通过代码测试，返回的是一个生成器会更准确。
   - 如果没有参数会返回空的生成器。
   - 如果参数是列表，通过zip函数合成元组的时候如果有一个列表没有元素了，会立刻停止。
   - 生成器每次返回一个元组，一个元组中的元素个数和传入的参数个数一样。

2. dict函数创建字典的举例

   代码1：使用dict函数创建字典

   ```python
   # 创建一个空字典
   dct1=dict()
   print("创建一个空字典：" + str(dct1))
   
   # 根据键值对创建字典
   dct2=dict(a=1, b=2, c=3)
   print("根据键值对创建字典：" + str(dct2))
   
   # 映射函数方式来构造字典
   list1=['one', 'two', 'three']
   list2=[1, 2, 3]
   dct3=dict(zip(list1, list2))
   print("映射函数方式来构造字典：" + str(dct3))
   
   # 可迭代对象方式来构造字典
   dct4=dict([('one', 11), ('two', 22), ('three', 33)])
   print("可迭代对象方式来构造字典：" + str(dct4))
   ```

   输出1：

   ```txt
   创建一个空字典：{}
   根据键值对创建字典：{'a': 1, 'b': 2, 'c': 3}
   映射函数方式来构造字典：{'one': 1, 'two': 2, 'three': 3}
   可迭代对象方式来构造字典：{'one': 11, 'two': 22, 'three': 33}
   ```

3. 通过dict对象的fromkeys()方法创建值为空的字典

   代码1：dict对象的fromkeys()方法创建值为空的字典

   ```python
   list_name=['one', 'two', 'three']
   dct=dict.fromkeys(list_name)
   print(dct)
   ```

   输出1：

   ```txt
   {'one': None, 'two': None, 'three': None}
   ```

   总结1：

   - fromkeys()是一个类方法，他会返回一个新字典，并且每个键的值默认为None。

4. 各种删除字典或字典元素的方法

   代码1：使用del语句删除一个字典

   ```python
   dct={};
   # 输出删除前的地址
   print(id(dct))
   del dct
   # 输出删除后的地址
   print(id(dct))
   ```

   输出1：

   ```txt
   2398789508544
   Traceback (most recent call last):
     File "D:\VisualStudio_source\Python 从入门到精通\test\test.py", line 49, in <module>
       print(id(dct))
   NameError: name 'dct' is not defined
   ```

   总结1：

   - 删除一个字典之后调用id()方法查看地址会报错。

   ---

   代码2：采用字典对象的方法clear()方法清空一个字典

   ```python
   dct=dict(a=1, b=2, c=3)
   print("清空前：")
   print(id(dct))
   print(dct)
   dct.clear();
   print("\n清空后：")
   print(id(dct))
   print(dct)
   ```

   输出2：

   ```txt
   清空前：
   2210859262720
   {'a': 1, 'b': 2, 'c': 3}
   
   清空后：
   2210859262720
   {}
   ```

   总结2：

   - 使用clear()方法只是把内容给清空了，并没有把内存也回收。

   ---

   代码3：使用字典对象的pop()方法删除字典元素

   ```python
   dct=dict(a=1, b=2, c=3)
   print("删除某个元素前：")
   print(dct)
   print("\n删除某个元素后：")
   val=dct.pop('b')
   print("val：" + str(val))
   print(dct)
   ```

   输出3：

   ```txt
   删除某个元素前：
   {'a': 1, 'b': 2, 'c': 3}
   
   删除某个元素后：
   val：2
   {'a': 1, 'c': 3}
   ```

   总结3：

   - 使用字典对象pop()方法可以通过指定对应的键然后将它从字典中删除，删除后会返回这个键所对应的值。

   ---

   代码4：使用字典对象的popitem()方法删除并返回字典中的一个元素

   ```python
   dct=dict(a=1, b=2, c=3)
   print("删除某个元素前：")
   print(dct)
   print("\n删除某个元素后：")
   key, val=dct.popitem()
   print(key, val)
   print(dct)
   ```

   输出4：

   ```txt
   删除某个元素前：
   {'a': 1, 'b': 2, 'c': 3}
   
   删除某个元素后：
   c 3
   {'a': 1, 'b': 2}
   ```

   总结4：

   - 字典对象的popitem()方法不需要任何的参数，它会删除最后面的一个键值对，然后将这个键值对返回。

### 6.1.2、访问字典

1. 获取字典指定键的值最好用字典对象的get()方法

   代码1：对get()方法的测试

   ```python
   dct=dict(a=1, b=2, c=3)
   print("检索一个存在于字典中的键所对应的值：")
   val=dct.get('a')
   print(val);
   print("\n检索一个不在字典中的键，get方法不设置键不存在的处理：")
   val=dct.get('d')
   print(val);
   print("\n检索一个不在字典中的键，get方法设置键不存在的处理：")
   val=dct.get('d', "此键不存在！")
   print(val)
   ```

   输出1：

   ```txt
   检索一个存在于字典中的键所对应的值：
   1
   
   检索一个不在字典中的键，get方法不设置键不存在的处理：
   None
   
   检索一个不在字典中的键，get方法设置键不存在的处理：
   此键不存在！
   ```

   总结1：

   - 当get方法检索一个不存在的键的时候，如果没有在get方法中给出第二个参数，那么采用默认情况下的处理，返回关键字None，如果指定了第二个参数那么会返回第二个参数的内容。

### 6.1.3、遍历字典

1. 使用for通过字典对象的items()方法返回键值对元组列表

   代码1：

   ```python
   dct=dict(a=1, b=2, c=3)
   print("输出dct.items()的值：")
   print(dct.items())
   print("\n输出dct.items()的类型：")
   print(type(dct.items()))
   print("\n遍历dct字典：")
   for item in dct.items():
       print(item)
   ```

   输出1：

   ```txt
   输出dct.items()的值：
   dict_items([('a', 1), ('b', 2), ('c', 3)])
   
   输出dct.items()的类型：
   <class 'dict_items'>
   
   遍历dct字典：
   ('a', 1)
   ('b', 2)
   ('c', 3)
   ```

   总结1：

   - 从以上输出可以看出字典对象的items()方法返回的是一个类似于元组列表的数据。
   - 用for循环遍历items()方法的返回值，每次迭代产生的item是一个二维元组，第一个值是键，第二个值是值。