# Perl |十六进制函数

> 原文:[https://www.geeksforgeeks.org/perl-hex-function/](https://www.geeksforgeeks.org/perl-hex-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的十六进制函数将给定的十六进制数(基数为 16)转换为其等价的十进制数(基数为 10)。

> **语法:**十六进制数
> 
> **参数:**
> **编号:**待转换的十六进制数
> 
> **返回:**给定十六进制数的等价十进制数。

**例 1:**

```perl
#!/usr/bin/perl

# Initialising some hexadecimal values for
# the parameter of the hex function
$A = "A";
$B = "B";
$C = "1A";
$D = "2C";

# Calling the hex function
$E = hex $A;
$F = hex $B;
$G = hex $C;
$H = hex $D;

# Getting the equivalent decimal number
# of the given hexadecimal number
print "$E\n";
print "$F\n";
print "$G\n";
print "$H\n";
```

 **输出:**

```perl
10
11
26
44

```

**例 2:**

```perl
#!/usr/bin/perl

# Initialising some hexadecimal values and
# Calling the hex function
$A = hex D;
$B = hex af;
$C = hex AF;
$D = hex BF;

# Getting the equivalent decimal number
# of the given hexadecimal number
print "$A\n";
print "$B\n";
print "$C\n";
print "$D\n";
```

**输出:**

```perl
13
175
175
191
```