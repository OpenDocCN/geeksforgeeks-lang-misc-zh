# Perl | Math::BigInt- > bzero()方法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-bzero-method/](https://www.geeksforgeeks.org/perl-mathbigint-bzero-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

**bzero()** 方法的 **`Math::BigInt`** 模块用于创建一个值为零的新对象，如果在现有对象上使用，它会将其设置为零。

> **语法:**数学::bigint->bzro()
> 
> **参数:**无参数
> 
> **返回:**值为零的对象

**例 1:**

```perl
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
$x->bzero();

# Object after function call
print("After function call: $x");
```

**Output:**

```perl
Before function call: 78215936043546
After function call: 0

```

**例 2:**

```perl
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Create a BigInt object 
$x = Math::BigInt->bzero();

# Object created with bzero()
print("$x");
```

**Output:**

```perl
0

```