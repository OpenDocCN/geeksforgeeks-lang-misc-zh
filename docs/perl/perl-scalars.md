# Perl |标量

> 原文:[https://www.geeksforgeeks.org/perl-scalars/](https://www.geeksforgeeks.org/perl-scalars/)

标量是一次存储单个数据单元的变量。标量变量存储的数据可以是不同的类型，如字符串、字符、浮点、一大组字符串，也可以是网页等等。
**例:**

## Perl 语言

```perl
# Perl program to demonstrate
# scalars variables

# a string scalar
$name = "Alex";

# Integer Scalar
$rollno = 13;

# a floating point scalar
$percentage = 87.65;

# to display the result
print "Name = $name\n";
print "Roll number = $rollno\n";
print "Percentage = $percentage\n";
```

**输出:**

```perl
Name = Alex
Roll number = 13
Percentage = 87.65
```

数值标量

数值标量变量保存像整数、整数(正和负)、浮点数(包含小数点)这样的值。下面的例子演示了 perl 中不同类型的数值标量变量。
**例:**

## Perl 语言

```perl
# Perl program to demonstrate various types
# of numerical scalar variables

# Positive integer numerical
# scalar variables
$intpositive = 25;

# Negative integer numerical
# scalar variables
$intnegative = -73;

# Floating point numerical
# scalar variables
$float = 23.5;

# In hexadecimal form
$hexadec = 0xcd;

# to display the result
print "Positive Integer = $intpositive\n";
print "Negative Integer = $intnegative\n";
print "Floating Point = $float\n";
print "Hexadecimal Form = $hexadec\n";
```

**输出:**

```perl
Positive Integer = 25
Negative Integer = -73
Floating Point = 23.5
Hexadecimal Form = 205
```

字符串标量

字符串标量变量保存的值类似于一个单词(由不同的字符组成)、一组单词或一个段落。下面的示例演示了不同类型的字符串标量变量。
**例:**

## Perl 语言

```perl
# Perl program to demonstrate various types
# of string scalar variables

# String scalar
$alphastring = "GeeksforGeeks";
$numericstring = "17";
$alphanumeric = "gfg21";

#special character in string scalar
$specialstring = "^gfg";

# in single quotes
$singlequt = 'Hello Geeks';

# To display the result
print "String with alphabets = $alphastring\n";
print "String with numeric values = $numericstring\n";
print "String with alphanumeric values = $alphanumeric\n";
print "String within Single quotes = $singlequt\n";
print "String with special characters = $specialstring\n";
```

**输出:**

```perl
String with alphabets = GeeksforGeeks
String with numeric values = 17
String with alphanumeric values = gfg21
String within Single quotes = Hello Geeks
String with special characters = ^gfg
```