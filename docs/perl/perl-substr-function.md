# Perl | substr()函数

> 原文:[https://www.geeksforgeeks.org/perl-substr-function/](https://www.geeksforgeeks.org/perl-substr-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 substr()从传递给函数的字符串中返回一个子字符串，从给定的索引开始，直到指定的长度。默认情况下，如果没有指定长度，此函数将返回从给定索引开始的字符串的剩余部分。如果要用其他子字符串替换字符串的这一部分，也可以将替换字符串传递给 substr()函数。
该索引和长度值也可能为负值，这会改变字符串中索引计数的方向。
例如，如果传递负索引，那么子串将从字符串的右端返回，如果传递负长度，那么函数将从字符串的后端留下那么多字符。

> **语法:**子字符串(字符串、索引、长度、替换)
> **参数:**
> 
> *   **字符串:**要从中提取子字符串的字符串
> *   **索引:**子串的起始索引
> *   **长度:**子串的长度
> *   **替换:**替换子串(如果有)
> 
> **返回:**所需长度的子串

**注意:**参数“长度”和“替换”可以省略。

**例 1**

```
#!/usr/bin/perl

# String to be passed
$string = "GeeksForGeeks";

# Calling substr() to find string 
# without passing length
$sub_string1 = substr($string, 4);

# Printing the substring
print "Substring 1 : $sub_string1\n";

# Calling substr() to find the 
# substring of a fixed length
$sub_string2 = substr($string, 4, 5);

# Printing the substring
print "Substring 2 : $sub_string2 ";
```

**输出:**

```
Substring 1 : sForGeeks
Substring 2 : sForG 

```

**例 2**

```
#!/usr/bin/perl

# String to be passed
$string = "GeeksForGeeks";

# Calling substr() to find string 
# by passing negative index
$sub_string1 = substr($string, -4);

# Printing the substring
print "Substring 1 : $sub_string1\n";

# Calling substr() to find the 
# substring by passing negative length
$sub_string2 = substr($string, 4, -2);

# Printing the substring
print "Substring 2 : $sub_string2 ";
```

**输出:**

```
Substring 1 : eeks
Substring 2 : sForGee 

```