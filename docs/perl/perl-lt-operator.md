# Perl | lt 运算符

> 原文:[https://www.geeksforgeeks.org/perl-lt-operator/](https://www.geeksforgeeks.org/perl-lt-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 **lt** 运算符是用于检查两个字符串是否相等的字符串比较运算符之一。它用于检查它左边的字符串是否比它右边的字符串短。

> **语法:** String1 **lt** String2
> 
> **如果左参数小于右参数，则返回:** 1

**例 1:**

```perl
#!/usr/local/bin/perl

# Initializing Strings
$a = "Geeks";
$b = "Welcome";

# Comparing the strings using lt operator
$c = $a lt $b;

if($c == 1)
{
    print"String1 is less than String2";
}
else
{
    print"String1 is not less than String2";
}
```

**Output:**

```perl
String1 is less than String2

```

**例 2:**

```perl
#!/usr/local/bin/perl

# Initializing Strings
$a = "GeeksWelcome";
$b = "Geeks";

# Comparing the strings using lt operator
$c = $a lt $b;

if($c == 1)
{
    print"String1 is less than String2";
}
else
{
    print"String1 is not less than String2";
}
```

**Output:**

```perl
String1 is not less than String2

```