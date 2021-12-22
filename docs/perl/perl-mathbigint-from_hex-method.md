# Perl | Math::BigInt->from _ hex()方法

> 原文:[https://www . geesforgeks . org/perl-mathbigint-from _ hex-method/](https://www.geeksforgeeks.org/perl-mathbigint-from_hex-method/)

**Math::Perl 中的 BigInt** 模块提供了用任意精度和重载算术运算符表示整数的对象。
**from_hex()** 方法的 **Math::BigInt** 模块用于将作为输入传递的十六进制数转换为其对应的十进制数。

> **语法:**数学::BigInt- > from_hex()
> **参数:**输入要转换的十六进制数
> **返回:**传递的十六进制数对应的十进制数

**例 1:**

## 实际抽取与汇报语言

```perl
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Converting from hexadecimal to decimal
$x = Math::BigInt->from_hex("3E8");
print("$x\n");

# Converting from hexadecimal to decimal
$x = Math::BigInt->from_hex("D75A");
print("$x\n");
```

**Output:** 

```perl
1000
55130
```

**例 2:**

## 实际抽取与汇报语言

```perl
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Converting from hexadecimal to decimal
$x = Math::BigInt->from_hex("-3E8");
print("$x\n");

# Converting from hexadecimal to decimal
$x = Math::BigInt->from_hex("-D75A");
print("$x\n");
```

**Output:** 

```perl
-1000
-55130
```