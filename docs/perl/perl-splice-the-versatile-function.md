# Perl | splice()–多功能功能

> 原文:[https://www . geeksforgeeks . org/perl-拼接多功能功能/](https://www.geeksforgeeks.org/perl-splice-the-versatile-function/)

在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中，splice()函数用于从数组中移除并返回一定数量的元素。可以插入元素列表来代替移除的元素。

> **语法:**拼接(@数组、偏移量、长度、替换 _ 列表)
> 
> **参数:**
> 
> *   @ array–the array under consideration.
> *   Offset–The offset of the element removal.
> *   Length–The number of elements to be removed from the offset (including the offset).
> *   Replace _ list- the list of elements that replace the removed elements.

**例:**

```perl
#!/usr/bin/perl

# an array of numbers from 0 to 7
@array = (0..7);                 

# Original array
print "Original Array: @array\n"; 

# splice() replaces elements from 
# 2 to 4 with a to c 
@array2 = splice(@array, 2, 3, (a..c)); 

# Printing the Updated Array
print("Elements of Updated \@array are @array\n");    

# array2 contains elements removed 
# from array i.e. 2, 3 and 4
print("Removed elements are @array2");         
```

**输出:**

```perl
Original Array: 0 1 2 3 4 5 6 7
Elements of Updated @array are 0 1 a b c 5 6 7
Removed elements are 2 3 4

```