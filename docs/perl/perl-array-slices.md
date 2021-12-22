# Perl |数组切片

> 原文:[https://www.geeksforgeeks.org/perl-array-slices/](https://www.geeksforgeeks.org/perl-array-slices/)

在 Perl 中，[数组](https://www.geeksforgeeks.org/perl-arrays/)是一种特殊类型的变量。数组用于存储值列表，列表中的每个对象被称为一个元素。元素可以是数字、字符串或任何类型的标量数据，包括另一个变量。
阵列可以存储任何类型的数据，并且可以通过多种方式访问这些数据。这些值可以通过在数组前放置 **$** 符号并在方括号内存储要访问的元素的索引值来提取。
**例如:**

```
# Define an array
@arr = (1, 2, 3);

# Accessing and printing first 
# element of an array
print "$arr[0]\n";

# Accessing and printing second
# element of an array
print "$arr[1]\n";
```

这种提取数组元素的方法一次只能提取一个元素，当要访问的元素列表很长时，这可能会变得令人困惑。例如，如果列表包含 100 个元素，并且我们需要从索引“a”到索引“b”提取 20 个元素，那么这个方法会造成混乱。为了避免这种情况，Perl 提供了一种数组切片的方法。这可用于访问一系列数组元素。

### 数组的切片

数组切片是为了访问数组中的一系列元素，以简化从数组中访问多个元素的过程。这可以通过两种方式实现:

*   传递多个索引值
*   使用范围运算符

**传递多个索引值:**
数组切片可以通过从要访问其值的数组中传递多个索引值来完成。这些值作为参数传递给数组名。Perl 将在指定的索引上访问这些值，并对这些值执行所需的操作。
**例:**

```
#!/usr/bin/perl

# Perl program to implement the use of Array Slice
@array = ('Geeks', 'for', 'Geek');

# Using slicing method
@extracted_elements = @array[1, 2];

# Printing the extracted elements
print"Extracted elements: ". 
     "@extracted_elements";
```

**Output:**

```
Extracted elements: for Geek

```