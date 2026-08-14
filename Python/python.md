# Python Notes

- 日期: 2026.8.13

# 1. 输入和输出

## 命令行模式 / Python交互模式
- 命令行模式, 提示符 PS C:\>
- Python交互模式, 提示符 >>>

## 输出和输入
- print() 可以向屏幕上输出指定的文字
 - print('hello, world') -> hello, world
 - print('The quick brown fox', 'jumps over', 'the lazy dog') -> The quick brown fox jumps over the lazy dog
 - print(100 + 200) -> 300
 - print('100 + 200 =', 100 + 200) -> 100 + 200 = 300

- input() 用户输入字符串, 并存放到一个变量里
 - name = input() -> 用户输入Lykor -> name变量为Lykor

# 2 Python基础

# 2.1 数据类型和变量

## 数据类型
- 整数 ex. 1, 100, -8080 二进制, 十六进制
- 浮点数 ex. 1.23, 1.23e9, 1.2e-5
- 字符串: 单引号' '或双引号" "括起来的任意文本
 - 转义字符: \ \n \t 
- 布尔值: 只有True、False两种值
- 空值 None, None不能理解为0, 因为0是有意义的

## 变量
- 变量: 不仅可以是数字, 还可以是任意数据类型; 变量名必须是大小写英文、数字和_的组合, 且不能用数字开头

## 常量
- 常量: 不能变的变量; 通常用全部大写的变量名表示常量

# 2.2 list / tuple

## list 列表
- list 是一种有序的集合, 可以随时添加和删除其中的元素
 - classmates = ['Michael', 'Bob', 'Tracy']
 - len(classmates) -> 3
 - classmates[0] -> 'Michael'
 - classmates[-1] -> 'Tracy'
 - classmates.append('Adam') -> 将Adam追加元素到末尾
 - classmates.insert(1, 'Jack') -> 将元素插入到指定的位置
 - classmates.pop() -> 删除末尾的元素

## tuple 元祖
- tuple 与list类似, 但是tuple一旦初始化就不能修改
 - classmates = ('Michael', 'Bob', 'Tracy')

# 2.3 dict / set

## dict 字典
- dict / map: 使用键-值(key-value)存储, 具有极快的查找速度
 - d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
 - d['Michael'] -> 95

## set 
- set: 也是一组Key的集合, 但不存储value
 - s = {1, 2, 3}

# 2.4 条件判断
## if / else / elif

```python
age = 20
if age >= 18:
    print('teenager')
elif age >= 6:
    print('adult')
else:
    print('kid')
```

# 2.5 模式匹配
## match: match - case匹配

```python
age = 15
match age:
    case x if x < 10:
        print(f'< 10 years old: {x}')
    case 10:
        print('10 years old.')
    case 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18:
        print('11~18 years old.')
    case 19:
        print('19 years old.')
    case _:
        print('not sure.')
```

## 复杂匹配: 匹配列表

```python
args = ['gcc', 'hello.c', 'world.c']
# args = ['clean']
# args = ['gcc']

match args:
    # 如果仅出现gcc，报错:
    case ['gcc']:
        print('gcc: missing source file(s).')
    # 出现gcc，且至少指定了一个文件:
    case ['gcc', file1, *files]:
        print('gcc compile: ' + file1 + ', ' + ', '.join(files))
    # 仅出现clean:
    case ['clean']:
        print('clean')
    case _:
        print('invalid command.')
```

# 2.6 循环
## for...in 循环: 依次把list或tuple中的每个元素迭代出来
 
```python
names = ['Michael', 'Bob', 'Tracy']
for name in names:
    print(name)
```

## while 循环: 只要条件满足, 就不断循环, 条件不满足时退出循环

```python
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print(sum)
```

## break: 在循环中break可以提前退出循环

```python
n = 1
while n <= 100:
    if n > 10: # 当n = 11时，条件满足，执行break语句
        break # break语句会结束当前循环
    print(n)
    n = n + 1
print('END')
```

## continue: 跳过当前的这次循环, 直接开始下一次循环

```python
n = 0
while n < 10:
    n = n + 1
    if n % 2 == 0: # 如果n是偶数，执行continue语句
        continue # continue语句会直接继续下一轮循环，后续的print()语句不会执行
    print(n)
```

## range: 生成一串整数, 常和for循环一起使用
- range(起点, 终点, 步长)

```python
for i in range(5):
    print(i)
```

## enumerate: 遍历数据时, 同时得到“序号”和“元素”

```python
names = ['Tom', 'Mike', 'Jack']

for i, name in enumerate(names):
    print(i, name)
```

## zip: 同时遍历两个或多个序列

```python
names = ['Tom', 'Mike', 'Jack']
scores = [80, 90, 85]

for name, score in zip(names, scores):
    print(name, score)
```

# 3 函数

# 3.1 定义函数
- def: 依次写出函数名、括号、括号中的参数和冒号:

```python
def my_abs(x):
    if x >= 0:
        return x
    else:
        return -x

print(my_abs(-99))
```

# 3.2 函数的参数
- 位置参数: 下方x, n均为位置参数

```python
def power(x, n):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
```

- 默认参数

```python
def power(x, n=2):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
```

- 可变参数: 传入的参数个数是可变的, 可以是1个、2个到任意个

```python
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
```

- 关键字参数: 关键字参数允许你传入0个或任意个含参数名的参数, 这些关键字参数在函数内部自动组装为一个dict

```python
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)

>>> person('Michael', 30)
name: Michael age: 30 other: {}
```

- 日期: 2026.8.14

# 4 高级特性

# 4.1 切片
- L[0:3]: 从索引0开始取, 直到索引3为止, 但不包括索引3; 即0, 1, 2, 正好是三个元素

```python
L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']
>>> L[0:3]
['Michael', 'Sarah', 'Tracy']
>>> L[:3]
['Michael', 'Sarah', 'Tracy']
>>> L[1:3]
['Sarah', 'Tracy']
>>> L[-1]      # 最后一个元素
'Jack'
>>> L[-2:]     # 最后两个元素
['Bob', 'Jack']
>>> L[::2]     # 每隔一个取一个
['Michael', 'Tracy', 'Jack']
>>> L[::-1]    # 倒序
['Jack', 'Bob', 'Tracy', 'Sarah', 'Michael']
```

# 4.2 迭代
- 迭代 Iteration: 给定一个list或tuple, 可以通过for循环来遍历这个list或tuple

```python
>>> d = {'a': 1, 'b': 2, 'c': 3}
>>> for key in d:
...     print(key)
...
a
c
b

names = ['Tom', 'Jack', 'Mike']
for i, name in enumerate(names):
    print(i, name)

names = ['Tom', 'Jack']
scores = [90, 80]
for name, score in zip(names, scores):
    print(name, score)

d = {'a': 1, 'b': 2, 'c': 3}
for key, value in d.items():
    print(key, value)
```

# 4.3 列表生成式
- 列表生成式 List Comprehensions: 用来创建list的生成式
- 把要生成的元素x*x放到前面, 后面跟for循环

```python
>>> [x * x for x in range(1, 11)]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
>>> [x * x for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]
```

# 4.4 生成器
- 生成器 generator: 边循环边计算的机制
- generator保存的是算法, 每次调用next(g), 就计算出g的下一个元素的值, 直到计算到最后一个元素

```python
>>> g = (x * x for x in range(10))
>>> next(g)
0
>>> next(g)
1
>>> next(g)
4

g = (x * x for x in range(5))
for x in g:
    print(x)
```

# 4.5 迭代器
- 迭代器 Iterator: 可以被next()函数调用并不断返回下一个值的对象

# 5 模块

# 5.1 使用模块
- 模块定义: 一个.py文件就是一个Python模块(module)
- import xxx -> 导入整个模块; 使用时一般写 xxx.xxx
- from xxx import yyy -> 从xxx模块/包中导入指定的yyy; 可以直接调用 yyy

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-

' a test module '

__author__ = 'Michael Liao'     ## 作者信息    

import sys                      ## 导入Python标准库中的sys模块

def test():
    args = sys.argv
    if len(args)==1:
        print('Hello, world!')
    elif len(args)==2:
        print('Hello, %s!' % args[1])
    else:
        print('Too many arguments!')

if __name__=='__main__':
    test()
```

# 6 类与对象
- 面对对象编程 Object Oriented Programming (OOP)
- OOP把对象作为程序的基本单元, 一个对象包含了数据和操作数据的函数

# 6.1 类和实例
- 面对对象最重要的概念就是类(class)和实例(Instance)
- 类是抽象的模版, 实例是根据类创建出来的一个个具体的“对象”

```python
class Student(object):                     ## class后面接类名, 通常是大写开头的单词
    def __init__(self, name, score):       ## 将认为必须绑定的属性强制填写进去
        self.name = name
        self.score = score

>>> bart = Student('Bart Simpson', 59)     ## self指向创建的实例本身, 不需要传
>>> bart.name
'Bart Simpson'
>>> bart.score
59

## 数据封装: 可以直接在实例上调用, 直接操作对象内部的数据, 无需知道方法内部的实现细节
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score

    def print_score(self):
        print('%s: %s' % (self.name, self.score))
```

# 6.2 访问限制
- 让内部属性不被外部访问, 可以把属性的名称前加上两个下划线__, python中实例变量名以__开头, 为私有变量, 只有内部可以访问

```python
class Student(object):
    def __init__(self, name, score):
        self.__name = name
        self.__score = score

    def print_score(self):
        print('%s: %s' % (self.__name, self.__score))

    def get_name(self):             ## 外部代码获取name和score需要内部加函数
        return self.__name

    def get_score(self):
        return self.__score

    def set_score(self, score):     ## 外部代码修改score
        self.__score = score
```

# 6.3 继承和多态
- 当我们定义一个class的时候, 可以从某个现有的class继承, 新的class称为子类(Subclass), 而被继承的class称为基类、父类或超类(Base class、 Super class)
- 继承: 子类获得了父类的全部功能; 子类可以新增自己的方法; 子类可以重写父类的方法

```python
class Animal:
    def run(self):
        print("Animal is running")

class Dog(Animal):
    def run(self):
        print("Dog is running")
```

- 多态: 同一个方法名; 不同子类可以有不同实现; 调用时会根据实际对象执行对应的方法
- 多态好处: 当需要传入子类的一些变量时, 只需要接收父类数据类型就行, 这样不需要修改依赖父类的一些函数





