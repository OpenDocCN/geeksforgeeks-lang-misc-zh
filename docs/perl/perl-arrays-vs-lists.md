# Perl–数组与列表

> 原文:[https://www.geeksforgeeks.org/perl-arrays-vs-lists/](https://www.geeksforgeeks.org/perl-arrays-vs-lists/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 是一种通用的、解释的、动态的编程语言。Perl 有三种基本数据类型，即[标量](https://www.geeksforgeeks.org/perl-scalars/)、[数组](https://www.geeksforgeeks.org/perl-arrays/)和[散列](https://www.geeksforgeeks.org/perl-hashes/)。

### Perl 列表

[列表](https://www.geeksforgeeks.org/perl-list-and-its-types/)是标量值的序列。但是，该列表在 Perl 中不是一个数据结构。在 Perl 中，可以对列表执行的操作非常有限。由于没有变量引用此列表，因此列表不能用于打印以外的操作。

**例:**

```perl
(10, 20, 30);
("this", "is", "a", "list", "in", "perl");

```

#### 简单列表

简单列表是包含同类元素的列表。

```perl
# declaration without variable referencing
print("List declared and printed: ");
print join(' ', 10, 20, 30, 40, 50);
print("\n\n");

# qw() forms list by extracting words 
# out of the string using space as a delimiter.
print("List declared using qw(): ");
print join(' ', qw(this is gfg));
print("\n\n");

# indexing
print("Accessing element at index 2: ");
print((10, 20, 30, 40, 50)[2]);
print("\n\n");

# range
print("Range function on list\n");
print join(' ', 1..6);
print("\n\n");

# loop
print("Iterating over list elements:\n ");
foreach $element (1..6)
{
    print("$element\t");
}
print("\n\n");

# splicing
print("Splicing list\n");
print("Spliced elements: ");
print join(' ', (1..6)[1..3]);
print("\n\n");
```

**输出:**

```perl
List declared and printed: 10 20 30 40 50

List declared using qw(): this is gfg

Accessing element at index 2: 30

Range function on list
1 2 3 4 5 6

Iterating over list elements:
 1    2    3    4    5    6    

Splicing list
Spliced elements: 2 3 4

```

#### 复杂列表

复杂列表是包含异构元素的列表。

```perl
print("complex", 10, 20, "list");
```

**输出:**

```perl
complex1020list

```

#### 扁平列表

如果存在嵌套列表，它将被合并成一个没有任何嵌套的列表。

```perl
print(2, 3, 4, (5, 6));
print("\n");
print(2, 3, 4, 5, 6);
print("\n");
print((2, 3, 4), 5, 6);
print("\n");
```

**输出:**

```perl
23456
23456
23456
```

### Perl 数组

数组是一种 Perl 数据结构。Perl 中的数组是一个包含列表的变量。数组变量以“@”符号作为前缀。数组在 Perl 中有广泛的应用。对可以在阵列上执行的操作类型没有限制。Perl 中的数组可以是 2D，但是列表不能是二维的。

**例:**

```perl
@num = (10, 20, 30);
@str = ("this", "is", "a", "list", "in", "perl");

```

#### 数组操作

```perl
# declaration
@array = (10, 20, 30, 40, 50);
print("Declared array\n");
print join(' ', @array);
print("\n\n");

# accessing particular element
print("Accessing element at index 2 \n");
print(@array[2]);
print("\n\n");

# push
print("Pushing two elements in to the array\n");

## returns total no. of elements in updated array
push(@array, (60, 70)); 
print join(' ', @array);
print("\n\n");

# pop
print("Popping elements from array\n");
print("Popped element: ");

## returns the popped elements of the array
print(pop(@array)); 
print("\n");
print join(' ', @array);
print("\n\n");

# shift
print("Shift element in an array\n");
shift(@array);
print join(' ', @array);
print("\n\n");

# unshift
print("Unshift element in an array\n");
unshift(@array, 10);
print join(' ', @array);
print("\n\n");

# splicing the array
print("Splice an array\n");
print("Spliced elements: ");
print join(' ', splice @array, 3, 2 );
print("\nArray after being spliced: ");
print join(' ', @array);
print("\n\n");

# reversing the array
print("Reverse elements in an array\n");
print join(' ', reverse @array);
print("\n\n");

# loop
print("Iterate over elements in an array\n");
foreach $element (@array)
{
    print("$element\t");
}
print("\n\n");

# range
print("Range function\n");
@array1 = (1..5);
print("@array1\t");
print("\n\n");
```

**输出:**

```perl
Declared array
10 20 30 40 50

Accessing element at index 2 
30

Pushing two elements in to the array
10 20 30 40 50 60 70

Popping elements from array
Popped element: 70
10 20 30 40 50 60

Shift element in an array
20 30 40 50 60

Unshift element in an array
10 20 30 40 50 60

Splice an array
Spliced elements: 40 50
Array after being spliced: 10 20 30 60

Reverse elements in an array
60 30 20 10

Iterate over elements in an array
10    20    30    60    

Range function
1 2 3 4 5    

```

#### 2D 阵列

Perl 允许创建二维数组。

```perl
@array = ( [ 10, 20, 30 ],
           [ "ana", "joe", "ester" ],
           [ "Welcome to gfg" ] );

for $array_ref( @array ) 
{
    print("[ @$array_ref ], \n");
}
```

**输出:**

```perl
[ 10 20 30 ],
[ ana joe ester ],
[ Welcome to gfg ],

```

下表列出了阵列和列表之间的差异:

T58】Unshift

| 基于 | 数组 | 列表 |
| --- | --- | --- |
| 声明 | 一个变量引用一个列表 | 没有变量引用 |
| 访问元素 | 支持 | 索引支持 |
| 范围支持 | 范围支持 | 范围支持 |
| 推送支持 | 推送并在列表末尾插入新添加的元素 | 禁止推单。支持 |
| Pop | Pop，从列表末尾弹出一个元素。 | 列表中禁止 Pop |
| 循环 | 数组元素可以使用循环 | 迭代列表元素可以使用循环 |
| Shift | Shift 被支持，数组的第一个元素被移除 | Shift 在列表中禁止 |
| Unshift | 列表中禁止解除移位 |
| 拼接 | 阵列中支持拼接。列表中支持 | 拼接。但是，拼接列表无法访问，因为没有变量引用它。 |
| 反转 | 数组支持反转操作 | 列表不支持反转 |

在 Perl 中，列表和数组通常被认为是相同的。但是这两者是有区别的。虽然列表在 Perl 中不是一种数据结构，但数组是在 Perl 中引用列表的变量。在实际应用中，我们使用数组。