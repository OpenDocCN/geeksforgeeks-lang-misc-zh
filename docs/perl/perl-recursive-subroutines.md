# Perl |递归子程序

> 原文:[https://www.geeksforgeeks.org/perl-recursive-subroutines/](https://www.geeksforgeeks.org/perl-recursive-subroutines/)

**先决条件:**[Perl 中的递归](https://www.geeksforgeeks.org/recursion-in-perl/)

**递归**是指属于或使用可重复应用的规则或程序**。它是通过算法的重复应用来定义函数或计算数字的过程。**递归子例程**是一种类型的[子例程](https://www.geeksforgeeks.org/perl-subroutines-or-functions/)，作为其执行的一部分调用自己，或者处于函数调用的潜在循环中。 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 为我们提供了迭代和递归使用子程序的灵活性。**

**一个简单的例子显示了递归子程序在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的使用，那就是计算一个数的阶乘。**

****例:****

```
#!/usr/bin/perl 

# Perl Program to calculate Factorial  
sub factorial
{ 

my $n = $_[0]; 

# checking if that value is 0 or 1 
if ($n == 0 || $n == 1) 
{ 
    return 1; 
} 

# Recursively calling the function with the next value 
# which is one less than current one 
else
{ 
    return $n * factorial($n - 1); 
} 
} 

# Driver Code 
$n = 7; 

# Function call and printing result after return 
print "Factorial of a number $n is ", factorial($n);
```

****输出:**

```
Factorial of a number 7 is 5040

```**