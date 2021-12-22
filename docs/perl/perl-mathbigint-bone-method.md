# Perl | Math::BigInt- >骨()法

> 原文:[https://www.geeksforgeeks.org/perl-mathbigint-bone-method/](https://www.geeksforgeeks.org/perl-mathbigint-bone-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

**bone()** 方法的 **`Math::BigInt`** 模块用于创建一个值为 1 的新对象，如果在现有对象上使用，它会将其设置为 1。

> **语法:**数学:BigInt- >骨()
> 
> **参数:**
> 加减:将一的符号设置为“+”或“-”
> 
> **返回:**值为 1 的对象

**例 1:**

```
#!/usr/bin/perl  

# Import Math::BigInt module 
use Math::BigInt; 

# Create a BigInt object 
$x = Math::BigInt->bone();

# Object created with bone()
print("$x\n");

# Create a BigInt object 
$x = Math::BigInt->bone('-');

# Object created with bone()
print("$x");
```

**Output:**

```
1
-1

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
$x->bone();

# Object after function call
print("After function call: $x");
```

**Output:**

```
Before function call: 78215936043546
After function call: 1

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
$x->bone('-');

# Object after function call
print("After function call: $x");
```

**Output:**

```
Before function call: 78215936043546
After function call: -1

```