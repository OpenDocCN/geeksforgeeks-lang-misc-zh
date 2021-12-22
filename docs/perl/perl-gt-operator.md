# Perl | gt 运算符

> 原文:[https://www.geeksforgeeks.org/perl-gt-operator/](https://www.geeksforgeeks.org/perl-gt-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 **gt** 运算符是用于检查两个字符串是否相等的字符串比较运算符之一。它用于检查其左边的字符串是否大于其右边的字符串。

> **语法:** String1 **lt** String2
> 
> **如果左参数大于右参数，则返回:** 1

**例 1:**

```
#!/usr/local/bin/perl

# Initializing Strings
$a = "Welcome";
$b = "Geeks";

# Comparing the strings using gt operator
$c = $a gt $b;

if($c == 1)
{
    print"String1 is greater than String2";
}
else
{
    print"String1 is not greater than String2";
}
```

**Output:**

```
String1 is greater than String2

```

**例 2:**

```
#!/usr/local/bin/perl

# Initializing Strings
$a = "Geeks";
$b = "GeeksWelcome";

# Comparing the strings using gt operator
$c = $a gt $b;

if($c == 1)
{
    print"String1 is greater than String2";
}
else
{
    print"String1 is not greater than String2";
}
```

**Output:**

```
String1 is not greater than String2

```