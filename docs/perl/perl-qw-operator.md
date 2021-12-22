# Perl | qw 运算符

> 原文:[https://www.geeksforgeeks.org/perl-qw-operator/](https://www.geeksforgeeks.org/perl-qw-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 qw 运算符用于提取给定字符串的每个元素，因为它在单引号(')中的元素数组中。
这个函数代表**引用单词**，因为它认为给定字符串中的每个单词都像 qw(极客的极客)一样被引用，相当于(‘极客’，‘极客’)。
这个 qw()使用了圆括号，所以看起来像是一个函数，其实不是。它使用不同类型的分隔符，如下所示:

```perl
@String = qw/Ram is a boy/;
@String = qw{Geeks for Geeks};
@String = qw[Geeks for Geeks];
@String = qw'Geeks for Geeks';
@String = qw"Geeks for Geeks";
@String = qw!Geeks for Geeks!;
@String = qw@Geeks for Geeks@;
```

> **语法:** qw(字符串)
> 
> **参数:**
> **字符串:**是提取每个元素的输入字符串。
> 
> **返回:**给定字符串的每个元素，因为它是单引号(")中的元素数组。

**例 1:**

```perl
#!/usr/bin/perl

# Initialising a String as the parameter of qw
# operator whose each element is extracted.
@String = qw(GfG is a computer science portal);
foreach $key (@String) {
   print"Element is: $key\n";
}
```

 **输出:**

```perl
Element is: GfG
Element is: is
Element is: a
Element is: computer
Element is: science
Element is: portal

```

**例 2:**

```perl
#!/usr/bin/perl

# Initialising a String as the parameter of qw
# operator whose each element is extracted.
@String = qw(Delhi Mumbai Kolkata Patna);
foreach $key (@String) {
   print"City name is: $key\n";
}
```

**输出:**

```perl
City name is: Delhi
City name is: Mumbai
City name is: Kolkata
City name is: Patna

```

**注意:**qw 操作符读取一个空白，并提取空白前后的元素。