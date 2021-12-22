# Perl |数组排序

> 原文:[https://www.geeksforgeeks.org/perl-sorting-of-arrays/](https://www.geeksforgeeks.org/perl-sorting-of-arrays/)

Perl 有一个内置的 sort()函数来对字母和数字的数组进行排序。当数组被传递给 sort()函数时，它会返回一个已排序的数组。

> **语法:**排序@数组
> 
> **返回:**一个排序数组

Perl 中数组的排序可以通过多种方式完成:

1.  使用 ASCII 值对数组进行排序
2.  比较功能的使用
3.  排序的字母顺序(不区分大小写)
4.  数字数组的排序

**Use of ASCII values to sort an Array**

由于大写字母的 ASCII 值小于小写字母的 ASCII 值，所有大写的值都排列在小写值开始之前。
**例:**

```
#!/usr/bin/perl

# Initializing an array
@country = ('India', 'America', 'london', 
            'france', 'bangladesh');

# Printing sorted array
print sort @country;
```

**Output:**

```
AmericaIndiabangladeshfrancelondon

```

以上程序是这样工作的:
**步骤 1-** 由于大写字母 A(从 65 开始)的 ASCII 值小于小写字母 A(从 97 开始)，所有大写字母单词都排列在小写字母单词之前。
**步骤 2-** 在上面的例子中，数组有国家名称，其中很少有单词以大写字母开头，而其他单词以小写字母开头，因此在对小写字母值排序之前，所有大写字母的值都会被排序。

**Use of Comparison function (cmp)**

在这种排序技术中，迭代器遍历原始数组的每两个元素。每次迭代，它将第一个值放入变量$a，将第二个值放入变量$b。现在，调用 cmp 函数，这些值以块的形式传递。如果$a 的内容应该保留在左边，这个函数将返回-1，而如果$b 的内容应该在左边，它将返回 1。
此功能可用于对数组进行降序排序。sort()函数默认使用 cmp()，但不使用 block。
**例:**

```
#!/usr/bin/perl

# Initializing an array
@fruits = ('chikoo', 'apple', 'banana',
           'orange', 'grapes');

# Sorting array in ascending order
@x = sort { $a cmp $b } @fruits;

# Sorting array in descending order
@y = sort { $b cmp $a } @fruits;

# Printing sorted array
print "Array in ascending order: @x\n";

# Printing sorted array
print "Array in descending order: @y";
```

**Output:**

```
Array in ascending order: apple banana chikoo grapes orange
Array in descending order: orange grapes chikoo banana apple

```

上面的程序是这样工作的:
**步骤 1-** 一个数组被初始化为水果的名称
**步骤 2-** 它从$a 的左边和$b 的右边获取值，并使用 cmp 函数比较这两个值。所以，在上面的例子中‘葡萄’被与‘千酷’相比较。

**Alphabetical order of Sorting(Case insensitive)**

为了对包含大写和小写值的数组进行排序，为了便于比较，需要将这些值转换为大写或小写。此外，cmp()函数将用于对数组进行排序。

**注意:**数组的原值不会被修改。
T3】例:

```
#!/usr/bin/perl

# Initializing an array
@fruits = ('Chikoo', 'Apple', 'banana',
           'orange', 'Grapes');

# Converting values to lower case for
# comparison before sorting
@x = sort { lc($a) cmp lc($b) } @fruits;

# Converting values to upper case for
# comparison before sorting
@y = sort { uc($a) cmp uc($b) } @fruits;

# Printing sorted array
print "Array after converting to lower case: @x\n";

# Printing sorted array
print "Array after converting to upper case: @y\n";
```

**Output:**

```
Array after converting to lower case: Apple banana Chikoo Grapes orange
Array after converting to upper case: Apple banana Chikoo Grapes orange

```

上面的程序是这样工作的:
**步骤 1-** 用值初始化一个数组。
**步骤 2-** 将值逐个转换为小写和大写，而不考虑它们的原始大小写，然后使用 cmp 函数进行比较并按升序排序。

**注:**可以看出两种情况下输出没有差别

**Sorting of an Array of Numbers**

如果使用排序函数对包含数字的数组进行排序，它会将数组中的每个值都作为字符串，因此 12 将放在 2 之前。因此，为了将这些值视为一个数字，在排序函数中使用了宇宙飞船运算符()而不是 cmp。该运算符将其操作数视为一个数字，并将数据排序为一个数字。

```
#!/usr/bin/perl

# Initializing an array
@n = (12, 44, 2, 5, 25, 7, 96, 1);

# Printing Original Array
print "Original Array: @n\n";

# Sorting numbers with use of
# spaceship operator
@x = sort { $a <=> $b } @n;

# Printing sorted array
print "Array after Sorting: @x";
```

**Output:**

```
Original Array: 12 44 2 5 25 7 96 1
Array after Sorting: 1 2 5 7 12 25 44 96

```

上面的程序是这样工作的:
**步骤 1-** 用数值初始化一个数组。
**步骤 2-** 使用宇宙飞船运算符将这些值视为数字，并根据$a 和$b 中的值返回 1、0、-1。