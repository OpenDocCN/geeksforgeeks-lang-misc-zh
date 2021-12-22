# Perl |有用的数学函数

> 原文:[https://www.geeksforgeeks.org/perl-useful-math-functions/](https://www.geeksforgeeks.org/perl-useful-math-functions/)

在 Perl 中，有时需要求解包含一些数学运算的各种表达式。这些数学运算可以通过使用各种内置函数来执行。

```
#!/usr/bin/perl 

# Initialising some values for the 
# parameter of the exp function 
$A = 0; 
$B = 1; 

# Calling the exp function 
$E = exp $A; 
$F = exp $B; 

# Getting the value of "e" raised to the 
# power of the given parameter. 
print "$E\n"; 
print "$F\n"; 

# Calculating square root using sqrt() 
$square_root = sqrt(64); 

# Printing the result 
print "Squareroot of 64 is: $square_root"; 
```

下面列出了一些在 Perl 中用于数学运算的有用函数:

| 功能 | 描述 |
| **[exp()](https://www.geeksforgeeks.org/perl-exp-function/)** | 计算作为参数的实数的幂的“e” |
| **[【妖术()](https://www.geeksforgeeks.org/perl-hex-function/)** | 将给定的十六进制数(以 16 为基数)转换为其等效的十进制数(以 10 为基数)。 |
| **[【srand()](https://www.geeksforgeeks.org/perl-srand-function/)** | 帮助 rand()函数在程序每次运行时生成一个常量值 |
| **[【sqrt()](https://www.geeksforgeeks.org/perl-sqrt-function/)** | 用于计算数字的平方根 |
| **T1】oct()T3】** | 将传递的八进制值转换为相应的十进制值 |
| **[【rand()](https://www.geeksforgeeks.org/perl-rand-function/)** | 返回一个介于 0 和传递给它的正数之间的随机小数，如果没有指定值，则返回 1 |
| **[log()](https://www.geeksforgeeks.org/perl-log-function/)** | 返回传递给它的值的自然对数。如果在不传递值的情况下调用，则返回$_。 |
| **[int()](https://www.geeksforgeeks.org/perl-int-function/)** | 返回给定值的整数部分。如果没有提供值，它将返回$_ 个 |
| **[【罪恶()](https://www.geeksforgeeks.org/perl-sin-function/)** | 用于计算一个值的正弦值，如果省略了值，则计算$_ 的正弦值 |
| **[cos()](https://www.geeksforgeeks.org/perl-cos-function/)** | 用于计算值的余弦值，如果省略了值，则为$_ 值 |
| **[【atan2()](https://www.geeksforgeeks.org/perl-atan2-function/)** | 用于计算-π到π范围内的 Y/X 的反正切。 |
| **[【ABS()](https://www.geeksforgeeks.org/perl-abs-function/)** | 返回其参数的绝对值 |