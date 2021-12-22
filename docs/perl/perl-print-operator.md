# Perl |打印操作符

> 原文:[https://www.geeksforgeeks.org/perl-print-operator/](https://www.geeksforgeeks.org/perl-print-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 print 运算符用于打印作为参数传递给它的 List 中表达式的值。Print 运算符打印作为参数传递给它的任何东西，无论它是字符串、数字、变量还是任何东西。双引号("")用作此运算符的分隔符。

> **语法:**打印" "
> **返回:**
> 失败时 0，成功时 1。

**例 1:**

## Perl 语言

```
#!/usr/bin/perl -w

# Defining a string
$string = "Geeks For Geeks";

# Defining an array of Integers
@array = (10, 20, 30, 40, 50, 60);

# Searching a pattern in the string
# using index() function
$index = index ($string, 'or');

# Printing the position of matched pattern
print "Position of 'or' in the string $index\n";

# Printing the defined array
print "Array of Integers is @array\n";
```

**Output:** 

```
Position of 'or' in the string 7
Array of Integers is 10 20 30 40 50 60
```

**例 2:**

## Perl 语言

```
#!/usr/bin/perl -w

# Defining a string
$string = "Welcome to GFG";

# Defining an array of integers
@array = (-10, 20, 15, -40, 45, -60);

# Searching a pattern in the string
# using index() function
$index = index($string, 'o G');

# Printing the position of matched pattern
print "Position of 'o G' in the string $index\n";

# Printing the defined array
print "Array of Integers @array\n";
```

**Output:** 

```
Position of 'o G' in the string 9
Array of Integers -10 20 15 -40 45 -60
```