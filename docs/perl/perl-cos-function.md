# Perl | cos()函数

> 原文:[https://www.geeksforgeeks.org/perl-cos-function/](https://www.geeksforgeeks.org/perl-cos-function/)

该函数用于计算一个值的余弦值，如果省略了 VALUE，则计算$_ 的余弦值。该值应以弧度表示。

> **语法:** cos(值)
> 
> **参数:**
> **弧度形式的值**
> 
> **返回:**函数返回值的余弦值。

**例 1:**

```
#!/usr/bin/perl

# Calling cos function
$var = cos(5);

# Printing value of cos(5)
print "cos value of 5 is $var";
```

**输出:**

```
cos value of 5 is 0.283662185463226
```

**例 2:**

```
#!/usr/bin/perl

# Calling cos function
$var = cos(9);

# Printing value of cos(9)
print "cos value of 9 is $var";
```

**输出:**

```
cos value of 9 is -0.911130261884677
```