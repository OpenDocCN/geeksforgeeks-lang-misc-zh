# Perl | reverse()函数

> 原文:[https://www.geeksforgeeks.org/perl-reverse-function/](https://www.geeksforgeeks.org/perl-reverse-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 reverse()函数在列表上下文中使用时，会更改列表中元素的顺序，并以相反的顺序返回列表。在标量上下文中，返回列表值的串联字符串，字符串的每个字符的顺序相反。

> **语法:**反向列表
> 
> **返回:**
> 标量上下文中的字符串和列表上下文中的列表。

**示例 1:** **列表上下文中:**

```
#!/usr/bin/perl -w

# Defining list of +ve Integers to the array
@array1 = (20, 30, 40, 50, 60, 70);
print reverse(@array1), "\n";

# Defining list of Integers to the array
@array2 = (1, -2, 3, 4, -5, 6);
print reverse(@array2), "\n";
```

**输出:**

```
706050403020
6-543-21
```

**示例 2:** **在标量上下文中:**

```
#!/usr/bin/perl -w

# Defining string to be reversed
$string = "Hello World";
print scalar reverse("$string"), "\n";

$string = "Geeks For Geeks";
print scalar reverse("$string"), "\n";
```

**输出:**

```
dlroW olleH
skeeG roF skeeG
```