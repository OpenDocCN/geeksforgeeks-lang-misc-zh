# Perl |数据类型

> 原文:[https://www.geeksforgeeks.org/perl-data-types/](https://www.geeksforgeeks.org/perl-data-types/)

数据类型指定有效的 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 变量可以保存的数据类型。Perl 是一种**松散类型的语言**。在 Perl 程序中使用时，不需要为数据指定类型。 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 解释器将根据数据本身的上下文选择类型。

Perl 中有 3 种数据类型，如下所示:

1.  **标量**
2.  **阵列**
3.  **散列(关联数组)**

**1。标量:**它是单个数据单元，可以是整数、浮点、字符、字符串、段落或整个网页。要了解更多关于标量的信息，请参考 Perl 中的 [**标量。**](https://www.geeksforgeeks.org/perl-scalars/)

**示例:**

## Perl 语言

```
# Perl Program to demonstrate the
# Scalars data types

# An integer assignment
$age = 1;            

# A string
$name = "ABC";

# A floating point  
$salary = 21.5;    

# displaying result
print "Age = $age\n";
print "Name = $name\n";
print "Salary = $salary\n";
```

**输出:**

```
Age = 1
Name = ABC
Salary = 21.5
```

*   **标量运算:**对标量数据类型可以进行加、减、乘等多种运算。

**示例:**

## Perl 语言

```
# Perl Program to demonstrate
# the Scalars operations

#!/usr/bin/perl

# Concatenates strings
$str = "GFG" . " is the best";

# adds two numbers    
$num = 1 + 0;

# multiplies two numbers            
$mul = 4 * 9;

# concatenates string and number            
$mix = $str . $num;            

# displaying result
print "str = $str\n";
print "num = $num\n";
print "mul = $mul\n";
print "mix = $mix\n";
```

**输出:**

```
str = GFG is the best
num = 1
mul = 36
mix = GFG is the best1
```

**2。数组:**数组是以列表形式存储相同数据类型值的变量。要在 Perl 中声明一个数组，我们在变量名前面使用“@”符号。

```
@age=(10, 20, 30)
```

它将创建一个包含值 10、20 和 30 的整数数组。要访问数组的单个元素，我们使用“{content}”签名。

```
$age[0]
```

它将产生输出 10。要了解更多关于数组的信息，请参考 Perl 中的 [**数组**](https://www.geeksforgeeks.org/perl-arrays/)

**示例:**

## Perl 语言

```
# Perl Program to demonstrate
# the Arrays data type

#!/usr/bin/perl

# creation of arrays
@ages = (33, 31, 27);            
@names = ("Geeks", "for", "Geeks");

# displaying result
print "\$ages[0] = $ages[0]\n";
print "\$ages[1] = $ages[1]\n";
print "\$ages[2] = $ages[2]\n";
print "\$names[0] = $names[0]\n";
print "\$names[1] = $names[1]\n";
print "\$names[2] = $names[2]\n";
```

**输出:**

```
$ages[0] = 33
$ages[1] = 31
$ages[2] = 27
$names[0] = Geeks
$names[1] = for
$names[2] = Geeks
```

**3。哈希(关联数组):**它是一组键值对。它也被称为关联数组。为了在 Perl 中声明一个散列，我们使用“%”符号。要访问特定的值，我们使用“{content}”大括号中后跟键的符号。

**示例:**

## Perl 语言

```
# Perl Program to demonstrate the
# Hashes data type

# Hashes
%data = ('GFG', 7, 'for', 4, 'Geeks', 11);

#displaying result
print "\$data{'CR'} = $data{'CR'}\n";
print "\$data{'Ramos'} = $data{'Ramos'}\n";
print "\$data{'Bale'} = $data{'Bale'}\n";
```

**输出:**

```
$data{'GFG'} = 7
$data{'for'} = 4
$data{'Geeks'} = 11
```