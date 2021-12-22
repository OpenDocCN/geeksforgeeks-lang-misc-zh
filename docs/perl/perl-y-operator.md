# Perl | y 运算符

> 原文:[https://www.geeksforgeeks.org/perl-y-operator/](https://www.geeksforgeeks.org/perl-y-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 **y** 运算符将搜索列表的所有字符转换为替换列表的相应字符。
这里的搜索列表是给定的输入字符，这些字符将被转换成替换列表中给出的相应字符。

> **语法:**y/search list/replacement list/
> 
> **返回:**翻译后的字符串

**示例 1:** 本示例使用 y 运算符从小写转换为大写。

```perl
#!/usr/bin/perl

# Initialising some strings
$string1 = 'gfg is a computer science portal';
$string2 = 'geeksforgeeks';

# Calling to y function
$string1 =~ y/a-z/A-Z/;
$string2 =~ y/a-z/A-Z/;

# Getting translated strings
print "$string1\n";
print "$string2\n";
```

 **输出:**

```perl
GFG IS A COMPUTER SCIENCE PORTAL
GEEKSFORGEEKS

```

**示例 2:** 本示例使用 y 运算符从大写转换为小写。

```perl
#!/usr/bin/perl

# Initialising some strings
$string1 = 'GFG IS A COMPUTER SCIENCE PORTAL';
$string2 = 'GEEKSFORGEEKS';

# Calling to y function
$string1 =~ y/A-Z/a-z/;
$string2 =~ y/A-Z/a-z/;

# Getting translated strings
print "$string1\n";
print "$string2\n";
```

**输出:**

```perl
gfg is a computer science portal
geeksforgeeks
```

**注意:**这个 y 运算符执行 [lc()函数](https://www.geeksforgeeks.org/perl-lc-function-for-lower-case-conversion/)和 [uc()函数](https://www.geeksforgeeks.org/perl-uc-function/)的任务，以及将输入字符翻译成数字形式等。

**示例 3:** 本示例使用 y 运算符将大写转换为数字形式。

```perl
#!/usr/bin/perl

# Initialising some strings
$string1 = 'GFG IS A COMPUTER SCIENCE PORTAL';
$string2 = 'GEEKSFORGEEKS';

# Calling to y function
$string1 =~ y/A-Z/0-9/;
$string2 =~ y/A-Z/0-9/;

# Getting translated strings
print "$string1\n";
print "$string2\n";
```

**输出:**

```perl
656 89 0 29999949 9284924 999909
6449959964499

```