# Perl | Math::BigInt- > bnan()方法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-bnan-method/](https://www.geeksforgeeks.org/perl-mathbigint-bnan-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

**bnan()** 方法的 **`Math::BigInt`** 模块用于创建一个新的具有值 nan 的对象，如果在现有对象上使用，它会将其转换为 NAN。

> **语法:**数学::BigInt- > bnan()
> 
> **参数:**无参数
> 
> **返回:** NAN(不是数字)

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
$x->bnan();

# Object after function call
print("After function call: $x");
```

**Output:**

```perl
Before function call: 78215936043546
After function call: NaN

```

**例 2:**

```perl
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Create a BigInt object 
$x = Math::BigInt->bnan();

# Object created with bnan()
print("$x");
```

**Output:**

```perl
NaN

```