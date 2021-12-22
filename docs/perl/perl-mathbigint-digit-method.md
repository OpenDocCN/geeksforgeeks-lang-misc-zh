# Perl | Math::BigInt- >数字()方法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-digit-method/](https://www.geeksforgeeks.org/perl-mathbigint-digit-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

`**Math::BigInt**`模块的`**digit()**`方法用于从右数取给定数的**n<sup>th</sup>T5】位。要从左侧获取数字，我们需要将 **n** 指定为负数。**

> **语法:**数学::BigInt- >数字($n)
> 
> **参数:**
> **$n:** 表示要提取的数字的整数值。
> 
> **返回:**一个整数值，代表从右侧开始计数的给定数字的第 n 位。

**示例 1:** 使用`**Math::BigInt->digit()**`方法

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

$num = 7821593604;

# Create a BigInt object
$x = Math::BigInt->new($num);

# Initialize n
$n = 4;

# Get the nth digit
# counting from right side 
$nth_digit = $x->digit($n);

print "${n}th digit in $num is $nth_digit.\n";

# Assign new value to n
$n = 6;

# Get the nth digit 
# counting from right side
$nth_digit = $x->digit($n);

print "${n}th digit in $num is $nth_digit.\n";
```

**Output:**

```perl
4th digit in 7821593604 is 9.
6th digit in 7821593604 is 1.

```

**例 2:** 使用`**Math::BigInt->digit()**`方法从左侧获取**第 n 个**数字

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

$num = 7821593604;

# Create a BigInt object
$x = Math::BigInt->new($num);

# To get nth digit form 
# left side of the number
# we need to specify n 
# as a negative number 

# If n is negative then 
# then method will return
# nth digit from left side
# but counting will start from 1.

# Initialize n
$n = 4;

# Get the nth digit
# from left side 
$nth_digit = $x->digit(-$n);

print "${n}th digit from left in $num is $nth_digit.\n";

# Assign new value to n
$n = 6;

# Get the nth digit 
# counting from left side
$nth_digit = $x->digit(-$n);

print "${n}th digit from left in $num is $nth_digit.\n";
```

**Output:**

```perl
4th digit from left in 7821593604 is 1.
6th digit from left in 7821593604 is 9.

```

**例 3:** 使用`**Math::BigInt->digit()**`方法计算数字的位数总和

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

$num = 7821593604;

# Create a BigInt object
$x = Math::BigInt->new($num);

# Get the length of the number
$length = $x->length();

# Variable to store sum
$sum = 0;

# for loop to calculate 
# sum of digits in given number
for($i = 0; $i < $length; $i++)
{
    # Get the ith digit from the
    # right side of the number 
    $sum = $sum + $x->digit($i);

}

# Print sum
print "Sum of digits in $num is $sum.";
```

**Output:**

```perl
Sum of digits in 7821593604 is 45.

```