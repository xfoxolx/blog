---
title: Python Tutorial 1 ⚡
published: 2024-09-18
description: "Python Tutorial"
image: "../cover/dark-4.jpg"
tags: ["Python", "Language"]
category: Language
draft: false
---

## 1. Python 基础

### 1.1 标识符命名规范 📏

标识符用于命名变量、函数、类等，规范命名可提升代码可读性与维护性。以下为 PEP 8 推荐的命名规则：

| 标识符类型                         | 命名风格                      | 示例             | 说明                                                        |
| ---------------------------------- | ----------------------------- | ---------------- | ----------------------------------------------------------- |
| **包（Package）**                  | 全小写，可用下划线            | my_package       | 短小、描述性强，避免下划线除非提高可读性。                  |
| **模块（Module）**                 | 全小写，可用下划线            | my_module.py     | 与包规范相同，简短且可读。                                  |
| **类（Class）**                    | CapWords（驼峰式首字母大写）  | MyClass          | 内部类可加前导下划线（如 \_InternalClass）。                |
| **函数/方法（Function/Method）**   | 全小写 + 下划线（snake_case） | my_function()    | 描述性强，避免特殊符号。                                    |
| **变量/参数（Variable/Argument）** | 全小写 + 下划线（snake_case） | my_variable      | 私有变量加单下划线前缀（如 \_private_var）。                |
| **常量（Constant）**               | 全大写 + 下划线               | MY_CONSTANT      | 仅用于真正不变的值，如配置常量。                            |
| **私有属性（Private Attributes）** | 双下划线前缀                  | \_\_private_attr | 避免从子类直接访问，使用 Foo.\_Foo\_\_attr 访问（不推荐）。 |

> 💡 **提示**: 遵循 PEP 8 命名规范，确保代码一致性和团队协作效率！

### 1.2 注释 ✍️

注释提高代码可读性，Python 支持以下方式：

```python
# 单行注释：简洁说明代码功能
"""
多行注释：用于函数、类或模块的详细说明。
可跨多行，常用于文档字符串（docstring）。
"""
'''
另一种多行注释写法，与 """ 等效。
'''
```

### 1.3 编码声明

为确保代码跨平台兼容性和字符编码正确，文件头部通常包含以下声明：

```python
#!/usr/bin/env python3  # 指定 Python 解释器（推荐，跨平台）
# -*- coding: utf-8 -*-  # 设置文件编码为 UTF-8
```

## 2. 运算符

Python 提供多种运算符，用于数学计算、比较、逻辑判断等。以下按类别整理：

### 2.1 算术运算符

- `+`（加）、`-`（减）、`*`（乘）、`/`（除）
- `//`（整除）、`%`（取模）、`**`（幂）

### 2.2 比较运算符

- `==`（等于）、`!=`（不等于）、
- `>`（大于）、`<`（小于）、`>=`（大于等于）、`<=`（小于等于）

### 2.3 赋值运算符

- `=`（简单赋值）
- `+=`、`-=`、`*=`、`/=`（复合赋值）
- `//=`（整除赋值）、`%=`（取模赋值）、`**=`（幂赋值）

### 2.4 逻辑与位运算符

- **逻辑运算符**：`and`（与）、`or`（或）、`not`（非）
- **位运算符**：`&`（按位与）、`|`（按位或）、`^`（按位异或）、`~`（按位取反）、`<<`（左移）、`>>`（右移）

### 2.5 成员与身份运算符

- **成员运算符**：`in`（在其中）、`not in`（不在其中）
- **身份运算符**：`is`（同一对象）、`is not`（不同对象）

## 3. 数字类型

### 3.1 整数（int）

表示无小数部分的数字，无大小限制。

```py
int_number = 1
number_one = number_two =1
number_one, number_two = 6, 8
abs(x)                            # 返回整数的绝对值。
pow(x, y)                         # 计算 x 的 y 次幂，相当于 x ** y。
divmod(x, y)                      # 返回 (x // y, x % y) 的元组。
bin(x) oct(x) hex(x)              # 将整数转换为二进制、八进制、十六进制字符串。
```

### 3.2 浮点数（float）

表示带小数部分的数字，遵循 IEEE 754 双精度标准（64 位）。注意浮点数精度问题。

```python
float_number = 3.14
sci_notation = 2.4e3    # 2400.0
small_num = 1.23e-2     # 0.0123
round(3.14159, 2)       # 3.14（四舍五入）
import math
math.floor(3.7)         # 3（向下取整）
math.ceil(3.2)          # 4（向上取整）
from math import isclose
isclose(0.1 + 0.2, 0.3, rel_tol=1e-9)  # True（容差比较）
```

**特殊值**:

```python
float('inf')   # 正无穷
float('-inf')  # 负无穷
float('nan')   # 非数字（Not a Number）
```

### 3.3 复数（complex）

形如 `a + bj`，其中 `a` 是实部，`b` 是虚部，`j` 表示虚数单位。

```python
complex_num = complex(3, 4)  # 3 + 4j
complex_num = 3 + 4j
print(complex_num.real)      # 3.0（实部）
print(complex_num.imag)      # 4.0（虚部）
print(complex_num.conjugate())  # 3 - 4j（共轭）
print(abs(complex_num))      # 5.0（模）
```

### 3.4 布尔（bool）

继承自 `int`，表示 `True` 或 `False`。非空非零值为 `True`。

```py
bool_type = True
bool(0)              # False
bool("")             # False
bool([])             # False
bool(None)           # False
```

### 3.5 类型转换

将一种数字类型转换为另一种：

```python
int(3.14)         # 3（截断小数）
float(3)          # 3.0
complex("3+4j")   # 3 + 4j
```

## 4. 字符串

字符串是 Python 的**序列类型**，支持索引、切片、迭代等操作，且是**不可变**数据类型。掌握字符串操作能极大提升代码效率！ 😎

### 4.1 字符串基本操作

字符串可以用单引号、双引号或三引号定义，适用于不同场景。以下是常用操作示例：

```python
string = "hello"                # 单引号或双引号定义
long_string = """long
text"""                         # 三引号支持多行文本
# string[0] = 'H'              # 错误：字符串不可变
string = string.replace("h", "H")  # 替换生成新字符串
print(str(123))                 # '123'（类型转换）
print(string[3])                # 'l'（索引）
print(string[0:3])              # 'Hel'（切片）
print(string + " " + long_string)  # 字符串拼接
print(string * 3)               # 'HelHelHel'（重复）
print("e" in string)            # True（检查子字符串）
```

> 💡 **提示**: 字符串不可变，修改操作（如 `replace`）会生成新对象，需重新赋值。

### 4.2 字符串常用方法

Python 提供丰富的字符串方法，简化文本处理：

```python
text = "  Hello, World!  "
len(text)                   # 15（返回长度）
text.upper()                # '  HELLO, WORLD!  '（全大写）
text.lower()                # '  hello, world!  '（全小写）
text.title()                # '  Hello, World!  '（单词首字母大写）
text.capitalize()           # '  Hello, world!  '（首字母大写）
text.find("World")          # 8（子字符串首次出现位置）
text.rfind("o")             # 11（子字符串最后出现位置）
text.index("World")         # 8（类似 find，未找到抛 ValueError）
text.count("o")             # 3（统计子字符串出现次数）
text.strip()                # 'Hello, World!'（去除首尾空白）
text.lstrip()               # 'Hello, World!  '（去除左侧空白）
text.rstrip()               # '  Hello, World!'（去除右侧空白）
text.split(",")             # ['  Hello', ' World!  ']（按分隔符分割）
"-".join(["a", "b", "c"])  # 'a-b-c'（连接字符串）
text.replace("World", "Python")  # '  Hello, Python!  '（替换）
text.isalpha()              # False（是否全字母）
text.isdigit()              # False（是否全数字）
text.isalnum()              # False（是否字母或数字）
text.isspace()              # False（是否全空白）

# 正则表达式（需导入 re 模块）
import re
re.match(r"\w+", text)      # 从开头匹配单词
re.search(r"World", text)   # 查找第一个匹配
re.findall(r"o", text)      # ['o', 'o', 'o']（查找所有匹配）
re.sub(r"World", "Python", text)  # '  Hello, Python!  '（替换）
```

> 🚀 **效率提示**: 拼接大量字符串时，用 `join()` 而非 `+`，因为 `+` 每次创建新对象，效率较低。

### 4.3 转义字符与原始字符串

转义字符用于表示特殊字符，原始字符串（以 `r` 开头）按字面值处理，忽略转义：

| 转义字符 | 含义                   |
| -------- | ---------------------- |
| `\'`     | 单引号                 |
| `\"`     | 双引号                 |
| `\\`     | 反斜杠                 |
| `\n`     | 换行                   |
| `\t`     | 水平制表符（Tab）      |
| `\r`     | 回车                   |
| `\b`     | 退格（删除前一个字符） |
| `\f`     | 换页符                 |
| `\v`     | 垂直制表符             |
| `\0`     | 空字符（NULL）         |

```python
print("Line\nbreak")        # 输出: Line（换行）break
print(r"C:\new\test")       # 输出: C:\new\test（原始字符串）
```

### 4.4 字符串格式化

Python 提供多种字符串格式化方式，f-string 是现代首选。

#### 4.4.1 `%` 运算符（传统，Python 2 风格）

```python
name, age, score = "Alice", 25, 95.5
print("%s is %d years old and scored %.1f." % (name, age, score))
# 输出: Alice is 25 years old and scored 95.5.
```

> ⚠️ **注意**: `%` 运算符已过时，推荐使用 `str.format()` 或 f-string。

#### 4.4.2 `str.format()` 方法（Python 3.0+）

```python
name, age, score = "Alice", 25, 95.5
print("Hello, {}!".format(name))  # Hello, Alice!
print("{} is {} years old.".format(name, age))  # Alice is 25 years old.
print("{name} scored {score:.1f}.".format(name=name, score=score))
print("{:>10} is {:02d} years old.".format(name, age))  # '     Alice is 25 years old.'
```

> ℹ️ **提示**: `str.format()` 灵活但稍显冗长，Python 3.6+ 推荐 f-string。

#### 4.4.3 f-string（Python 3.6+，推荐）

```python
name, age, score = "Alice", 25, 95.5
print(f"Hello, {name}!")  # Hello, Alice!
print(f"{name} is {age} years old and scored {score:.1f}.")
print(f"Next year, {name} will be {age + 1}.")  # 计算表达式
print(f"{name:>10} scored {score:06.2f}.")  # 格式控制
```

> 🎯 **推荐**: f-string 语法简洁、性能优异，是现代 Python 的首选格式化方式。

## 5. 容器类型数据 📦

### 5.1 列表 ✨

#### 特性

- **有序**：元素按插入顺序排列，可通过索引访问。
- **可变**：支持修改、添加、删除元素。
- **可重复**：允许存储重复元素。
- **异构**：可包含不同类型元素（如整数、字符串、列表等）。

```python
# 创建列表
my_list = [1, "hello", 3.14, True, [2, 4, 6]]  # 异构列表
nested_list = [["hi!", 2], ["python", 3]]       # 嵌套列表
numbers = list((1, 2, 3, 4))                    # 从元组创建
chars = list("hello")                           # 从字符串创建: ['h', 'e', 'l', 'l', 'o']

# 列表推导式
squares = [x**2 for x in range(5)]             # 输出: [0, 1, 4, 9, 16]

# 索引与切片
print(my_list[0])                              # 访问: 1
print(my_list[1:4:2])                          # 切片: ["hello", True]

# 修改操作
my_list[1] = "oh!"                             # 修改元素
my_list += ["oh!", "python"]                   # 末尾添加
```

#### 常用方法

```py
my_list.append("hello")             # 末尾添加单个元素
my_list.extend(["hello","world"])   # 添加多个元素
my_list.insert(1,"hello")           # 指定索引添加元素
my_list.remove("hello")             # 删除匹配项
my_list.pop()                       # 删除并返回指定索引的元素（默认最后一个）
del my_list[1]                      # 删除索引或切片的元素
my_list.clear()                     # 清空列表
my_list.sort()                      # 对列表进行原地排序
my_list.index("h")                  # 返回列表元素的索引
my_list.count(5)                    # 返回列表元素值的出现次数
my_list.reverse()                   # 反转列表
```

#### 拷贝注意事项 ⚠️

```python
# 赋值拷贝影响原列表
a = [1, 2, 3]
b = a
b[0] = 2  # a 也会改变

# 正确做法
b = a.copy()          # 浅拷贝
b = list(a)           # 浅拷贝
b = a[::]             # 浅拷贝
import copy
b = copy.deepcopy(a)  # 深拷贝（适用于嵌套列表）
```

#### 注意事项

- 适合存储**有序数据**或需要频繁**添加/删除**的场景。
- 函数内修改列表会影响原列表。
- 避免在循环中修改列表，可能导致意外行为。
- 列表与元组的主要区别：**列表可变，元组不可变**。

#### 高级用法 🚀

```python
# 去重
lst = [1, 2, 2, 3, 3, 4]
unique_lst = list(set(lst))  # 输出: [1, 2, 3, 4]

# 使用 map() 和 filter()
numbers = [1, 2, 3, 4]
squares = list(map(lambda x: x**2, numbers))  # 输出: [1, 4, 9, 16]
evens = list(filter(lambda x: x % 2 == 0, numbers))  # 输出: [2, 4]
```

## 5.2 元组 🛠️

#### 特性

- **有序**：元素按插入顺序排列，可通过索引访问。
- **不可变**：创建后无法修改、添加或删除元素。
- **可重复**：允许存储重复元素。
- **异构**：可包含不同类型元素。

```python
# 创建元组
my_tuple = (1, "hello", 3.14, True, (2, 4, 6))  # 异构元组
nested_tuple = (1, (2, 3), 4)                   # 嵌套元组
numbers = 1, 2, 3                              # 自动解析: (1, 2, 3)
single_tuple = (42,)                            # 单元素元组需加逗号
tuple_from_list = tuple([1, 2, 3])             # 从列表创建
tuple_from_string = tuple("hello")             # 从字符串创建: ('h', 'e', 'l', 'l', 'o')

# 索引与切片
print(my_tuple[2])                             # 访问: 3.14
print(my_tuple[1:4])                           # 切片: ("hello", 3.14, True)

# 操作
print(my_tuple + numbers)                      # 拼接
print(my_tuple * 3)                            # 重复
a, b, c = numbers                              # 解包
first, *rest, last = my_tuple                  # 部分解包
```

> 元组是不可变的，因此可以作为字典的键，而列表不行。
> `locations = {(0, 0): "origin", (1, 1): "point A"}`

- 元组是不可变的，其方法非常少，仅支持查询操作

```python
print(my_tuple.count(1))                       # 统计元素出现次数
print(my_tuple.index("hello"))                 # 返回元素索引
```

- 元组常用于函数返回多个值，便于解包

```py
def get_min_max(numbers):
    return (min(numbers), max(numbers))

min_val, max_val = get_min_max([1, 2, 3, 4, 5])
print(min_val, max_val)  # 输出: 1 5
```

> 注意事项
> 元组本身不可变，但如果元组包含可变对象（如列表），这些对象的内部内容可以被修改
> 元组不支持直接与字符串拼接，需先转换为列表或使用字符串格式化
> 访问元组时需防止索引越界

- 高级用法

```py
# 为元组的每个元素指定名称，提高代码可读性
from collections import namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(10, 20)
print(p.x, p.y)  # 输出: 10 20
# 去重
unique = tuple(set(tup))
# 多重解包
nested = (1, (2, 3), 4)
a, (b, c), d = nested
print(a, b, c, d)  # 输出: 1 2 3 4
```

### 5.3 集合

#### 特性

- **无序**：元素无固定顺序，无法通过索引访问。
- **唯一性**：自动去除重复元素。
- **可变**：支持添加、删除元素，但元素必须是不可变的（如数字、字符串、元组）。
- **异构**：可包含不同类型的不可变元素。

```py
my_set = {1, "hello", 3.14}
empty_set = set()  # 空集合只能用 set() 创建，{} 创建的是空字典
numbers = set([1, 2, 2, 3])  # 从列表创建，去重后为 {1, 2, 3}
chars = set("hello")  # 从字符串创建，结果为 {'h', 'e', 'l', 'o'}
squares = {x**2 for x in range(5)}  # 结果为 {0, 1, 4, 9, 16}
"hello" in my_set  # 成员测试
my_set.add()      # 添加单个元素
my_set.update()   # 添加多个元素
my_set.remove()   # 删除指定元素抛出异常
my_set.discard()  # 删除指定元素报错
my_set.pop()      # 随机删除并返回一个元素
my_set.clear()    # 清空集合
```

- 集合运算

```py
# 并集（Union）：| 或 union()
set1 = {1, 2, 3}
set2 = {3, 4, 5}
print(set1 | set2)  # 输出: {1, 2, 3, 4, 5}
print(set1.union(set2))  # 同上
# 交集（Intersection）：& 或 intersection()
print(set1 & set2)  # 输出: {3}
print(set1.intersection(set2))  # 同上
# 差集（Difference）：- 或 difference()
print(set1 - set2)  # 输出: {1, 2}
print(set1.difference(set2))  # 同上
# 对称差集（Symmetric Difference）：^ 或 symmetric_difference()
print(set1 ^ set2)  # 输出: {1, 2, 4, 5}
print(set1.symmetric_difference(set2))  # 同上
# 子集与超集
# issubset() 或 <=：检查是否为子集。
# issuperset() 或 >=：检查是否为超集。
set3 = {1, 2}
print(set3.issubset(set1))  # 输出: True
print(set1.issuperset(set3))  # 输出: True
```

- 常用方法

| 方法                        | 描述                         |
| --------------------------- | ---------------------------- |
| `add(x)`                    | 添加元素 x                   |
| `update(iterable)`          | 添加可迭代对象中的元素       |
| `remove(x)`                 | 删除元素 x，不存在则抛出错误 |
| `discard(x)`                | 删除元素 x，不存在不报错     |
| `pop()`                     | 随机删除并返回一个元素       |
| `clear()`                   | 清空集合                     |
| `union(*sets)`              | 返回并集                     |
| `intersection(*sets)`       | 返回交集                     |
| `difference(*sets)`         | 返回差集                     |
| `symmetric_difference(set)` | 返回对称差集                 |
| `issubset(set)`             | 检查是否为子集               |
| `issuperset(set)`           | 检查是否为超集               |
| `isdisjoint(set)`           | 检查两个集合是否无交集       |

### 使用场景

- **去重**：快速去除列表中的重复元素。
- **成员测试**：高效检查元素是否存在（O(1) 时间复杂度）。
- **集合运算**：处理交集、并集等场景，如学生名单比较。
- **键值存储**：提取字典的键或使用 `frozenset` 作为字典键。

```py
# 去重
lst = [1, 2, 2, 3, 3, 4]
unique = set(lst)  # 输出: {1, 2, 3, 4}
# 成员测试
large_set = set(range(1000000))
print(999999 in large_set)  # 高效，O(1)
# 集合运算
students_math = {"Alice", "Bob", "Charlie"}
students_physics = {"Bob", "David", "Eve"}
common = students_math & students_physics  # 输出: {'Bob'}
# 过滤数据
numbers = {x for x in range(10) if x % 2 == 0}  # 输出: {0, 2, 4, 6, 8}
# 键值存储的键
keys = set({"a": 1, "b": 2}.keys())  # 输出: {'a', 'b'}
# 集合的不可变变体：frozenset
fs = frozenset([1, 2, 3])
# fs.add(4)  # 错误：frozenset 不可变
my_dict = {fs: "numbers"}  # 合法，因为 frozenset 是不可变的
print(my_dict)  # 输出: {frozenset({1, 2, 3}): 'numbers'}
```

- 注意事项

```py
# 无序性
s = {1, 2, 3}
print(list(s))  # 输出顺序可能为 [1, 2, 3] 或其他
# 元素不可变
# s = {1, [2, 3]}  # 错误：TypeError
s = {1, (2, 3)}  # 合法：元组是不可变的
# 空集合陷阱
empty_dict = {}  # 类型是 dict
empty_set = set()  # 类型是 set
# 遍历时修改集合可能导致 RuntimeError，建议复制集合或转为列表。
s = {1, 2, 3}
# for x in s: s.remove(x)  # 错误：修改集合
for x in list(s): s.discard(x)  # 正确
```

- 高级用法

```py
# 高效去重与交集
large_list = [1, 2, 2, 3, 3, 4] * 100000
unique = list(set(large_list))  # 快速去重
# 集合常用于操作字典的键。
d1 = {"a": 1, "b": 2}
d2 = {"b": 3, "c": 4}
common_keys = set(d1) & set(d2)  # 输出: {'b'}
```

### 5.4 字典

- 字典特性
  - 无序（插入顺序保持）：在 Python 3.7+中，字典保留插入顺序，但逻辑上仍视为无序（不能通过索引直接访问）。
  - 可变：字典支持添加、修改、删除键值对。
  - 键唯一：同一键只能出现一次，重复赋值会覆盖旧值。
  - 异构：键和值可以是不同类型。

```py
my_dict = {"name": "Alice", "age": 25, "is_student": True}
person = dict(name="Bob", age=30)  # 使用关键字参数
person = dict([("name", "Bob"), ("age", 30)])  # 从键值对列表创建
squares = {x: x**2 for x in range(5)}  # 输出: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
keys = ["name", "age"]
values = ["Alice", 25]
person = dict(zip(keys, values))  # 输出: {'name': 'Alice', 'age': 25}
my_dict["name"]     # 通过键访问对应的值，键不存在时抛出 KeyError
my_dict.get("name")  # 使用 get() 方法：安全访问，若键不存在返回默认值（默认 None）
person["age"] = 26         # 修改值
person["city"] = "Tokyo"   # 添加新键值对
del person["city"] # 删除指定键值对。
pop()：删除并返回指定键的值，若键不存在可指定默认值。
popitem()：删除并返回最后一个插入的键值对（Python 3.7+）。
clear()：清空字典。
```

- 遍历字典

```py
# 遍历键
person = {"name": "Alice", "age": 25, "city": "Tokyo"}
for key in person:
    print(key)  # 输出: name, age, city
for key in person.keys():
    print(key)  # 同上
# 遍历值
for value in person.values():
    print(value)  # 输出: Alice, 25, Tokyo
# 遍历键值对
for key, value in person.items():
    print(f"{key}: {value}")  # 输出: name: Alice, age: 25, city: Tokyo
```

- 字典复刻

```py
# 浅拷贝使用 copy() 或 dict()，仅复制顶层结构。
original = {"a": [1, 2], "b": 3}
copy_dict = original.copy()
copy_dict["a"][0] = 100  # 修改嵌套列表，影响原字典
print(original)  # 输出: {'a': [100, 2], 'b': 3}
# 深拷贝使用 copy.deepcopy()，复制整个
import copy
copy_dict = copy.deepcopy(original)
copy_dict["a"][0] = 200
print(original)  # 输出: {'a': [100, 2], 'b': 3}
```

- 常用方法

| 方法                         | 描述                            |
| ---------------------------- | ------------------------------- |
| `get(key[, default])`        | 返回键的值，不存在返回默认值    |
| `keys()`                     | 返回所有键的视图                |
| `values()`                   | 返回所有值的视图                |
| `items()`                    | 返回所有键值对的视图            |
| `pop(key[, default])`        | 删除并返回键的值                |
| `popitem()`                  | 删除并返回最后一个键值对        |
| `clear()`                    | 清空字典                        |
| `update(iterable)`           | 用键值对更新字典                |
| `setdefault(key[, default])` | 若键不存在，插入键和默认值      |
| `fromkeys(keys[, value])`    | 从键列表创建字典，值默认为 None |

使用场景

- 存储和查询键值对，如用户信息、配置项。
- 使用字典统计元素出现次数

```py
words = ["apple", "banana", "apple", "orange"]
counts = {}
for word in words:
    counts[word] = counts.get(word, 0) + 1
print(counts)  # 输出: {'apple': 2, 'banana': 1, 'orange': 1}
```

- 根据键分组数据

```py
students = [("Alice", "A"), ("Bob", "B"), ("Charlie", "A")]
grouped = {}
for name, grade in students:
    grouped.setdefault(grade, []).append(name)
print(grouped)  # 输出: {'A': ['Alice', 'Charlie'], 'B': ['Bob']}
```

- 缓存在递归或复杂计算中存储中间结果

```py
cache = {}
def fibonacci(n):
    if n in cache:
        return cache[n]
    if n <= 1:
        return n
    cache[n] = fibonacci(n-1) + fibonacci(n-2)
    return cache[n]
print(fibonacci(10))  # 输出: 55
```

- 字典与 JSON 格式高度兼容，常用于处理 API 数据

```py
import json
data = json.loads('{"name": "Alice", "age": 25}')
print(data["name"])  # 输出: Alice
```

- 字典的视图对象视图对象节省内存，适合动态跟踪字典变化

```py
person = {"name": "Alice", "age": 25}
keys = person.keys()
print(keys)  # 输出: dict_keys(['name', 'age'])
person["city"] = "Tokyo"
print(keys)  # 输出: dict_keys(['name', 'age', 'city'])
```

- 注意事项

```py
# 键的不可变性
# d = {[1, 2]: "value"}  # 错误：TypeError
d = {(1, 2): "value"}  # 合法：元组作为键
# 历时修改字典可能导致 RuntimeError，建议遍历视图的副本。
for key in list(person.keys()):  # 安全
    del person[key]
```

- 高级用法

```py
# 嵌套字典
users = {
    "Alice": {"age": 25, "city": "Tokyo"},
    "Bob": {"age": 30, "city": "Osaka"}
}
print(users["Alice"]["city"])  # 输出: Tokyo
# 默认字典
from collections import defaultdict
dd = defaultdict(int)
dd["count"] += 1  # 自动初始化为 0
print(dd)  # 输出: defaultdict(<class 'int'>, {'count': 1})
```