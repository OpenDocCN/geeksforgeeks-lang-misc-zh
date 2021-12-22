# 正则表达式中的 Perl |运算符

> 原文:[https://www . geesforgeks . org/perl-正则表达式中的运算符/](https://www.geeksforgeeks.org/perl-operators-in-regular-expression/)

**先决条件:** [Perl |正则表达式](https://www.geeksforgeeks.org/perl-regular-expressions/)

**正则表达式**是一个字符串，它是提供文本字符串匹配的不同字符的组合。正则表达式也可以称为正则表达式或正则表达式。
应用正则表达式的基本方法是使用绑定运算符=~ (Regex 运算符)和！~(否定正则表达式运算符)。

**Perl 中有三种类型的正则表达式运算符:**

1.  匹配正则表达式
2.  替换(搜索和替换)正则表达式
3.  全局字符音译正则表达式

**1)模式匹配或匹配正则表达式:**匹配运算符“m//”用于将字符串或语句与正则表达式进行匹配。运算符中使用的正斜杠(m//)充当分隔符，该分隔符也可以像 m{}、m()、m > <等。表达式写在运算符中使用的两个正斜杠之间。

> **语法:** m/PATTERN/

这里，PATTERN 是字符串中要搜索的正则表达式
**我们来看一些说明模式匹配的例子:**
在下面的例子中，一个字符串和正则表达式匹配，成功后它返回“match found”，否则返回“match not found”。
**例 1:**

```
#!/usr/bin/perl

# Initializing a string
$a = "GeeksforGeeks"; 

# matching the string and 
# a regular expression and returns
# match found or not
if ($a =~ m/for/)  
{ 
    print "Match Found\n"; 
} 
else 
{ 
    print "Match Not Found\n"; 
} 
```

**输出:**

```
Match Found
```

**例 2:**

```
#!/usr/bin/perl

# Initialising an string
$a = "GeeksforGeeks"; 

# matching the string and 
# a regular expression and returns
# match found or not
if ($a =~ m:abc:) 
{ 
    print "Match Found\n"; 
} 
else
{ 
    print "Match Not Found\n"; 
} 
```

**输出:**

```
Match Not Found

```

这里，在上面的代码中，使用了不同的分隔符“:”代替“/”，这表明没有必要使用“/”作为分隔符。

**2)替代(搜索和替换)正则表达式:**替代运算符“s///”用于搜索特定单词，然后用给定的正则表达式替换它。运算符(s//)中使用的正斜杠充当分隔符。

> **语法:**s/PATTERN/REPLACEMENT/；

这里的 PATTERN 是要用 REPLACEMENT 正则表达式替换的正则表达式。

**我们来看一些举例说明替代正则表达式:**
在下面的例子中，首先搜索一个 PATTERN 单词，然后用 REPLACEMENT 单词替换它。
**示例-1:**

```
#/user/bin/perl

# Initialising a string
$string = "GeeksforGeeks is a computer science portal.";

# Calling the substitute regular expression
$string =~ s/GeeksforGeeks/gfg/;
$string =~ s/computer science/cs/;

# Printing the substituted string
print "$string\n";
```

**输出:**

```
gfg is a cs portal.

```

**示例-2:**

```
#/user/bin/perl

# Initialising a string
$string = "10001";

# Calling the substitution regular expression
$string =~ s/000/999/;

# Printing the substituted string
print "$string\n";
```

**输出:**

```
19991

```

**3)全局字符音译正则表达式:**翻译或音译运算符“[tr//](https://www.geeksforgeeks.org/perl-tr-operator/)或“[y//](https://www.geeksforgeeks.org/perl-y-operator/)”用于用给定的单个字符替换字符的所有出现。运算符(tr///和 y///)中使用的正斜杠充当分隔符。

> **语法:**
> tr/SEARCHLIST/REPLACEMENTLIST/
> y/SEARCHLIST/REPLACEMENTLIST/

这里的搜索列表是一个字符，它的所有出现都将被替换列表中的字符替换。

**我们来看一些说明翻译正则表达式的例子:**
在下面的例子中，所有出现的“G”都被“G”替换成两个不同的运算符“[tr//](https://www.geeksforgeeks.org/perl-tr-operator/)”和“[y//](https://www.geeksforgeeks.org/perl-y-operator/)”。
**例 1:**

```
#/user/bin/perl

# Initialising a string
$string = 'GeeksforGeeks';

# Calling the tr/// operator
$string =~ tr/G/g/;

# Printing the replaced string
print "$string\n";
```

**输出:**

```
geeksforgeeks

```

**例 2:**

```
#/user/bin/perl

# Initialising a string
$string = 'GeeksforGeeks';

# Calling the y/// operator
$string =~ y/G/g/;

# Printing the replaced string
print "$string\n";
```

**输出:**

```
geeksforgeeks

```