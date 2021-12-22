# Perl |有用的字符串运算符

> 原文:[https://www.geeksforgeeks.org/perl-useful-string-operators/](https://www.geeksforgeeks.org/perl-useful-string-operators/)

Perl 中的一个[字符串](https://www.geeksforgeeks.org/perl-quoted-interpolated-and-escaped-strings/)是一个标量变量，以($)符号开始，它可以包含字母、数字和特殊字符。字符串可以由一个单词、一组单词或多行段落组成。字符串由用户在单引号(')或双引号(")中定义。
运算符是任何编程语言的基础，在 Perl 中也是如此。用户可以将字符串中的[运算符](https://www.geeksforgeeks.org/perl-string-operators/)定义为有助于对操作数执行特定数学和逻辑计算的符号。这些操作类似于连接、比较、替换等。
**例:**

## Perl 语言

```perl
# Perl program to demonstrate the
# Concatenation Operator(.) in String

#!/usr/bin/perl

# Input first string 
$first_string = "Geeks";

# Input second string 
$second_string = "forGeeks";

# Implement Concatenation operator(.) 
$concat_string = $first_string.$second_string;

# displaying concatenation string result
print "String After Concatenation = $concat_string\n";
```

**Output:** 

```perl
String After Concatenation = GeeksforGeeks
```

Perl 中字符串操作的一些有用操作符如下所示:

<figure class="table">

| 操作员 | 描述 |
| [**qw**](https://www.geeksforgeeks.org/perl-qw-operator/) | quote word '运算符用于提取给定字符串的每个元素，因为它在单引号(')中的元素数组中 |
| [**q**](https://www.geeksforgeeks.org/perl-q-operator/) | 用于代替单引号。它使用一组圆括号将字符串括起来 |
| [**qq**](https://www.geeksforgeeks.org/perl-qq-operator/) | 用于代替双引号。它使用一组圆括号将字符串括起来 |
| [**y**](https://www.geeksforgeeks.org/perl-y-operator/) | 将搜索列表的所有字符转换为替换列表的相应字符 |
| [**【tr】**](https://www.geeksforgeeks.org/perl-tr-operator/) | 类似于“y”运算符，它将搜索列表的所有字符转换为替换列表的相应字符 |
| [**eq**](https://www.geeksforgeeks.org/perl-eq-operator/) | 用于检查左边的字符串是否等于右边的字符串 |
| [**【ne】**](https://www.geeksforgeeks.org/perl-ne-operator/) | 用于检查左边的字符串是否与右边的字符串不相等 |
| [T1】leT3】](https://www.geeksforgeeks.org/perl-le-operator/) | 用于检查左边的字符串是否小于或等于右边的字符串 |
| [T1】geT3】](https://www.geeksforgeeks.org/perl-ge-operator/) | 用于检查左边的字符串是否大于或等于右边的字符串 |
| [**lt**](https://www.geeksforgeeks.org/perl-lt-operator/) | 用于检查其左侧的字符串是否小于其右侧的字符串 |
| [**gt**](https://www.geeksforgeeks.org/perl-gt-operator/) | 用于检查左边的字符串是否大于右边的字符串 |
| [**【CMP】**](https://www.geeksforgeeks.org/perl-cmp-operator/) | 用于比较放在此运算符左右的两个字符串是否相等或小于另一个字符串 |
| [**换人符**](https://www.geeksforgeeks.org/perl-substitution-operator/) | 用于用用户指定的模式替换字符串的文本 |
| [**匹配算子(m)**](https://www.geeksforgeeks.org/perl-matching-operator/) | 用于匹配给定文本中的模式 |

</figure>