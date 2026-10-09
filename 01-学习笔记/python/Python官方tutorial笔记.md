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
- 比较运算符
**数据类型**
- 字符串`str`，用成对的单引号 `'...'`或双引号 `"..."`标示。字符串可以用 `+` 合并（粘到一起），也可以用 `*` 重复；相邻的两个或多个 _字符串字面值_ （引号标注的字符）会自动合并；支持索引和切片；内置函数 `len()` 返回字符串长度
**列表list**：用方括号标注，逗号分隔的一组值（可不同类型）。支持合并，索引和切片；可通过`listname.append()`在列表末尾添加新元素；可嵌套列表
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


