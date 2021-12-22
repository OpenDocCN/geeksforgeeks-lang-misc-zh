# Perl |数组(推送、弹出、移位、解除移位)

> 原文:[https://www . geesforgeks . org/perl-arrays-push-pop-shift-unshift/](https://www.geeksforgeeks.org/perl-arrays-push-pop-shift-unshift/)

Perl 提供了各种内置函数来添加和移除数组中的元素。

<figure class="table">

| 功能 | 描述 |
| 推 | 在数组末尾插入列表值 |
| 流行音乐 | 移除数组的最后一个值 |
| 变化 | 左移数组的所有值 |
| 松开打字机或键盘的字型变换键 | 将列表元素添加到数组的前面 |

</figure>

**push function**

该函数将列表中给出的值插入到数组的末尾。可以插入多个值，用逗号分隔。这个函数增加了数组的大小。它返回新数组中的元素数。

> **语法:**推送(数组、列表)

**例:**

## Perl 语言

```
#!/usr/bin/perl

# Initializing the array
@x = ('Java', 'C', 'C++');

# Print the Initial array
print "Original array: @x \n";

# Pushing multiple values in the array
push(@x, 'Python', 'Perl');

# Printing the array
print "Updated array: @x";
```

**输出:**

```
Original array: Java C C++ 
Updated array: Java C C++ Python Perl
```

**pop function**

此函数用于移除数组的最后一个元素。在执行 pop 函数后，数组的大小减少一个元素。如果列表为空，此函数返回 undef，否则返回数组的最后一个元素。

> **语法:** pop(数组)

**例:**

## Perl 语言

```
#!/usr/bin/perl

# Initializing the array
@x = ('Java', 'C', 'C++');

# Print the Initial array
print "Original array: @x \n";

# Prints the value returned by pop
print "Value returned by pop: ", pop(@x);

# Prints the array after pop operation
print "\nUpdated array: @x";
```

**输出:**

```
Original array: Java C C++ 
Value returned by pop: C++
Updated array: Java C
```

**shift function**

此函数返回数组中的第一个值，将其移除，并将数组列表的元素向左移动 1。Shift 操作删除了类似 pop 的值，但从数组的开头而不是 pop 中的结尾开始。如果数组为空，此函数返回 undef，否则返回数组的第一个元素。

> **语法:**移位(数组)

**例:**

## Perl 语言

```
#!/usr/bin/perl

# Initializing the array
@x = ('Java', 'C', 'C++');

# Print the Initial array
print "Original array: @x \n";

# Prints the value returned
# by shift function
print "Value returned by shift: ",
                        shift(@x);

# Array after shift operation
print "\nUpdated array: @x";
```

**输出:**

```
Original array: Java C C++ 
Value returned by shift :Java
Updated array: C C++
```

**unshift function**

该函数将给定的元素列表放在数组的开头。从而向右移动数组中的所有值。使用此操作可以取消多个值的偏移。此函数返回数组中新元素的数量。

> **语法:**未移位(数组，列表)

**例:**

## Perl 语言

```
#!/usr/bin/perl

# Initializing the array
@x = ('Java', 'C', 'C++');

# Print the Initial array
print "Original array: @x \n";

# Prints the number of elements
# returned by unshift
print "No of elements returned by unshift: ",
                   unshift(@x, 'PHP', 'JSP');

# Array after unshift operation
print "\nUpdated array: @x";
```

**输出:**

```
Original array: Java C C++ 
No of elements returned by unshift :5
Updated array: PHP JSP Java C C++
```