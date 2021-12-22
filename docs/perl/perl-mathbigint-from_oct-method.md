# Perl | Math::BigInt->from _ oct()方法

> 原文:[https://www . geesforgeks . org/perl-mathbigint-from _ oct-method/](https://www.geeksforgeeks.org/perl-mathbigint-from_oct-method/)

**Math::Perl 中的 BigInt** 模块提供了用任意精度和重载算术运算符表示整数的对象。
**from_oct()** 方法的 **Math::BigInt** 模块用于将作为输入传递的八进制数转换为其对应的十进制数。

> **语法:**数学:BigInt- > from_oct()
> **参数:**输入要转换的八进制数
> **返回:**传递的八进制数对应的十进制数

**例 1:**

## 实际抽取与汇报语言

```perl
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Converting from octal to decimal
$x = Math::BigInt->from_oct("0345");
print("$x\n");

# Converting from octal to decimal
$x = Math::BigInt->from_oct("_443");
print("$x\n");
```

**Output:** 

```perl
229
291
```

**例 2:**

## 实际抽取与汇报语言

```perl
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Converting negative number
# from octal to decimal
$x = Math::BigInt->from_oct("-0345");
print("$x\n");

# Converting negative number
# from octal to decimal
$x = Math::BigInt->from_oct("-_443");
print("$x\n");
```

**Output:** 

```perl
-229
-291
```