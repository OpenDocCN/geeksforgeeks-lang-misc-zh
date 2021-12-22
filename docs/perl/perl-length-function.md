# Perl | length()函数

> 原文:[https://www.geeksforgeeks.org/perl-length-function/](https://www.geeksforgeeks.org/perl-length-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 length()函数查找给定字符串的长度(字符数)，如果未指定，则为$_ 个字符。

> **语法:**长度(VAR)
> 
> **参数:**
> **VAR:** 字符串或一组要计算长度的字符串
> **Return:**
> 返回字符串的大小。

**例 1:**

```
#!/usr/bin/perl

# String whose length is to be calculated
$orignal_string = "Geeks for Geeks";

# Function to calculate length
$string_len = length($orignal_string);

# Printing the Length
print "Length of String is: $string_len";
```

**输出:**

```
Length of String is: 15
```

**例 2:**

```
#!/usr/bin/perl

# String whose length is to be calculated
$orignal_string = "123456 is Geeks Code";

# Function to calculate length
$string_len = length($orignal_string);

# Printing the Length
print "Length of String is: $string_len";
```

**输出:**

```
Length of String is: 20
```

注意:如果要确定相应的大小，则使用数组或哈希上的标量上下文。