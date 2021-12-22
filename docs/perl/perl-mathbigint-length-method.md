# Perl | Math::BigInt->length()方法

> 原文:[https://www . geesforgeks . org/perl-mathbigint-length-method/](https://www.geeksforgeeks.org/perl-mathbigint-length-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

**`Math::BigInt`** 模块的`**length()**`方法用于获取给定号码的长度，即给定号码中的位数。

> **语法:**数学:BigInt- >长度()
> 
> **参数:**无
> 
> **返回:**代表给定数字长度的整数值。

**示例 1:** 使用`**Math::BigInt->length()**`方法对数字进行计数

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Specify number
$num = 78215936043546;

# Create BigInt object
$x = Math::BigInt->new($num);

# Get the length (or count of 
# digits) of the
# given number using
# Math::BigInt->length() method
$len = $x->length();

print "Length of $num is $len.\n";

# Specify another number
$num = 7821593604584625197;

# Create BigInt object
$x = Math::BigInt->new($num);

# Get the length (or count of 
# digits) of the
# given number using
# Math::BigInt->length() method
$len = $x->length();

print "Length of $num is $len.\n";
```

**Output:**

```perl
Length of 78215936043546 is 14.
Length of 7821593604584625197 is 19.

```

**例 2:** 使用`**Math::BigInt->length()**`方法将给定的数字分成两半。

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Specify number
$num = 78215936043546;

# Create BigInt object
$x = Math::BigInt->new($num);

# Get the length (or count of 
# digits) of the
# given number using
# Math::BigInt->length() method
$len = $x->length(); 

# Variable to store first half
$firstHalf = 0;
$i = 1;

# loop to calculate first half
while($i <= ($len/2))
{
    $firstHalf = ($firstHalf * 10) + 
                    $x->digit(-$i);
    $i = $i + 1;

}

# Variable to store second half
$secondHalf = 0;

# Loop to calculate second half
while($i <= $x->length())
{
    $secondHalf = ($secondHalf * 10) + 
                      $x->digit(-$i);
    $i = $i + 1;
}

# Note: Math::BigInt->digit() method
# returns the digit at ith position 
# from right end of the given number
# a negative value of i is used
# to get ith digit from left end 
# of the given number

# Print original number
print "Original number: $num\n";

# Print first half
print "First half: $firstHalf\n";

# Print Second half
print "Second half: $secondHalf";
```

**Output:**

```perl
Original number: 78215936043546
First half: 7821593
Second half: 6043546

```