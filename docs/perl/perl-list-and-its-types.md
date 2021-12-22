# Perl 列表及其类型

> 原文:[https://www.geeksforgeeks.org/perl-list-and-its-types/](https://www.geeksforgeeks.org/perl-list-and-its-types/)

**Introduction to Lists**

列表是标量值的集合。我们可以使用索引访问列表的元素。索引以 0 开始(第 0 个索引指列表的第一个元素)。我们使用括号和逗号运算符来构造一个列表。在 Perl 中，标量变量以$符号开始，而列表变量以@符号开始。
**重要说明:**perl 中的 List 不是数据结构。它们只是代码中的一些子表达式/表达式。它们通常被分配给一个数组。

## Perl 语言

```perl
#!/usr/bin/perl

# Empty List assigned to an array
# Note that the expression () is a
# list and "empty_list" variable is an
# array variable.
@empty_list = ();

# Note that the expression (1, 2, 3) is a
# list and "integer_list" variable is an
# array variable.
@integer_list = (1, 2, 3);
```

列表有多种类型，如下所述:

*   **简单列表:**具有相同数据类型的列表称为简单列表
    **示例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Empty List assigned to an array
@empty_list = ();

# List of integers
@integer_list = (1, 2, 3);

# List of strings assigned to an array
@string_list = ("Geeks", "for", "Geeks");

print "Empty list: @empty_list\n";
print "Integer list: @integer_list\n";
print "String list: @string_list\n";
```

*   **输出:**

```perl
Empty list: 
Integer list: 1 2 3
String list: Geeks for Geeks
```

*   **复杂列表:**列表可能包含各种不同的数据类型。这些类型的列表被称为复杂列表。
    **例:**

## Perl 语言

```perl
#!/usr/bin/perl

# List of strings and integers assigned to an array
@complex_list = (1, 2, "Geeks", "for", "Geeks");

# printing this List
print "Complex List: @complex_list";
```

*   **输出:**

```perl
Complex List: 1 2 Geeks for Geeks
```

*   **展平列表:**一个列表中可能包含另一个列表，但是 Perl 将展平内部列表，并且该列表的元素将被视为外部列表的元素。
    **例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining Internal list as an array
@Internal_list = (5, 6, 7);

# Defining External list.
@External_list = (1, "Geeks", 3, "For", @Internal_list);

# Printing Flattening list
print "Printing list within list: @External_list";
```

*   **输出:**

```perl
Printing list within list: 1 Geeks 3 For 5 6 7
```

**Accessing List Elements**

使用标量变量可以访问列表元素。访问列表元素时，使用了$符号，因为 Perl 中的标量变量是使用$符号访问的。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining a list
@List = (1, 2, 3, 4, 5);

# Accessing list element
print "Second element of List is: $List[2]";
```

**输出:**

```perl
Second element of List is: 3
```

**Slicing a List**

在 Perl 中对一个列表进行切片可以通过给另一个列表赋予逗号(，)分隔的索引值来完成。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining 1st List
@list1 = (1, "Geeks", 3, "For", 5);

# Defining 2nd List
@list2 = @list1[1, 2, 4];

# Printing Sliced List
print "Sliced List: @list2";
```

**输出:**

```perl
Sliced List: Geeks 3 5
```

**Defining Range in a List**

Perl 中的 Range 运算符是创建列表的一种简单方法。当与 list 一起使用时，range 运算符简化了用连续的数字和字母序列创建列表的过程。范围运算符也可用于对列表进行切片。

> **语法:**左值..右值

**注意:**如果左值大于右值，它将创建一个空列表，否则它将从左值到右值连续分配值。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining list with range of a to j
@x = ("a".."j");

# Defining list with range of 1 to 15
@y = (1..15);

# Defining list with range of A to J
@z = ("A".."J");

# Printing these lists
print "List with elements from a to j: @x\n";
print "List with elements from 1 to 15: @y\n";
print "List with elements from A to J: @z";
```

**输出:**

```perl
List with elements from a to j: a b c d e f g h i j
List with elements from 1 to 15: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
List with elements from A to J: A B C D E F G H I J
```

**组合范围和切片:**
范围和切片操作符可以组合在一起对列表进行切片操作。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining a list of elements
@x = ("Geeks", 2, 3, "For", 5);

# Use of Range and slice operator
@z = @x[2..4];

# Printing the sliced List
print "Sliced List: @z";
```

**输出:**

```perl
Sliced List: 3 For 5
```