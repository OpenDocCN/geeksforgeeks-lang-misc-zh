# Perl | Math::BigInt- > brsft()方法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-brsft-method/](https://www.geeksforgeeks.org/perl-mathbigint-brsft-method/)

**Math::Perl 中的 BigInt** 模块提供了用任意精度和重载算术运算符表示整数的对象。
**【brsft()】**方法的**数学::BigInt** 模块用于将给定值右移一个给定为参数的基数。

> **语法:**数学::BigInt- > brsft()
> **参数:**
> $y-要进行移位的次数
> $n-移位的基数
> **返回:**将基数除以给定次数得到的结果

**注意:**默认以 2 为基数。
**例 1:**

## 实际抽取与汇报语言

```
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Right shifting one time with base 2
$x = Math::BigInt->new(25);
$x->brsft(1);  # same as $x >> 1
print("$x\n");

# Right shifting 2 times with base 10
$x = Math::BigInt->new(2345);
$x->brsft(2, 10);       
print($x);
```

**Output:** 

```
12
23
```

负值有一个例外，即只有基数为 2，输出将是实际输出和原始数字之间的差异。以下示例将说明:
**示例 2:**

## 实际抽取与汇报语言

```
#!/usr/bin/perl

# Import Math::BigInt module
use Math::BigInt;

# Right shifting one time with base 2
$x = Math::BigInt->new(31);
$x->brsft(1);  # same as $x >> 1
print("$x\n");

# Right shifting the negative value
$x = Math::BigInt->new(-31);
$x->brsft(1);       
print($x);
```

**Output:** 

```
15
-16
```