# Perl | sqrt()函数

> 原文:[https://www.geeksforgeeks.org/perl-sqrt-function/](https://www.geeksforgeeks.org/perl-sqrt-function/)

很多时候，在求解数学表达式时，我们需要计算一个数的平方根。
为了解决这个问题，像其他编程语言一样，Perl 为我们提供了一个内置函数 sqrt()，可以用来计算一个数的平方根。

> **语法:** sqrt 值
> 
> **返回:**传递值的平方根

**注意:** sqrt()只能计算正值的平方根。

**例 1:**

```
#!/usr/bin/perl

# Calculating square root using sqrt()
$square_root = sqrt(64);

# Printing the result
print "Squareroot of 64 is: $square_root";
```

**Output:**

```
Squareroot of 64 is: 8

```

**例 2:**

```
#!/usr/bin/perl

# Calculating square root using sqrt()
$square_root = sqrt(16);

# Printing the result
print "Squareroot of 16 is: $square_root";
```

**Output:**

```
Squareroot of 16 is: 4

```