# Perl | int()函数

> 原文:[https://www.geeksforgeeks.org/perl-int-function/](https://www.geeksforgeeks.org/perl-int-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 int()函数返回给定值的整数部分。如果未提供任何值，它将返回$_。请注意，$_ 是默认输入，在这种情况下为 0。int()函数不进行舍入。为了将一个值舍入为整数，使用了 sprintf。

> **语法:t1(var)**
> 
> **参数:**
> **VAR:** 要转换成整数的值
> 
> **返回:**返回 VAR 的整数部分

**例 1:**

```perl
#!/usr/bin/perl

# Passing positive decimal value
$int_val = int(19.8547);
print"Integer value is $int_val\n";

# Passing negative decimal value
$int_val = int(-18.659);
print"Integer value is $int_val\n";
```

**输出:**

```perl
Integer value is 19
Integer value is -18

```

**例 2:**

```perl
#!/usr/bin/perl

# Passing fractional positive value
$int_val = int(17 / 4);
print"Integer value is $int_val\n";

# Passing fractional negative value
$int_val = int(-17 / 4);
print"Integer value is $int_val\n";
```

**输出:**

```perl
Integer value is 4
Integer value is -4
```