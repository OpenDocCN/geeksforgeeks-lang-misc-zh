# Perl |删除前导和尾随空格(修剪)

> 原文:[https://www . geesforgeks . org/perl-删除-前导和尾随-空格-trim/](https://www.geeksforgeeks.org/perl-removing-leading-and-trailing-white-spaces-trim/)

从字符串中删除不需要的空格可用于仅存储所需的数据和删除不必要的尾随空格。这可以使用 Perl 中的 trim 函数来完成。trim 函数使用正则表达式来移除空格。它不是库函数，而是由用户在需要时定义的。修剪函数的类型有:

*   **Left Trimming (~ s/\ s+//)** : Remove redundant spaces from the leftmost part of the string until the actual text begins. Starting from the leftmost side, the string contains one or more spaces (\s+) and does not replace anything.
*   **Right Trimming (~ s/\ s+$/)** : Remove redundant spaces from the far right of the string until the actual end of the text is reached. Starting from the far right, the string contains one or more spaces (\s+) and does not replace anything.
*   **Trimming (~ s/\ s +| s+$//)** : The extra space on both sides of the strings is removed.

**示例:**以下代码演示了 Perl 中的左修剪、右修剪和修剪:

```perl

# Perl program for removing leading and
# trailing white spaces using trim

#!/usr/bin/perl

# Original String
$str1 = "     Geeks----";

print"The Original String is:\n";
print"${str1}\n\n";

# Applying left trim to str1
print"After Lefttrim Str1:\n";
$str1=~ s/^\s+//;
print"${str1}\n\n";

# again initializing the 
# value to string
$str1 = "----Geeks     ";

# Applying right trim to str1
print"After Righttrim Str1:\n";
$str1=~ s/\s+$//;
print"${str1}\n\n";

# again initializing the 
# value to strings
$str1="      Geeks      ";

# Applying trim to str1
print"After trim Str1:\n";
$str1=~ s/^\s+|\s+$//g;
print"${str1}\n";
```

**输出:**

```perl
The Original String is:
     Geeks----

After Lefttrim Str1:
Geeks----

After Righttrim Str1:
----Geeks

After trim Str1:
Geeks
```