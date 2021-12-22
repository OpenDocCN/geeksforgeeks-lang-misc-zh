# Perl |替换运算符

> 原文:[https://www.geeksforgeeks.org/perl-substitution-operator/](https://www.geeksforgeeks.org/perl-substitution-operator/)

Perl中的替换运算符或' s '运算符用于用用户指定的某种模式替换字符串的文本。

> **语法:** s/text/pattern
> 
> **返回:失败时** 0，成功时替换次数

**例 1:**

```
#!/usr/bin/perl -w

# String in which text 
# is to be replaced
$string = "GeeksforGeeks";

# Use of s operator to replace
# text with pattern
$string =~ s/for/to/;

# Printing the updated string
print "$string\n";
```

**输出:**

```
GeekstoGeeks

```

**例 2:**

```
#!/usr/bin/perl -w

# String in which text 
# is to be replaced
$string = "Hello all!!! Welcome here";

# Use of s operator to replace
# text with pattern
$string =~ s/here/to Geeks/;

# Printing the updated string
print "$string\n";
```

**输出:**

```
Hello all!!! Welcome to Geeks

```