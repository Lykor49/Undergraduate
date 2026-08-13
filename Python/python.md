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
- if / else / elif

```python
age = 20
if age >= 6:
    print('teenager')
elif age >= 18:
    print('adult')
else:
    print('kid')
```

# 2.5 模式匹配
- match: match - case匹配

```
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

- 复杂匹配: 匹配列表

```
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
