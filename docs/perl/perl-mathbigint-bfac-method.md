# Perl | Math::BigInt- > bfac()方法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-bfac-method/](https://www.geeksforgeeks.org/perl-mathbigint-bfac-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

`**Math::BigInt**`模块的`**bfac()**`方法用于计算存储为`**BigInt**`对象的数字的阶乘。

> **语法:**数学::BigInt- > bfac()
> 
> **参数:**无
> 
> **返回:**一个规范化的 BigInt 对象，其值代表给定数字的阶乘。

**示例 1:** 使用`**Math::BigInt->bfac()**`方法

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

$num = 5;

# Calculate the factorial of
# the above specified number

# Create a BigInt object
$x = Math::BigInt->new($num);

# Use Math::BigInt->bfac() method
# to calculate factorial
$factorial = $x->bfac();

print "Factorial of $num : $factorial\n";

$num = 10;

# Calculate the factorial of
# the above specified number

# Create a BigInt object
$x = Math::BigInt->new($num);

# Use Math::BigInt->bfac() method
# to calculate factorial
$factorial = $x->bfac();

print "Factorial of $num : $factorial\n";
```

**Output:**

```perl
Factorial of 5 : 120
Factorial of 10 : 3628800

```

**例 2:** 使用`**Math::BigInt->digit()**`方法计算大数阶乘中的位数

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

$num = 100;

# Calculate the factorial of
# the above specified number

# Create a BigInt object
$x = Math::BigInt->new($num);

# Use Math::BigInt->bfac() method
# to calculate factorial
$factorial = $x->bfac();

# Print the factorial
print "Factorial of $num : $factorial \n";

# Print count of digits in factorial
$count = $factorial->length();
print "Count of digits in factorial : $count";
```

**Output:**

```perl
factorial of 100 : 93326215443944152681699238856266700490715968264381621468592963895217599993229915608941463976156518286253697920827223758251185210916864000000000000000000000000 
Count of digits in factorial : 158

```

**例 3:** 使用`**Math::BigInt->digit()**`方法计算 nCr 值。

```perl
#!/usr/bin/perl 

# Import Math::BigInt module
use Math::BigInt;

# Value of n
$n = 5;

# Value of r
$r = 3;

# Create BigInt objects 
$x = Math::BigInt->new($n);
$y = Math::BigInt->new($r);
$z = Math::BigInt->new($n - $r);

# calculate nCr using 
# formula n! / (r! * (n-r)!)
$nCr = $x->bfac() / ($y->bfac() * $z->bfac());

# Print calculated value of nCr
print "Value of ${n}C${r} : $nCr \n";

# Value of n
$n = 50;

# Value of r
$r = 15;

# Create BigInt objects 
$x = Math::BigInt->new($n);
$y = Math::BigInt->new($r);
$z = Math::BigInt->new($n - $r);

# calculate nCr using 
# formula n! / (r! * (n-r)!)
$nCr = $x->bfac() / ($y->bfac() * $z->bfac());

# Print calculated value of nCr
print "Value of ${n}C${r} : $nCr \n";
```

**Output:**

```perl
Value of 5C3 : 10 
Value of 50C15 : 2250829575120 

```