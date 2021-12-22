# Perl | sin()函数

> 原文:[https://www.geeksforgeeks.org/perl-sin-function/](https://www.geeksforgeeks.org/perl-sin-function/)

此函数用于计算值的正弦值，如果省略了值，则计算$_ 的正弦值。这个函数总是返回一个浮点。

> **语法:** sin(值)
> 
> **参数:**
> **数值**以浮动形式出现
> 
> **返回:**函数返回正弦值。

**例 1:**

```
#!/usr/bin/perl

# Calling sin() function
$var = sin(5);

# Printing value for sin(5)
print "sin value of 5 is $var";
```

**输出:**

```
sin value of 5 is -0.958924274663138
```

**例 2:**

```
#!/usr/bin/perl

# Calling sin() function
$var = sin(9);

# Printing value for sin(9)
print "sin value of 9 is $var";
```

**输出:**

```
sin value of 9 is 0.412118485241757
```