# Perl | tr 运算符

> 原文:[https://www.geeksforgeeks.org/perl-tr-operator/](https://www.geeksforgeeks.org/perl-tr-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 tr 运算符将 SearchList 的所有字符翻译成 ReplacementList 的相应字符。
这里的搜索列表是给定的输入字符，这些字符将被转换成替换列表中给出的相应字符。

> **语法:**tr/search list/replacement list/
> 
> **返回:**翻译后的字符串

**示例 1:** 本示例使用 tr 运算符从小写转换为大写。

```perl
#!/usr/bin/perl

# Initializing the strings
$string1 = 'gfg is a computer science portal';
$string2 = 'geeksforgeeks';

# Calling tr function
$string1 =~ tr/a-z/A-Z/;
$string2 =~ tr/a-z/A/;

# Printing the translated strings
print "$string1\n";
print "$string2\n";
```

 **输出:**

```perl
GFG IS A COMPUTER SCIENCE PORTAL
AAAAAAAAAAAAA

```

**示例 2:** 本示例使用 tr 运算符从大写转换为小写。

```perl
#!/usr/bin/perl

# Initializing the strings
$string1 = 'GFG IS A COMPUTER SCIENCE PORTAL';
$string2 = 'GEEKSFORGEEKS';

# Calling tr function
$string1 =~ tr/A-Z/a-z/;
$string2 =~ tr/A-Z/p/;

# Printing translated strings
print "$string1\n";
print "$string2\n";
```

**输出:**

```perl
gfg is a computer science portal
ppppppppppppp
```

**示例 3:** 本示例使用 tr 运算符将大写转换为数字形式。

```perl
#!/usr/bin/perl

# Initializing the strings
$string1 = 'GFG IS A COMPUTER SCIENCE PORTAL';
$string2 = 'GEEKSFORGEEKS';

# Calling tr function
$string1 =~ tr/A-Z/0-9/;
$string2 =~ tr/A-Z/5/;

# Printing translated strings
print "$string1\n";
print "$string2\n";
```

**输出:**

```perl
656 89 0 29999949 9284924 999909
5555555555555

```

**使用‘s’运算符:**
在‘tr’运算符的末尾使用‘s’运算符来检测给定字符串中的重复字符，并用指定的字符替换它们。

**示例:**

```perl
#!/usr/bin/perl

# Initializing the strings
$string1 = 'geeksforgeeks';
$string2 = 'geeksforgeeks';

# Calling tr function
# without appending 's' to 'tr' operator
$string1 =~ tr/ee/e/;

# Appending 's' to 'tr' operator
$string2 =~ tr/ee/e/s;

# Printing translated strings
print "$string1\n";
print "$string2\n";
```

**输出:**

```perl
geeksforgeeks
geksforgeks

```

在上面的代码中，可以看到，当“s”被附加到“tr”运算符的末尾时，它会用单个“e”替换重复的“e”，即“ee”。

**使用“c”运算符:**
在“tr”运算符的末尾使用“c”运算符来检测给定字符串中的空格(“”)字符，并将其替换为指定的字符。

**示例:**

```perl
#!/usr/bin/perl

# Initializing the strings
$string1 = 'gfg is a computer science portal';
$string2 = 'gfg is a computer science portal';

# Calling tr function
# without appending 'c' to 'tr' operator
$string1 =~ tr/a-z/_/;

# Appending 'c' to 'tr' operator
$string2 =~ tr/a-z/_/c;

# Printing translated strings
print "$string1\n";
print "$string2\n";
```

**输出:**

```perl
___ __ _ ________ _______ ______
gfg_is_a_computer_science_portal

```

在上面的代码中，可以看到在每个单词之间使用了下划线(“_”)，这是通过附加“c”来完成的。

> **注 1:** 该 tr 运算符执行 [lc()函数](https://www.geeksforgeeks.org/perl-lc-function-for-lower-case-conversion/)和 [uc()函数](https://www.geeksforgeeks.org/perl-uc-function/)的任务，并将输入字符翻译成数字形式等。
> 
> **注 2:** 此 tr 运算符与 y 运算符略有不同，因为 y 运算符不使用运算符后加“c”或“s”，但 tr 运算符使用。