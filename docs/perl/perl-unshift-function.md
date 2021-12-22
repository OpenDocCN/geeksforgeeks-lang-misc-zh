# Perl | unshift()函数

> 原文:[https://www.geeksforgeeks.org/perl-unshift-function/](https://www.geeksforgeeks.org/perl-unshift-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 unshift()函数将给定的元素列表放在数组的开头。从而向右移动数组中的所有值。使用此操作可以取消多个值的偏移。此函数返回数组中新元素的数量。

> **语法:** unshift(数组，列表)
> **返回:**数组中新元素的数量

**例 1:**

## Perl 语言

```
#!/usr/bin/perl

# Initializing the array
@x = ('Geeks', 'for', 'Geeks');

# Print the Initial array
print "Original array: @x \n";

# Prints the number of elements
# returned by unshift
print "No of elements returned by unshift: ",
                   unshift(@x, 'Welcome', 'to');

# Array after unshift operation
print "\nUpdated array: @x";
```

**Output:** 

```
Original array: Geeks for Geeks 
No of elements returned by unshift: 5
Updated array: Welcome to Geeks for Geeks
```

**例 2:**

## Perl 语言

```
#!/usr/bin/perl

# Initializing the array
@x = (10, 20, 30, 40, 50);

# Print the Initial array
print "Original array: @x \n";

# Prints the number of elements
# returned by unshift
print "No of elements returned by unshift: ",
                   unshift(@x, 70, 80, 'Geeks');

# Array after unshift operation
print "\nUpdated array: @x";
```

**Output:** 

```
Original array: 10 20 30 40 50 
No of elements returned by unshift: 8
Updated array: 70 80 Geeks 10 20 30 40 50
```