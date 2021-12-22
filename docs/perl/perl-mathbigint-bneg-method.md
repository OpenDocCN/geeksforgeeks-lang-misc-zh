# Perl | Math::BigInt- > bneg()方法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-bneg-method/](https://www.geeksforgeeks.org/perl-mathbigint-bneg-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

**bneg()** 方法的 **`Math::BigInt`** 模块用于将输入值更改为负值，对零或 NAN 值不做任何操作

> **语法:**数学::bigint->bng()
> 
> **参数:**无参数
> 
> **返回:**值为否定值的对象

**例 1:**

```
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Specify number 
$num = 78215936043546; 

# Create BigInt object 
$x = Math::BigInt->new($num); 

$x->bneg();

print($x);
```

**Output:**

```
-78215936043546

```

**例 2:**

```
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Specify number 
$num = -78215936043546; 

# Create BigInt object 
$x = Math::BigInt->new($num); 

$x->bneg();

print($x);
```

**Output:**

```
78215936043546

```

**例 3:**

```
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Specify number 
$num = 0;
$num1 = NaN;

# Create BigInt object 
$x = Math::BigInt->new($num); 
$y = Math::BigInt->new($num1); 

$x->bneg();
$y->bneg();

print("$x\n");
print($y);
```

**Output:**

```
0
NaN

```