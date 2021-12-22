# Perl | shift()函数

> 原文:[https://www.geeksforgeeks.org/perl-shift-function/](https://www.geeksforgeeks.org/perl-shift-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 shift()函数返回数组中的第一个值，将其移除，并将数组列表的元素向左移动一个。Shift 操作删除了类似 pop 的值，但从数组的开头而不是 pop 中的结尾开始。如果数组为空，此函数返回 undef，否则返回数组的第一个元素。

> **语法:**移位(数组)
> 
> **如果数组为空，则返回:** -1，否则返回数组的第一个元素

**例 1:**

```
#!/usr/bin/perl -w

# Defining Array to be shifted
@array1 = ("Geeks", "For", "Geeks");

# Original Array
print "Original Array: @array1\n";

# Performing the shift operation
$shifted_element = shift(@array1);

# Printing the shifted element
print "Shifted element: $shifted_element\n";

# Updated Array
print "Updated Array: @array1";
```

**Output:**

```
Original Array: Geeks For Geeks
Shifted element: Geeks
Updated Array: For Geeks

```

**例 2:**

```
#!/usr/bin/perl -w

# Program to move first element 
# of an array to the end

# Defining Array to be shifted
@array1 = ("Geeks", "For", "Geeks");

# Original Array
print "Original Array: @array1\n";

# Performing the shift operation
$shifted_element = shift(@array1);

# Placing First element in the end
@array1[3] = $shifted_element;

# Updated Array
print "Updated Array: @array1";
```

**Output:**

```
Original Array: Geeks For Geeks
Updated Array: For Geeks  Geeks

```