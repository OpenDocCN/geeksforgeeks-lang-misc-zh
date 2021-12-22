# Perl | Math::BigInt->is _ even()方法

> 原文:[https://www . geesforgeks . org/perl-mathbigint-is _ even-method/](https://www.geeksforgeeks.org/perl-mathbigint-is_even-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

`**Math::BigInt**`模块的`**is_even()**`方法用于检查存储为`**BigInt**`对象的数字是否为偶数。

> **语法:**数学:BigInt- >是 _even()
> 
> **参数:**无
> 
> **如果 BigInt 对象中存储的数字是偶数，则返回:** true，否则返回 false。

**示例 1:** 使用`**Math::BigInt->is_even()**`方法

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Value of n
$n = '89132506319263974586';

# Create BigInt object
$x = Math::BigInt->new($n);

# Check if the number stored
# in BigInt object is even or not
$isEven = $x->is_even();

if ($isEven)
{
    print "$n is an even number\n";
}

else
{
    print "$n is not an even number\n";
}

# Value of n
$n = '98793270075788553683446589224555431';

# Create BigInt object
$x = Math::BigInt->new($n);

# Check if the number stored
# in BigInt object is even or not
$isEven = $x->is_even();

if ($isEven)
{
    print "$x is an even number";
}

else
{
    print "$x is not an even number";
}
```

**Output:**

```perl
89132506319263974586 is an even number
98793270075788553683446589224555431 is not an even number

```

**例 2:** 使用`**Math::BigInt->is_even()**`方法检查十六进制数是否为十进制偶数。

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Hexadecimal string
$hexValue = '0x24CB016EA';

# value of '0x24CB016EA' in
# decimal number system is 9876543210

# Create BigInt object
$x = Math::BigInt->new($hexValue);

# Check whether the Hexadecimal 
# number stored as BigInt object
# is an even number or not 
# using Math::BigInt->is_even() method
$isEven = $x->is_even();

if($isEven)
{
    print "$hexValue is an even number in decimal";
}

else
{
    print "$hexValue is not an even number in decimal";
}
```

**Output:**

```perl
0x24CB016EA is an even number in decimal

```

**例 3:** 使用`**Math::BigInt->is_even()**`方法检查二进制数是否为十进制偶数。

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Binary string
$binary = '0b1001001100101100000001011011101010';

# 0b1001001100101100000001011011101010
# is 9876543210 in decimal 

# Create BigInt object
$x = Math::BigInt->new($binary);

# Check whether the Binary
# number stored as BigInt object
# is an even number or not 
# using Math::BigInt->is_even() method
$isEven = $x->is_even();

if($isEven)
{
    print "$binary is an even Number in decimal";
}

else
{
    print "$binary is not an even number in decimal";
}
```

**Output:**

```perl
0b1001001100101100000001011011101010 is an even Number in decimal

```