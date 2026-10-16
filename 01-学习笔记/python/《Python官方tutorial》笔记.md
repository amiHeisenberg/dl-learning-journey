**python提示符**为`>>>`
**python语言风格**
- 缩进，同一块语句每一行缩进相同。注意用四个空格做缩进，不混用Tab和空格；交互式输入复合语句时，提示符变成 `...`，要在最后输入空白行表示完成（因为解析器不知道哪一行代码是代码块的最后一行）
- 用空行分隔函数和类，及函数内较大的代码块
- 最好把注释放到单独一行
- 使用文档字符串
- 运算符前后、逗号后要用空格，但不要直接在括号内使用
**python注释**以`#`开头，可以在行开头或在空白符与代码之后
**运算符** 
- `+`, `-`, `*` ,`/`(返回浮点数), `//`（返回商）, `%`（返回余数）, `**`（计算乘方）,`=` (赋值，交互模式下，上次输出的表达式会赋给变量 `_`)
- `\`(转义符，如果不希望前置 `\` 的字符转义成特殊字符，可以使用 _原始字符串_，在引号前添加 `r` 即可print(r'C:\this\name'))
- 比较运算符 `in`&`not in`判断元素是否在容器内，`is`&`is not`判断两个对象是否是同一个对象,`<`,`>`,`==`
**数据类型**
- 字符串`str`，用成对的单引号 `'...'`或双引号 `"..."`标示。字符串可以用 `+` 合并（粘到一起），也可以用 `*` 重复；相邻的两个或多个 _字符串字面值_ （引号标注的字符）会自动合并；支持索引和切片；内置函数 `len()` 返回字符串长度
**列表list**：用方括号标注，逗号分隔的一组值（可不同类型）。支持合并，索引和切片；可嵌套列表;列表数据类型具有很多[方法]([5. 数据结构 — Python 3.15.0 文档](https://docs.python.org/zh-cn/3/tutorial/datastructures.html#more-on-lists))
```
#list的部分方法示例

fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
fruits.count('apple') #输出2
fruits.count('tangerine') #输出0
fruits.index('banana') #输出3。从0号位开始查找并返回'banana'首次出现的索引
fruits.index('banana', 4)  #输出6。从 4 号位开始查找并返回下一个 banana的索引
fruits.reverse() #翻转列表中的元素
fruits #输出['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
fruits.append('grape') #在列为添加项
fruits #输出['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']
fruits.sort() #原地排序列表中的元素
fruits #输出['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
fruits.pop() #输出'pear'。移除列表中给定位置上的条目，并返回该条目；如果未指定索引号，则 `a.pop()` 将移除并返回列表中的最后一个条目。

# `insert`, `remove` 或 `sort` 等仅修改列表的方法都不会打印返回值 -- 它们返回默认值 `None`。 [[1]](https://docs.python.org/zh-cn/3/tutorial/datastructures.html#id2) 这是适用于 Python 中所有可变数据结构的设计原则。
```
**字典dic**: 用 `{}` 包裹，存放键值对 key: value。`key`不能重复且需为不可变类型
- 创建字典
```
# 方式1：大括号直接写
d1 = {"name":"小明", "age":18}

# 方式2：空字典，后面慢慢添加
d2 = {}
d2["name"] = "小红"
print(d2) # {'name': '小红'}
```
- 读取字典中的值：用 `字典[键]`
```
d = {"name":"小明", "age":18}
print(d["name"]) # 输出 小明
print(d["age"])  # 输出 18
```
- 添加修改键值对：用`字典[key] = 值`
- 删除字典元素：`del 字典[key]`直接删除键值对；`.pop(key)`：删除并返回被删掉的值
- 一些字典方法
	- `.items()`取出所有 `(key, value)` 成对的数据，专门用于 for 循环
	- `.copy()`复制一份全新独立字典，修改副本不会影响原字典
	- `.keys()`：只取出所有键，`.values()`：只取出所有值


**切片与索引**：切片返回列表，索引返回元素本身
**内置函数**
- `print()`输出字符串不带引号；会在各参数项之间插入一个空格；多个`printf()`使用关键字`end`可以取消输出后的换行或以另一个字符串结尾；`f-string`格式化字符串`print(f"Found an even number {num}")`等价于`print("Found an even number", num)`
- `input(提示文字)`：获取用户输入（文本）
- `range()`函数：生成等差数列
```
list(range(5)) #[0,1,2,3,4]
list(range(5, 10)) #[5,6,7,8,9]
list(range(0, 10, 3)) #[0,3,6,9]
list(range(-10, -100, -30)) #[-10,-40,-70]
```
**关键字**
- `in`判断是否在容器内/for遍历使用
- `def`定义函数
- `lambda`创建小巧匿名函数
- `raise`主动抛出异常
- `try`尝试执行代码
- `pass`空语句，占位置
- `global`函数内声明全局变量
- 逻辑布尔
- `as`起别名
**if 语句**
`if...elif...elif...else...`,else为可选的
```
x = int(input("Please enter an integer: ")) 
# *input(提示文字)：获取用户输入（文本）；int(内容)：把文本数字转成整数*

if x < 0:
    x = 0
    print('Negative changed to zero')
elif x == 0:
    print('Zero')
elif x == 1:
    print('Single')
else:
    print('More')
```
循环的else子句
```
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break
    else:
        # 循环到底未找到一个因数
        print(n, 'is a prime number')
```
**for 语句**
```
# 创建示例多项集
users = {'Hans': 'active', 'Éléonore': 'inactive', '景太郎': 'active'}

# 策略：迭代一个副本
# *循环遍历副本copy（副本固定不变），然后去删除原字典中的内容。防止字典大小改变，遍历器混乱。*
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]

# 策略：创建一个新多项集
active_users = {}
for user, status in users.items():
    if status == 'active':
        active_users[user] = status
```
**break&continue语句**
`break`语句跳出最近一层的for或while循环，`continue`只跳过本次迭代的后面部分转而继续执行循环的下一次迭代
**pass语句**
pass语句不执行任何动作。语法上需要一个语句，但程序毋需执行任何动作时，可以使用该语句。
```
while True:
    pass  # 无限等待键盘中断 (Ctrl+C)
```
**match语句**
match接受一个表达式并把它的值与一个或多个 case 块给出的一系列模式进行比较，只有第一个匹配的模式会被执行，并且它还可以提取值的组成部分（序列的元素或对象的属性）赋给变量。如果没有匹配的case，则不执行任何分支。
```
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:                           #变量名 `_` 被作为通配符并必定会匹配成功
            return "Something's wrong with the internet"
```
**函数**
1. 定义函数:使用关键字`def`，后跟函数名与括号内的形参列表。函数语句从下一行开始，并且必须缩进。
- 无/有return
```
def fib(n):    # 打印小于 n 的斐波那契数列
    """Print a Fibonacci series less than n."""    #文档字符串，见下方注释
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a+b
    print()
#无return则默认返回None

# 现在调用我们刚定义的函数：
fib(2000)
```
   ^[函数内的第一条语句是字符串时，该字符串就是文档字符串，也称为 _docstring_，详见 [文档字符串](https://docs.python.org/zh-cn/3/tutorial/controlflow.html#tut-docstrings)。利用文档字符串可以自动生成在线文档或打印版文档，还可以让开发者在浏览代码时直接查阅文档；Python 开发者最好养成在代码中加入文档字符串的好习惯。]
   ```
   def fib2(n):  # 返回斐波那契数组直到 n
    """Return a list containing the Fibonacci series up to n."""
    result = []
    a, b = 0, 1
    while a < n:
        result.append(a)    # 见下方注释
        a, b = b, a+b
    return result

f100 = fib2(100)    # 调用它
f100                # 输出结果
   ```
   ^[语句 `result.append(a)` 调用了列表对象 `result` 的 _方法_。 方法是‘从属于’对象的函数，其名称为 `obj.methodname`，其中 `obj` 是某个对象（可以是一个表达式），`methodname` 是由对象的类型定义的方法名称。 不同的类型定义了不同的方法。 不同的类型的方法可以使用相同的名称而不会产生歧义。 （使用 _类_ 可以定义自己的对象类型和方法，参见 [类](https://docs.python.org/zh-cn/3/tutorial/classes.html#tut-classes)。）]
   - 函数的参数
	  - 默认值参数：默认值在 定义作用域里的函数定义中求值；且默认值只计算一次，当默认值为列表、字典或类实例等可变对象时，默认值会被更新
  ```
  def ask_ok(prompt, retries=4, reminder='Please try again!'):  #prompt为必选参数，另外两个为有默认值的可选参数
    while True:
        reply = input(prompt)
        if reply in {'y', 'ye', 'yes'}:
            return True
        if reply in {'n', 'no', 'nop', 'nope'}:
            return False
        retries = retries - 1
        if retries < 0:
            raise ValueError('invalid user response')   #ValueError表示值错误的异常类，TypeError表示类型错误的异常类
        print(reminder)
  ```
2. 函数的调用
   函数调用时，关键字参数必须跟在位置参数后面。

**数据结构**
1. 列表
- 用方括号标注，逗号分隔的一组值（可不同类型）
- 列表实现堆栈：后进后出，`list.append()`将条目添加至栈顶，`list.pop()`从栈顶取出条目
- 列表实现队列：先进先出，但这样使用很低效（在列表开头插入或弹出条目所有元素都要移动一位）。实现队列最好用 [`collections.deque`](https://docs.python.org/zh-cn/3/library/collections.html#collections.deque "collections.deque")，可以快速从两端添加或删除元素。
```
from collections import deque   
#`deque` 是从 `collections` 导入的类；deque(参数) 就是调用它的构造方法，用来创建一个双端队列实例。
queue = deque(["Eric", "John", "Michael"]) #deque(可迭代对象)：用可迭代对象里的元素，初始化双端队列
queue.append("Terry")           # Terry 到了
queue.append("Graham")          # Graham 到了
queue.popleft()                 # 第一个到的现在走了，popleft删除并返回最左端元素
#输出'Eric'
queue.popleft()                 # 第二个到的现在走了
#输出'John'
queue                           # 按到达顺序排列的剩余队列
#输出deque(['Michael', 'Terry', 'Graham'])
```
- 列表推导式：列表推导式的方括号内包含以下内容：一个表达式，后面为一个 `for` 子句，然后，是零个或多个 `for` 或 `if` 子句。结果是由表达式依据 `for` 和 `if` 子句求值计算而得出一个新列表。
```
[(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
#构造得到[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
#等价于
combs = []
for x in [1,2,3]:
    for y in [3,1,4]:
        if x != y:
            combs.append((x, y))
combs
```
- 嵌套的列表推导式：列表推导式中的初始表达式可以是任何表达式，甚至可以是另一个列表推导式。
```
[[row[i] for row in matrix] for i in range(4)]
#构造得到[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
- 列表和列表推导式中的解包：用 `*` 来“解包”可迭代对象的元素，将每个元素单独提供作为函数的参数
```
x = [[1, 2, 3], 'cat', {'spam': 'eggs'}]
[[*element] for element in x]
#输出[1, 2, 3, 'c', 'a', 't', 'spam']
```
2. `del`语句
	可以按索引而不是按值从一个列表移除条目,如`del a[0]`, 不会像`pop()`一样返回一个值。 `del` 语句还可被用来从列表移除切片或清空整个列表，如`del a[2:4]``del a[:]`，（之前我们通过将一个空列表赋值给切片实现此功能），也可用于删除整个变量`del a`(此后再引用a会报错)
3. 元组和序列
	元组，列表，字符串都是序列。
- 元组由多个用逗号隔开的值组成(注意空元组用一对空圆括号创建；只有一个元素的元组通过在这个元素后添加逗号来构建），输入时，圆括号可有可无，不过尽量有，输出时，元组都要由圆括号标注。
- 元组与列表很像，但使用场景不同，用途也不同。元组是 [immutable](https://docs.python.org/zh-cn/3/glossary.html#term-immutable) （不可变的），一般可包含异质元素序列，通过解包（见本节下文）或索引访问（如果是 [`namedtuples`](https://docs.python.org/zh-cn/3/library/collections.html#collections.namedtuple "collections.namedtuple")，可以属性访问）。列表是 [mutable](https://docs.python.org/zh-cn/3/glossary.html#term-mutable) （可变的），列表元素一般为同质类型，可迭代访问。
```
t = 12345, 54321, 'hello!'
t[0]
#输出12345
t
输出(12345, 54321, 'hello!')
# 元组可以嵌套：
u = t, (1, 2, 3, 4, 5)
u
#输出((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
# 元组是不可变对象：
t[0] = 88888   #会报错
# 但它们可以包含可变对象：
v = ([1, 2, 3], [3, 2, 1])
```
4. 集合
- 集合是由不重复元素组成的无序多项集（迭代或打印时也无序）。
- 创建集合用花括号或 [`set()`](https://docs.python.org/zh-cn/3/builtins/stdtypes.html#set "set") 函数。（注意，创建空集合只能用 `set()`，不能用 `{}`，`{}` 创建的是空字典）
-  基本用法包括成员检测和消除重复元素。 集合对象还支持合集、交集、差集和对称差集等数学运算。

```
a = set('abracadabra')
b = set('alacazam')
a                                  # a 中独有的字母{'a', 'r', 'b', 'c', 'd'}
a - b                              # 存在于 a 中但不存在于 b 中的字母{'r', 'd', 'b'}
a | b                              # 存在于 a 或 b 中或两者中皆有的字母{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
a & b                              # 同时存在于 a 和 b 中的字母{'a', 'c'}
a ^ b                              # 存在于 a 或 b 中但非两者中皆有的字母{'r', 'd', 'b', 'm', 'z', 'l'}
```
5. 字典
- 可以把字典理解为 _键值对_ 的集合，但字典的键必须唯一
- 字典的创建：在花括号里输入逗号分隔的键值对，这也是字典的输出方式，空花括号 `{}` 用于创建空字典；[`dict()`](https://docs.python.org/zh-cn/3/builtins/stdtypes.html#dict "dict") 构造函数用键值对序列创建字典;字典推导式用键值表达式创建字典
- 与以连续整数为索引的序列不同，字典是以 _键_ 来索引的，键可以是任何不可变类型：字符串，数字，仅包含字符串、数字或元组的元组；如果一个元组直接或间接地包含了任何可变对象，则不可以用作键；列表不能作为键，因为列表可使用索引赋值、切片赋值或`list.append()`等方法进行修改
- 字典的主要操作：通过键来存储值并根据给定的键来提取值；通过 `del` 可以删除键值对；`list(d)` 操作，按插入次序返回该字典中所有键的列表
```
tel = {'jack': 4098, 'sape': 4139}     #等价于a = dict([('jack', 4098), ('sape', 4139)])
tel['guido'] = 4127
tel
#输出{'jack': 4098, 'sape': 4139, 'guido': 4127}
tel['jack']                            #提取键'jack'对应的值
#输出4098
tel['irv']                             #引发keyError,提取不存在的键
del tel['sape']                        #删除键值对
tel['irv'] = 4127                      #添加键值对 
tel
#输出{'jack': 4098, 'guido': 4127, 'irv': 4127}
list(tel)                              #按插入次序返回该字典中所有键的列表
#输出['jack', 'guido', 'irv']
sorted(tel)                            #返回排序后字典中所有键的列表
#输出['guido', 'irv', 'jack']  
'guido' in tel
#输出True
'jack' not in tel
#输出False
```
6. 循环的技巧
- 字典执行循环时，可以使用 [`items()`](https://docs.python.org/zh-cn/3/builtins/stdtypes.html#dict.items "dict.items") 方法同时提取键及其对应的值：
```
knights = {'gallahad': 'the pure', 'robin': 'the brave'}
for k, v in knights.items():
    print(k, v)
```
- 序列执行循环时，可以使用 [`enumerate()`](https://docs.python.org/zh-cn/3/builtins/functions.html#enumerate "enumerate") 函数同时取出位置索引和对应的值：
```
for i, v in enumerate(['tic', 'tac', 'toe']):
    print(i, v)
```
- 同时循环两个或多个序列时，用 [`zip()`](https://docs.python.org/zh-cn/3/builtins/functions.html#zip "zip") 函数可以将其内的元素一一匹配：
```
questions = ['name', 'quest', 'favorite color']
answers = ['lancelot', 'the holy grail', 'blue']
for q, a in zip(questions, answers):
    print('What is your {1}?  It is {2}.'.format(q, a))  
    #等价于print(f'what is your {q}? it is {a}')，`f-string`直接在{}中嵌入内容
```
- [`reversed()`](https://docs.python.org/zh-cn/3/builtins/functions.html#reversed "reversed") 函数实现逆向排序，[`sorted()`](https://docs.python.org/zh-cn/3/builtins/functions.html#sorted "sorted") 函数返回重新排序的序列， [`set()`](https://docs.python.org/zh-cn/3/builtins/stdtypes.html#set "set") 去除序列中的重复元素
- 在循环中修改列表的内容时，创建新列表比较简单，且安全
```
import math
raw_data = [56.2, float('NaN'), 51.7, 55.3, 52.5, float('NaN'), 47.8]
filtered_data = []
for value in raw_data:
    if not math.isnan(value):
        filtered_data.append(value)

filtered_data
```
7. 序列和其他类型的比较
```
(1, 2, 3)              < (1, 2, 4)       
#先比较前两个对应元素，如果不相等，则可确定比较结果；如果相等，则比较之后的两个元素
[1, 2, 3]              < [1, 2, 4]
'ABC' < 'C' < 'Pascal' < 'Python'        
#如果一个序列是另一个的初始子序列，则较短的序列可被视为较小（较少）的序列；对字符串来说，字典式顺#序使用 Unicode 码位序号排序单个字符
(1, 2, 3, 4)           < (1, 2, 4)
(1, 2)                 < (1, 2, -1)
(1, 2, 3)             == (1.0, 2.0, 3.0)
(1, 2, ('aa', 'ab'))   < (1, 2, ('abc', 'a'), 4)
```

**模块**
模块是包含 Python 定义和语句的文件，模块中的定义可以导入到其他程序中
```
import fibo    
#导入写好的`fibo`外部模块，但不会直接把 `fibo` 中定义的函数名称添加到当前 namespace 中,只是将#模块名称 `fibo` 添加到那里。 使用该模块名称你可以访问其中的函数:
fibo.fib(1000) #调用fibo中的函数fib
#如果经常使用某个函数，可以把它赋值给局部变量：
fib(500)
```
1. 模块的使用
	`if __name__ == "__main__":`
	- 当作模块导入,if 内代码不执行
		- `import fibo`
		- `from fibo import fib`
		- `import fibo as fib`
		- `from fibo import fib as fibonacci`
	- 作为脚本直接被执行：if 内代码运行
2. 模块的搜索路径
	当导入一个名为 `spam` 的模块时，
	- 第一步：查找内置模块查看 `sys.builtin_module_names`，是否存在`spam`内置模块。若找到：直接加载，结束搜索。若未找到则进入下一步。
	- 第二步：按`sys.path`顺序遍历目录查找，`sys.path`优先级从高到低： ① 当前脚本所在目录（最高优先级） ② `PYTHONPATH`自定义环境目录 ③ Python 默认安装目录（`Lib`文件夹，含标准库源码；`Lib/site-packages`存放 pip 第三方包）
3. 标准模块：Python 自带一个标准模块的库
4. `dir()`函数：内置函数 [`dir()`](https://docs.python.org/zh-cn/3/builtins/functions.html#dir "dir") 用于查找模块定义的名称，返回经过排序的字符串列表
	- 带参数 `dir(对象)`：查看指定模块 / 对象里面的名字，如`dir(fibo)`查看 fibo 模块的属性、函数名`['__name__', 'fib', 'fib2']`
	- 无参数 `dir()`：列出前作用域里已经定义好的全部名称（变量、模块、函数等）
	- `dir()`默认不会直接展示内置函数 / 内置变量

**包**
是通过使用“带点号模块名”来构造 Python 模块命名空间的一种方式。 例如，模块名 `A.B` 表示名为 `A` 的包中名为 `B` 的子模块。（使用带点号模块名可以避免模块名冲突，使用模块可以避免全局变量名冲突）
- 从包中导入单个模块
	- `import sound.effects.echo`
	- `from sound.effects import echo`
- `from sound.effects import *`
	- `__init__.py`的`__all__`列表：专门控制`from xxx import *`导入哪些名字 `__all__ = ["echo", "surround", "reverse"]`
	- 若无`__all__`：`import *`不会自动导入全部子模块，只导入`__init__.py`中预先定义 / 加载好的名称
	- 名字遮蔽：若`__init__.py`内定义同名函数，会覆盖同名子模块
	- 规范：正式代码不推荐`import *`，容易名字冲突；推荐显式导入：`from sound.effects import echo`
- 相对导入：使用点号来表示相对导入所涉及的当前包和上级包
