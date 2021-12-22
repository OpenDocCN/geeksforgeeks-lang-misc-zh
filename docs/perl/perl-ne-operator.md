# Perl | ne 运算符

> 原文:[https://www.geeksforgeeks.org/perl-ne-operator/](https://www.geeksforgeeks.org/perl-ne-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 **ne** 运算符是用于检查两个字符串是否相等的字符串比较运算符之一。它用于检查左边的字符串是否与右边的字符串不相等。

> **语法:** String1 **ne** String2
> 
> **如果左参数不等于右参数，则返回:** 1

**例 1:**

```
#!/usr/local/bin/perl

# Initializing Strings
$a = "Welcome";
$b = "Geeks";

# Comparing the strings using ne operator
$c = $a ne $b;

if($c == 1)
{
    print"String1 is not equal to String2";
}
else
{
    print"String1 is equal to String2";
}
```

**Output:**

```
String1 is not equal to String2

```

**例 2:**

```
#!/usr/local/bin/perl

# Initializing Strings
$a = "Geeks";
$b = "Geeks";

# Comparing the strings using ne operator
$c = $a ne $b;

if($c == 1)
{
    print"String1 is not equal to String2";
}
else
{
    print"String1 is equal to String2";
}
```

**Output:**

```
String1 is equal to String2

```