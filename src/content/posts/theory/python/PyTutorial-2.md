---
title: Python Tutorial 2 ⚡
published: 2024-09-18
description: "Python Tutorial"
image: "../cover/dark-4.jpg"
tags: ["Python", "Language"]
category: Language
draft: false
---

## 1. 程序流程控制

### 1.1 分支语句

```py
if condition:
    statement
else:
    statement
```

```py
if condition:
    statement
elif condition:
    statement
else:
    statement
```

```py
match subject:
    case pattern1 [if guard]:
        # Code block executed if pattern1 matches and guard (if present) is True
        statement1
    case pattern2 [if guard]:
        # Code block executed if pattern2 matches
        statement2
    case _:  # Optional wildcard (default case)
        # Code block executed if no other patterns match
        statement3
```

> 性能优化
> - 将最可能成立的条件放在前面，减少不必要的检查
> - 如果条件中涉及复杂计算，可以提前计算结果并存储

### 1.2 循环语句

- for 循环

```
for variable in iterable:
    # Code block to execute
```

```
for variable in range(10):
    # Code block to execute
```

- while 循环

```

```

### 1.3 跳转语句

## 2. 函数

## 3. 模块

## 4. 输入与输出

## 5. 错误与异常

## 6.类

## 7.标准库

## 8.虚拟环境与包
