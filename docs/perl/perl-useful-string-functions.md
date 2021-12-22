# Perl |有用的字符串函数

> 原文:[https://www.geeksforgeeks.org/perl-useful-string-functions/](https://www.geeksforgeeks.org/perl-useful-string-functions/)

Perl 中的一个[字符串](https://www.geeksforgeeks.org/perl-quoted-interpolated-and-escaped-strings/)是一个标量变量，以($)符号开始，它可以包含字母、数字和特殊字符。字符串可以由一个单词、一组单词或多行段落组成。字符串由用户在单引号(')或双引号(")中定义。

Perl 像任何其他编程语言一样，提供各种函数来操作字符串。
**例:**

```perl
# Perl program to demonstrate  
# string length function 

# string 
my $s = "geeksforgeeks"; 

# using length function & 
# displaying length 
print("Length: ", length($s));  

# Converting to Uppercase
print("\nTo Upper Case: "); 
print(uc($s), "\n"); 
```

**Output:**

```perl
Length: 13
To Upper Case: GEEKSFORGEEKS

```

Perl 的一些字符串函数如下:

| 功能 | 描述 |
|  | 用于从输入字符串中删除最后一个尾随换行符 |
| **[长度()](https://www.geeksforgeeks.org/perl-length-function/)** | 查找给定字符串的长度(字符数)，如果未指定，则查找$_ 长度 |
| **基底()T3** | 从传递给函数的字符串中返回子字符串，从给定的索引开始，直到指定的长度 |
| **[【UC()](https://www.geeksforgeeks.org/perl-uc-function/)** | 将字符串转换为大写后，返回传递给它的字符串 |
| **ucfirst()** | 将第一个字符转换为大写后，返回字符串 VAR 或$_。 |
| **[【LC()](https://www.geeksforgeeks.org/perl-lc-function-for-lower-case-conversion/)** | 返回风险值的较低版本，如果忽略风险值，则返回$_ 版本 |
| **[【lcfirst()](https://www.geeksforgeeks.org/perl-lcfirst-function/)** | 将第一个字符转换为小写后，返回字符串 VAR 或$_。 |
| **[chr()](https://www.geeksforgeeks.org/perl-chr-function/)** | 返回一个字符串，该字符串表示 Unicode 代码点为整数的字符 |
| **[斩()](https://www.geeksforgeeks.org/perl-chop-function/)** | 返回一个字符串，该字符串表示 Unicode 代码点为整数的字符 |
| **[指数()](https://www.geeksforgeeks.org/perl-index-function/)** | 返回给定子字符串(或模式)在字符串(或文本)中第一次出现的位置 |
| **[【rinex()](https://www.geeksforgeeks.org/perl-rindex-function/)** | 返回子字符串(或模式)在字符串(或文本)中最后一次出现的位置 |
| **[【sprint()](https://www.geeksforgeeks.org/perl-sprintf-function/)** | 使用用户提供的格式，使用列表中的值返回格式化的字符串 |
| **[【ord()](https://www.geeksforgeeks.org/perl-ord-function/)** | 返回字符串第一个字符的 ASCII 值 |
|  | 它转义作为参数传递给它的值中的所有元字符 |
| **[【分裂()](https://www.geeksforgeeks.org/perl-split-function/)** | 用于将绳子分割或切割成更小的部分或碎片 |