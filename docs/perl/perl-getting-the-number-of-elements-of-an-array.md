# Perl |获取数组的元素数量

> 原文:[https://www . geesforgeks . org/perl-获取数组的元素数/](https://www.geeksforgeeks.org/perl-getting-the-number-of-elements-of-an-array/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的[数组](https://www.geeksforgeeks.org/perl-arrays/)是用于存储标量值有序列表的变量。数组变量前面有一个“at”(@)符号。可以使用数组上的标量上下文来确定数组的大小，该标量上下文返回数组中的元素数量

**例 1:**

```
#!/usr/bin/perl

# Initializing the array
@a = (1, 2, 3);

# Assigning the array to a scalar
# variable which stores size of
# the array
$s = @a;

# Printing the size
print "Size of the Array is $s";
```

**Output:**

```
Size of the Array is 3

```

上面的代码返回数组的物理大小，而不是有效元素的数量。为了获得数组的最大索引，使用了“$#”，如下例所示:

**例 2:**

```
#!/usr/bin/perl

# Initializing the array
@a = (1, 2, 3);

# Store the value at any index
# Let's take index 15 here,
$a[15] = 20;

# Printing the Array
print "Array is @a";

# Getting the maximum index 
# of the array
$i = $#a;

# Printing the Max. Index
print "\nMaximum index is $i";
```

**Output:**

```
Array is 1 2 3             20
Maximum index is 15

```

上面的代码是这样工作的:-
**第一步:**用一些值初始化一个数组
**第二步:**在任意一个随机索引处赋值，将其他索引留空
**第三步:**打印数组以显示数组中剩余的空格
**第四步:**使用获取最大索引“$ #”
**第五步:**此外，打印最大索引