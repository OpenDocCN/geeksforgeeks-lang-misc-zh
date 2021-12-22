# Perl |有用的数组函数

> 原文:[https://www.geeksforgeeks.org/perl-useful-array-functions/](https://www.geeksforgeeks.org/perl-useful-array-functions/)

在 Perl 中，[数组](https://www.geeksforgeeks.org/perl-arrays/)是一种特殊类型的变量。数组用于存储值列表，列表中的每个对象被称为一个元素。元素可以是数字、字符串或任何类型的标量数据，包括另一个变量。
Perl 中的 Array 提供了各种内置函数来执行操作，比如在预定义的数组中添加和移除元素。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Initializing the array
@x = ('Java', 'C', 'C++');

# Print the Initial array
print "Original array: @x \n";

# Using push() function
# Pushing multiple values in the array
push(@x, 'Python', 'Perl');
print("Pushing new values...\n");

# Printing the array
print "Updated array: @x\n";

# Using pop() function
print("\nPopping the last element...\n");

# Prints the value returned by pop
print "Value returned by pop: ", pop(@x);

# Prints the array after pop operation
print "\nUpdated array: @x";
```

**Output:** 

```perl
Original array: Java C C++ 
Pushing new values...
Updated array: Java C C++ Python Perl

Popping the last element...
Value returned by pop: Perl
Updated array: Java C C++ Python
```

下面列出了一些有用的数组函数:

<figure class="table">

| 功能 | 描述 |
| [**推()**](https://www.geeksforgeeks.org/perl-push-function/) | 用于将值列表推到数组的末尾 |
| [**【pop()**](https://www.geeksforgeeks.org/perl-array-pop-function/) | 返回作为参数传递给它的数组的最后一个元素，从数组中移除该值 |
| [**shift()**](https://www.geeksforgeeks.org/perl-shift-function/) | 返回数组中的第一个值，将其移除并将数组列表的元素向左移动一个 |
| [**unshift()**T3】](https://www.geeksforgeeks.org/perl-unshift-function/) | 将给定的元素列表放在数组的开头，将所有值向右移动 |
| [**排序()**](https://www.geeksforgeeks.org/perl-sort-function/) | 用于在使用或不使用排序方法的情况下对列表进行排序 |
| [**【万阵()**](https://www.geeksforgeeks.org/perl-wantarray-function/) | 如果当前正在执行的子例程期望返回一个列表值，则返回 True 如果它正在寻找一个标量值，则返回 false。 |
| [**存在()**](https://www.geeksforgeeks.org/perl-exists-function/) | 用于检查给定数组或哈希中的元素是否存在 |
| [grep()T3](https://www.geeksforgeeks.org/perl-grep-function/) | 用于从给定数组中提取计算给定正则表达式真值的任何元素 |
| [**加入()**](https://www.geeksforgeeks.org/perl-join-function/) | 使用 VAR 的值将 LIST 的元素组合成一个字符串来分隔每个元素 |

</figure>