# Perl | sprintf()函数

> 原文:[https://www.geeksforgeeks.org/perl-sprintf-function/](https://www.geeksforgeeks.org/perl-sprintf-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 sprintf()函数使用用户提供的 Format，使用列表中的值返回格式化的字符串。这个函数与 printf 相同，但是它返回格式化的字符串而不是打印它。

> **语法:** sprintf 格式，列表
> 
> **返回:**一个格式化的标量字符串

**例 1:**

```
#!/usr/bin/perl -w

# Formatting the string using sprintf
$text1 = sprintf("%8s", 'Geeks');
$text2 = sprintf("%-8s", 'Geeks');

# Printing the formatted string
print "$text1\n$text2";
```

**Output:**

```
        Geeks
Geeks        

```

 **例 2:**

```
#!/usr/bin/perl -w

# Formatting the string using sprintf
$text1 = sprintf("%03d", '7');
$text2 = sprintf("%03d", '123');
$text3 = sprintf("%04d", '123');

# Printing the formatted string
print "$text1\n$text2\n$text3";
```

**Output:**

```
007
123
0123

```