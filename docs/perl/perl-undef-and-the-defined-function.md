# Perl | unde 和定义的函数

> 原文:[https://www . geesforgeks . org/perl-undf-and-the-defined-function/](https://www.geeksforgeeks.org/perl-undef-and-the-defined-function/)

**用于那些没有赋值的变量。人们可以将其与空值进行比较(在 Java、PHP 等中)。)和零(在 Ruby 中)。所以基本上当程序员声明一个 [**标量**](https://www.geeksforgeeks.org/perl-scalars/) 变量并且不赋值的时候，这个变量就应该包含*unde*值。在 Perl 中，如果一个变量的初始值是 undef，那么它将不打印任何东西。
**例:**** 

## **Perl 语言**

```perl
# Perl program for undef variable
# variable which declared without
# initial value

# variable x without initial value
my $x;

# printing its value
print "The value of x is = ${x}";
```

****输出:**** 

```perl
The value of x is = 
```

****undf()功能:***undf*用于重置任意变量的值。它可以带括号，也可以不带括号。这意味着使用该函数时括号是可选的。** 

*   ****例:**** 

## **Perl 语言**

```perl
# Perl program to illustrate
# the undef() function

# a variable with initial value 10
$k = 10;

# displaying its initial value
print "The value of variable k is ${k}\n";

# undef the variable
undef $k;

# value after the undef function
print "The value of variable k is ${x}\n";

# a variable with initial value 20
$m = 20;

# displaying its initial value
print "The value of variable m is ${m}\n";

# undef the variable
# you can also use
# $m = undef;
$m = undef();

# value after the undef function
print "The value of variable m is ${m}\n";
```

*   ****输出:**** 

```perl
The value of variable k is 10
The value of variable k is 
The value of variable m is 20
The value of variable m is 
```

****defined()函数:**该函数用于检查变量是否赋值。如果将值赋给变量，它将返回真，否则它将返回假。** 

*   ****语法:**** 

```perl
defined $variable_name
```

*   ****例:**** 

## **Perl 语言**

```perl
# Perl program to illustrate
# the defined() function.

# a variable assigned value 15
$k = 15;

# To check if variable is defined or not
if (defined $k)
{
     print "k is defined\n";
}
else
{
    print "k is not defined\n";
}

# undef the variable
$k = undef;

# To check if the variable is defined or not
if (defined $k)
{
    print "k is defined\n";
}
else
{
    print "k is not defined\n";
}
```

*   ****输出:**** 

```perl
k is defined
k is not defined
```

****注意:**虽然*未定义变量*没有定义值，但是在操作过程中可以取空值。例如，如果用户将两个变量 x 和 y 相加，其中 x 是 5，y 是未定义的，那么结果仍然是 5，因为 y 将取值 0。类似地，如果用户将两个字符串 strx 和 stry 连接起来，strx 的值为“GGF”，stry 为“未定义”，那么结果将是“GFG”，因为 stry 取空字符串“”的值。** 

*   ****例:**** 

## **Perl 语言**

```perl
# Perl program to demonstrate behaviour
# of undef variables, during operation
# like arithmetic, concatenation etc.

# first variable assigned with value
$x = 125;

# second variable with no value
my $y;

# arithmetic operation
$z = $x + $y;

# displaying sum
print "The sum of x and y is ${z}\n";

# declaring strx and assigned a value to it
$strx = "GFG";

# declaring stry without assigned value
my $stry;

# string concatenation
$strz = $strx.$stry;

# after concatenation
print "After concatenation of strx and stry  ${strz}\n";
```

*   ****输出:**** 

```perl
The sum of x and y is 125
After concatenation of strx and stry  GFG
```