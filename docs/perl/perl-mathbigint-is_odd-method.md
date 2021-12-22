# Perl | Math::BigInt->is _ odd()方法

> 原文:[https://www . geesforgeks . org/perl-mathbigint-is _ odd-method/](https://www.geeksforgeeks.org/perl-mathbigint-is_odd-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

`**Math::BigInt**`模块的`**is_odd()**`方法用于检查存储为`**BigInt**`对象的数字是否为奇数。

> **语法:**数学:BigInt- > is_odd()
> 
> **参数:**无
> 
> **如果 BigInt 对象中存储的数字是奇数，则返回:** true，否则返回 false。

**示例 1:** 使用`**Math::BigInt->is_odd()**`方法

```
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Value of n
$n = '89123751682746';

# Create BigInt object
$x = Math::BigInt->new($n);

# Check if the number stored
# in BigInt object is 
# an odd number or not
$isOdd = $x->is_odd();

if ($isOdd)
{
    print "$n is an odd number\n";
}

else
{
    print "$n is not an odd number\n";
}

# Value of n
$n = '6348762649837957979685908708650797587783';

# Create BigInt object
$x = Math::BigInt->new($n);

# Check if the number stored
# in BigInt object is
# an odd number or not
$isOdd = $x->is_odd();

if ($isOdd)
{
    print "$n is an odd number\n";
}

else
{
    print "$n is not an odd number\n";
}
```

**Output:**

```
89123751682746 is not an odd number
6348762649837957979685908708650797587783 is an odd number

```

**例 2:** 使用`**Math::BigInt->is_odd()**`方法检查八进制数是否为十进制奇数。

```
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Octal number represented as string
$octal = 726746425;

# value of octal '726746425'  is
# 123456789 in decimal number system 

# Create BigInt object
$x = Math::BigInt->from_oct($octal);

# Check whether the Octal 
# number stored in BigInt object
# is an odd number or not 
# using Math::BigInt->is_odd() method
$isOdd = $x->is_odd();

if($isOdd)
{
    print "$octal (in octal) is an odd number in decimal";
}

else
{
    print "$octal (in octal) is not an odd number in decimal";
}
```

**Output:**

```
726746425 (in octal) is an odd number in decimal

```

**例 3:** 使用`**Math::BigInt->is_odd()**`方法检查十六进制是否为十进制奇数。

```
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Hexadecimal number represented as string
$hex = 'Ox112210F4B16C1CB1';

# Hexadecimal value '0x112210F4B16C1CB1'  is
# 1234567890987654321 in decimal number system 

# Create BigInt object
$x = Math::BigInt->new($hex);

# Check whether the hexadecimal
# number stored in BigInt object
# is an odd number or not 
# using Math::BigInt->is_odd() method
$isOdd = $x->is_odd();

if($isOdd)
{
    print "$hex (in hexadecimal) is an odd number in decimal";
}

else
{
    print "$hex (in hexadecimal) is not an odd number in decimal";
}
```

**Output:**

```
Ox112210F4B16C1CB1 (in hexadecimal) is an odd number in decimal

```