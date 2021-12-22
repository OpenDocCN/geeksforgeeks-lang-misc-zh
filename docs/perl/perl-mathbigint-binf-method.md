# Perl | Math::BigInt- > binf()方法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-binf-method/](https://www.geeksforgeeks.org/perl-mathbigint-binf-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

**binf()** 方法的 **`Math::BigInt`** 模块用于创建一个值为无穷大的新对象，如果在现有对象上使用，它会将其设置为无穷大。

> **语法:**数学::BigInt- > binf()
> 
> **参数:**
> 加减:将无穷大的符号设置为“+”或“-”
> 
> **返回:**值为 inf 的对象

**例 1:**

```
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Create a BigInt object 
$x = Math::BigInt->binf();

# Object created with binf()
print("$x\n");

# Create a BigInt object 
$x = Math::BigInt->binf('-');

# Object created with binf()
print("$x");
```

**Output:**

```
inf
-inf

```

**例 2:**

```
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Specify number 
$num = 78215936043546; 

# Create BigInt object 
$x = Math::BigInt->new($num); 

# Object before function call
print("Before function call: $x\n"); 

# Calling the function
$x->binf();

# Object after function call
print("After function call: $x");
```

**Output:**

```
Before function call: 78215936043546
After function call: inf

```

**例 3:**

```
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Specify number 
$num = 78215936043546; 

# Create BigInt object 
$x = Math::BigInt->new($num); 

# Object before function call
print("Before function call: $x\n"); 

# Calling the function with '-' sign
$x->binf('-');

# Object after function call
print("After function call: $x");
```

**Output:**

```
Before function call: 78215936043546
After function call: -inf

```