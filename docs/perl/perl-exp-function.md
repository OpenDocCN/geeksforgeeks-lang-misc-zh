# Perl | exp 函数

> 原文:[https://www.geeksforgeeks.org/perl-exp-function/](https://www.geeksforgeeks.org/perl-exp-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 exp 函数计算“e”作为参数的实数的幂。
这里的“e”是欧拉数或自然对数系的基数或俗称的一个近似于 2.718281828 的无理数，是最重要的数学常数之一。这个“e”被广泛应用于许多场合，如复利、伯努利试验、正态分布、微积分等。

> **语法:**经验值
> 
> **参数:**
> **值:**定义“e”要升到的幂的实值。
> 
> **返回:**e 的值升到给定实数值的幂。

**例 1:**

```
#!/usr/bin/perl

# Initialising some values for the
# parameter of the exp function
$A = 0;
$B = 1;
$C = 10;
$D = 20;

# Calling the exp function
$E = exp $A;
$F = exp $B;
$G = exp $C;
$H = exp $D;

# Getting the value of "e" raised to the
# power of the given parameter.
print "$E\n";
print "$F\n";
print "$G\n";
print "$H\n";
```

 **输出:**

```
1
2.71828182845905
22026.4657948067
485165195.40979

```

**例 2:**

```
#!/usr/bin/perl

# Calling the exp function
# Without Intitializing values to variables
$A = exp 1;
$B = exp 2;
$C = exp 3;
$D = exp 4;

# Getting the value of "e" raised to the
# power of values taken as the parameter.
print "$A\n";
print "$B\n";
print "$C\n";
print "$D\n";
```

**输出:**

```
2.71828182845905
7.38905609893065
20.0855369231877
54.5981500331442
```