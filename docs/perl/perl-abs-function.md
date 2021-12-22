# Perl | abs()函数

> 原文:[https://www.geeksforgeeks.org/perl-abs-function/](https://www.geeksforgeeks.org/perl-abs-function/)

此函数返回其参数的绝对值。如果传递了一个纯整数值，那么它将按原样返回，但是如果传递了一个字符串，那么它将返回零。如果省略 VALUE，则使用$_

> **语法:** abs(值)
> 
> **参数:**
> **值:**必输项，可以是正数，也可以是负数，也可以是字符串。
> 
> **返回:**函数返回传递的参数的绝对值。

**例 1:**

```perl
#!/usr/bin/perl

# Defining decimal value
$var1 = 15.8;

# Defining integer value
$var2 = 7;

# Defining negative value
$var3 = "-15.2";

# Calling abs() function
$res1 = abs($var1);
$res2 = abs($var2);
$res3 = abs($var3);

# Printing these values
print "Abs value of var1 is $res1\n";
print "Abs value of var2 is $res2\n";
print "Abs value of var3 is $res3";
```

**输出:**

```perl
Abs value of var1 is 15.8
Abs value of var2 is 7
Abs value of var3 is 15.2
```

**例 2:**

```perl
#!/usr/bin/perl

# Defining string value
$var1 = "Geeks";

# Defining Fractional value
$var2 = 7/2;

# Calling abs() function
$res1 = abs($var1);
$res2 = abs($var2);

# Print these values
print "Abs value of var1 is $res1\n";
print "Abs value of var2 is $res2";
```

**输出:**

```perl
Abs value of var1 is 0
Abs value of var2 is 3.5
```