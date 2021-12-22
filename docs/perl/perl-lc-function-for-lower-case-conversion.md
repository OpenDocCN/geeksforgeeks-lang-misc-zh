# 小写转换的 Perl | lc()函数

> 原文:[https://www . geesforgeks . org/perl-LC-function-for-小写-conversion/](https://www.geeksforgeeks.org/perl-lc-function-for-lower-case-conversion/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 lc()函数返回 VAR 的较低版本，如果 VAR 被省略，则返回$_。

> **语法:** lc(VAR)
> **参数:**
> **VAR:** 要转换为小写
> **的句子返回:**
> VAR 的小写版本，如果省略 VAR 则返回$_ 的版本

**例 1:**

## Perl 语言

```
#!/usr/bin/perl

# Original String containing both
# lower and upper case letters
$original_string = "GEEkS FoR geEkS";

# Converting the string to Lower case
$changed_string = lc($original_string);

# Printing the original String
print "Original String : $original_string\n";

# Printing the Changed String
print "Changed String : $changed_string\n";
```

**输出:**

```
Original String : GEEkS FoR geEkS
Changed String : geeks for geeks
```

**例 2:**

## Perl 语言

```
#!/usr/bin/perl

# Original String containing
# lower and upper case letters
# as well as numerics
$original_string = "G33kS F0R g3EkS";

# Converting the string to Lower case
$changed_string = lc($original_string);

# Printing the original String
print "Original String : $original_string\n";

# Printing the Changed String
print "Changed String : $changed_string\n";
```

**输出:**

```
Original String : G33kS F0R g3EkS
Changed String : g33ks f0r g3eks
```