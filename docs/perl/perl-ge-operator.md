# Perl | ge 运算符

> 原文:[https://www.geeksforgeeks.org/perl-ge-operator/](https://www.geeksforgeeks.org/perl-ge-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 **ge** 运算符是用于检查两个字符串是否相等的字符串比较运算符之一。它用于检查其左侧的字符串是否大于或等于其右侧的字符串。

> **语法:**string 1**ge**string 2
> 
> **如果左参数大于或等于右参数**

，则返回: 1

**例 1:** String1 大于 String2

```
#!/usr/local/bin/perl

# Initializing Strings
$a = "Welcome";
$b = "Geeks";

# Comparing the strings using ge operator
$c = $a ge $b;

if($c == 1)
{
    print"String1 is greater than or equal to String2";
}
else
{
    print"String1 is not greater than or equal to String2";
}
```

**输出:**

```
String1 is greater than or equal to String2

```