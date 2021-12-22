# Perl |变量及其类型

> 原文:[https://www.geeksforgeeks.org/perl-variables-and-its-types/](https://www.geeksforgeeks.org/perl-variables-and-its-types/)

存储值的保留内存位置是变量。这意味着创建一个变量，会在内存中保留一个空间。变量的数据类型有助于解释器分配内存并决定在保留内存中存储什么。因此，变量可以存储整数、小数或字符串，并为变量分配不同的数据类型。
[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 有以下三种基本数据类型，即–

*   数量
*   数组
*   混杂

因此，在 Perl 中将使用三种类型的变量。标量变量可以存储数字、字符串或引用，并且前面有一个美元符号($)。数组变量将存储标量的有序列表，并在前面加上@符号。哈希变量将用于存储键/值对的集合，并将在前面加上符号%。

**Creating Variables**

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 变量不需要显式声明来保留内存空间。就像其他编程语言一样，' = '运算符左边的操作数基本上是变量的名称，' = '运算符右边的操作数基本上是变量中存储的值。
例如:

> $ age = 40
> $ name = " XYZ "；
> $ roll no = 22；
> 这里的 40、“XYZ”和 22 分别是分配给$age、$name 和$roll 无变量的值。

**Scalar Variables**

标量是单一的数据单位。数据可能是整数、浮点、字符、字符串、段落或整个网页。这里有一个使用标量变量的例子

## Perl 语言

```perl
#!/usr/bin/perl

# Assigning values to scalar
# variables
$age = 40;    
$name = "XYZ";
$rollno = 22;

# Printing variable values
print "Age = $age\n";
print "Name = $name\n";
print "Roll no = $rollno\n";
```

**输出:**

```perl
Age = 40
Name = XYZ
Roll no = 22 
```

**Array Variables**

存储标量值有序列表的变量是数组类型。数组数据类型的变量前面有一个“at”(@)符号。美元符号($)用于表示数组中的单个元素，其变量名后跟方括号中的元素索引。
下面是一个如何使用数组变量的例子:

## Perl 语言

```perl
#!/usr/bin/perl

# Assigning values to Array variables
@ages = (55, 80, 44);    # @ is used to declare
                        # array variables    
@names = ("XYZ", "LGH", "KMR");

# Printing values of Arrays
print "\$ages[0] = $ages[0]\n";
print "\$ages[1] = $ages[1]\n";
print "\$ages[2] = $ages[2]\n";
print "\$names[0] = $names[0]\n";
print "\$names[1] = $names[1]\n";
print "\$names[2] = $names[2]\n";
```

这里我们在“{content}”之前使用了“\ ”;签名只是为了把它打印成声明。否则，默认情况下，Perl 会将其理解为一个变量，并打印存储在其中的值。执行时，将产生以下输出–
**输出:**

```perl
$ages[0] = 55
$ages[1] = 80
$ages[2] = 44
$names[0] = XYZ
$names[1] = LGH
$names[2] = KMR 
```

**Hash Variables**

哈希是一组键/值对。哈希类型的变量前面有一个调制符号(%)。键用于引用哈希中的单个变量。要访问这些元素，在花括号中使用哈希变量名，后跟与值相关联的键。
下面是一个显示哈希变量的简单示例:

## Perl 语言

```perl
#!/usr/bin/perl

# Defining Hash variable using '%'
%data = ('XYZ', 55, 'LGH', 80, 'KMR', 44);

# Printing values of Hash variables
print "\$data{'XYZ'} = $data{'XYZ'}\n";
print "\$data{'LGH'} = $data{'LGH'}\n";
print "\$data{'KMR'} = $data{'KMR'}\n";
```

**输出:**

```perl
$data{'XYZ'} = 55
$data{'LGH'} = 80
$data{'KMR'} = 44 
```

**Variable Context**

基于上下文，Perl 对同一个变量的处理是不同的，即变量被使用的情况。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining Array variable
@names = ('XYZ', 'LGH', 'KMR');

# Assigning values of array variable
# to another array variable
@copy = @names;

# Assigning values of Array variable
# to a scalar variable
$size = @names;

# Printing the values of new variables.
print "Given names are : @copy\n";
print "Number of names are : $size\n";
```

**输出:**

```perl
Given names are : XYZ LGH KMR
Number of names are : 3
```

这里@names 是一个数组，已经在两个不同的上下文中使用过。首先，我们将其复制到任何其他数组中，即 list，因此它返回所有元素，假设上下文是 list context。接下来，尝试将同一个数组存储在标量中，默认情况下，假设该数组是标量上下文，则标量会进一步返回该数组中的元素数量。下表显示了各种上下文:

<figure class="table">

| 没有。 | 上下文和描述 |
| --- | --- |
| 1. | **标量**
标量变量赋值计算标量上下文中“=”右边的值。
 |
| 2. | **列表**
对数组或散列的赋值计算列表上下文中“=”的右边。
 |
| 3. | **布尔**
布尔上下文简单来说就是一个对表达式求值的地方，只是为了检查它是真还是假。
 |
| 4. | **Void**
这个上下文并不关心返回值是什么，甚至不需要返回值。
 |
| 5. | **插值**
这个上下文只会出现在引号("")中，或者出现在行为类似引号("")的事物中。
 |

</figure>