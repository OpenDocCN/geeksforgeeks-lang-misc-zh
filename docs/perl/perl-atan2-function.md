# Perl | atan2()函数

> 原文:[https://www.geeksforgeeks.org/perl-atan2-function/](https://www.geeksforgeeks.org/perl-atan2-function/)

该函数用于计算 Y/X 在-π到π范围内的反正切。

> **语法:** atan2(Y，X)
> 
> **参数:**
> **Y****X**为轴值
> 
> **返回:**函数返回-PI 到 PI 范围内 Y/X 的反正切。

**示例 1:**

```perl
#!/usr/bin/perl

# Assigning values to X and y
$Y = 45;
$X = 70;

# Calling atan2() function
$return_val = atan2($Y, $X);

# printing the value
print "atan2 of 45/70 is : $return_val\n";
```

 **输出:**

```perl
atan2 of 45/70 is : 0.571337479833627
```

**示例 2:**

```perl
#!/usr/bin/perl

# Assigning values to X and y
$Y = -30;
$X = 40;

# Calling atan2() function
$return_val = atan2($Y, $X);

# printing the value
print "atan2 of -30/40 is : $return_val\n";
```

**输出:**

```perl
atan2 of -30/40 is : -0.643501108793284
```