# Perl 匹配运算符

> 原文:[https://www.geeksforgeeks.org/perl-matching-operator/](https://www.geeksforgeeks.org/perl-matching-operator/)

Perl 中的 m 运算符用于匹配给定文本中的模式。传递给 m 运算符的字符串可以包含在用作正则表达式分隔符的任何字符中。
为了打印这个匹配的模式和剩余的字符串，m 操作符提供了各种操作符，包括$，它包含匹配的最后一个分组。
**{ content } amp；**–包含整个匹配字符串

#  **# Perl 匹配运算符** 

–包含匹配字符串
**{content}之前的所有内容；**–包含匹配字符串后的所有内容

> **语法:** m/String/
> 
> **返回:**
> 失败时 0，成功时 1

**例 1:**

```perl
#!/usr/bin/perl -w

# Text String
$string = "Geeks for geeks is the best";

# Let us use m operator to search 
# "or g"
$string =~ m/or g/;

# Printing the String
print "Before: 
 Perl 匹配运算符
\n";
print "Matched: {content}amp;\n";
print "After: {content}apos;\n";
```

**Output:**

```perl
Before: Geeks f
Matched: or g
After: eeks is the best

```

**例 2:**

```perl
#!/usr/bin/perl -w

# Text String
$string = "Welcome to GeeksForGeeks";

# Let us use m operator to search 
# "to Ge"
$string =~ m/to Ge/;

# Printing the String
print "Before: 
 Perl 匹配运算符
\n";
print "Matched: {content}amp;\n";
print "After: {content}apos;\n";
```

**Output:**

```perl
Before: Welcome 
Matched: to Ge
After: eksForGeeks

```