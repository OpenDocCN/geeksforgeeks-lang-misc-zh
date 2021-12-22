# Perl | lcfirst()函数

> 原文:[https://www.geeksforgeeks.org/perl-lcfirst-function/](https://www.geeksforgeeks.org/perl-lcfirst-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 lcfirst()函数在将 first 字符转换为小写后返回字符串 VAR 或$_。

> **语法:** lcfirst(VAR)
> 
> **参数:**
> **VAR:** 第一个字符要转换成小写的句子
> 
> **返回:**第一个字符小写的字符串 VAR 或$_。

**例 1:**

```perl
#!/usr/bin/perl

# Original String containing both
# lower and upper case letters
$orignal_string = "GEEkS FoR geEkS";

# Converting the First character to Lower case
$changed_string = lcfirst($orignal_string);

# Printing the original String
print "Original String : $orignal_string\n";

# Printing the Changed String
print "Changed String : $changed_string\n";
```

**输出:**

```perl
Original String : GEEkS FoR geEkS
Changed String : gEEkS FoR geEkS

```

**例 2:**

```perl
#!/usr/bin/perl

# Original String containing 
# lower and upper case letters
# as well as numerics
$orignal_string = "G33kS F0R g3EkS";

# Converting the first character to Lower case
$changed_string = lcfirst($orignal_string);

# Printing the original String
print "Original String : $orignal_string\n";

# Printing the Changed String
print "Changed String : $changed_string\n";
```

**输出:**

```perl
Original String : G33kS F0R g3EkS
Changed String : g33kS F0R g3EkS

```