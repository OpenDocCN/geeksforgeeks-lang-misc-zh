# Perl | chop()函数

> 原文:[https://www.geeksforgeeks.org/perl-chop-function/](https://www.geeksforgeeks.org/perl-chop-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 chop()函数用于从输入字符串中删除最后一个字符。

> **语法:** chop(字符串)
> 
> **参数:**
> **字符串:**是去掉最后一个字符的输入字符串。
> 
> **返回:**最后删除的字符。

**例 1:**

```perl
#!/usr/bin/perl

# Initialising a string
$string = "GfG is a computer science portal";

# Calling the chop() function
$A  = chop($string);

# Printing the chopped string and 
# removed character
print " Chopped String is : $string\n";
print " Removed character is : $A\n";
```

 **输出:**

```perl
Chopped String is : GfG is a computer science porta
Removed character is : l

```

**例 2:**

```perl
#!/usr/bin/perl

# Initialising a string
$string = "[1, 2, 3]";

# Calling the chop() function
$A  = chop($string);

# Printing the chopped string and 
# removed character
print " Chopped String is : $string\n";
print " Removed character is : $A\n";
```

**输出:**

```perl
Chopped String is : [1, 2, 3
Removed character is : ]

```