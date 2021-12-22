# Perl | rand()函数

> 原文:[https://www.geeksforgeeks.org/perl-rand-function/](https://www.geeksforgeeks.org/perl-rand-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 rand()函数返回一个介于 0 和传递给它的正数值之间的随机小数，如果没有指定值，则返回 1。自动调用 srand()为随机数生成器播种，除非它已经被调用。

> **语法:** rand(range_value)
> 
> **参数:**
> **范围 _ 值:**一个正数指定范围
> 
> **返回:**
> 一个介于 0 和指定值之间的随机浮点数

**例 1:**

```
#!/usr/bin/perl -w

# Calling the rand function
$random = rand(15);

# print the random number
# between 0 and 15
print("Random Number between 0 and 15: ",
                          $random, "\n");
```

**输出:**

```
Random Number between 0 and 15: 12.6694798049858
```

**例 2:**

```
#!/usr/bin/perl -w

# Calling the rand function
# with negative value
$random = rand(-25);

# print the random number
# between 0 and -25
print("Random Number between 0 and -25: ", 
                           $random, "\n");
```

**输出:**

```
Random Number between 0 and -25: -7.54296459674615
```