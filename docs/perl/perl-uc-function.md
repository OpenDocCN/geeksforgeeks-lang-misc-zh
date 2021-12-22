# Perl | uc()函数

> 原文:[https://www.geeksforgeeks.org/perl-uc-function/](https://www.geeksforgeeks.org/perl-uc-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 uc()函数将传递给它的字符串转换成大写后返回。它类似于 ucfirst()函数，只返回大写的第一个字符。

**注意:**已经大写的字符不修改。

> **语法:** uc String
> 
> **返回:**字符串大写。

**例 1:**

```
#!/usr/bin/perl -w

# String to be converted to UPPERCASE
$string = "geeksfOrGeeks";

print "Original String: $string\n";

# Converting the string to 
# UPPERCASE using uc() function
$UPPER_STRING = uc($string);

print "Modified String: $UPPER_STRING";
```

**Output:**

```
Original String: geeksfOrGeeks
Modified String: GEEKSFORGEEKS

```

**例 2:**

```
#!/usr/bin/perl -w

# String to be converted to UPPERCASE
$string = "WelComEToGeeKS";

print "Original String: $string\n";

# Converting the string to 
# UPPERCASE using uc() function
$UPPER_STRING = uc($string);

print "Modified String: $UPPER_STRING";
```

**输出:**

```
Original String: WelComEToGeeKS
Modified String: WELCOMETOGEEKS

```