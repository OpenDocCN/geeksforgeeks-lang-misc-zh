# Perl | quotemeta()函数

> 原文:[https://www.geeksforgeeks.org/perl-quotemeta-function/](https://www.geeksforgeeks.org/perl-quotemeta-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 quotemeta()函数转义作为参数传递给它的值中的所有元字符。

**示例:**

```
Input : "GF*..G" 
Output : "GF\*\.\.G"

```

> **语法:** quotemeta(值)
> 
> **参数:**
> **值:**包含元字符的字符串
> 
> **返回:**
> 一个包含所有转义元字符的字符串

**例 1:**

```
#!/usr/bin/perl -w
$string = "GF*\n[.]*G";

print "Original String: \n";
print $string;

# Applying operation on the String
print "\n\nString after operation: \n";
print quotemeta($string);
```

**输出:**

```
Original String: 
GF*
[.]*G

String after operation: 
GF\*\
\[\.\]\*G
```

**例 2:**

```
#!/usr/bin/perl -w
$string = "GF+n\{.}/G";

print "Original String: \n";
print $string;

# Applying operation on the String
print "\n\nString after operation: \n";
print quotemeta($string);
```

**输出:**

```
Original String: 
GF+n{.}/G

String after operation: 
GF\+n\{\.\}\/G
```