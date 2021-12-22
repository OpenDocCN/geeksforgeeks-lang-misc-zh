# Perl | Math::BigInt->from _ bin()方法

> 原文:[https://www . geesforgeks . org/perl-mathbigint-from _ bin-method/](https://www.geeksforgeeks.org/perl-mathbigint-from_bin-method/)

**Math::Perl 中的 BigInt** 模块提供了用任意精度和重载算术运算符表示整数的对象。
**from_bin()** 方法的 **Math::BigInt** 模块用于将作为输入传递的二进制数转换为其对应的十进制数。

> **语法:**数学::BigInt- > from_bin()
> **参数:**输入要转换的二进制数
> **返回:**传递的二进制数对应的十进制数

**例 1:**

## 实际抽取与汇报语言

```perl
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Converting from binary to decimal
$x = Math::BigInt->from_bin("110100");
print("$x\n");

# Converting from binary to decimal
$x = Math::BigInt->from_bin("0b11001000");
print("$x\n");
```

**Output:** 

```perl
52
200
```

**例 2:**

## 实际抽取与汇报语言

```perl
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Converting from binary to decimal
$x = Math::BigInt->from_bin("-110100");
print("$x\n");

# Converting from binary to decimal
$x = Math::BigInt->from_bin("-0b11001000");
print("$x\n");
```

**Output:** 

```perl
-52
-200
```