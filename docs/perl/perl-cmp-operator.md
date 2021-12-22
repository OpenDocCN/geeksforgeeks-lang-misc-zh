# Perl | cmp 运算符

> 原文:[https://www.geeksforgeeks.org/perl-cmp-operator/](https://www.geeksforgeeks.org/perl-cmp-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 cmp 运算符是一个字符串相等比较运算符，用于比较放在此运算符左右的两个字符串是否相等或小于另一个字符串。

> **语法:**string1 CMP string2
> 
> **返回:** -1 表示 string 1 小于，0 表示等于，1 表示大于 string 2。

**例 1:** 当 String1 小于 String2 时

```perl
#!/usr/local/bin/perl

# Initializing strings
$a = "Geeks";
$b = "Welcome";

# Comparing strings
$c = $a cmp $b;

# Printing the comparison result
print("Comparison of \$a and \$b returns $c");
```

**输出:**

```perl
Comparison of $a and $b returns -1

```