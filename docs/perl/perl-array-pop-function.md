# Perl |数组 pop()函数

> 原文:[https://www.geeksforgeeks.org/perl-array-pop-function/](https://www.geeksforgeeks.org/perl-array-pop-function/)

Perl 中的 pop()函数返回作为参数传递给它的 Array 的最后一个元素，将该值从数组中移除。请注意，传递给它的值必须是一个数组，而不是一个列表。

> **语法:**
> pop(数组)
> 
> **返回:**
> 如果列表为空，返回数组中的最后一个元素。

**例 1:**

```
#!/usr/bin/perl -w

# Defining an array of integers
@array = (10, 20, 30, 40);

# Calling the pop function
$popped_element = pop(@array);

# Printing the Popped element
print "Popped element is $popped_element";

# Printing the resultant array
print "\nResultant array after pop(): \n@array";
```

**Output:**

```
Popped element is 40
Resultant array after pop(): 
10 20 30

```

**例 2:**

```
#!/usr/bin/perl -w

# Defining an array of strings
@array = ("Geeks", "For", "Geeks", "Best");

# Calling the pop function
$popped_element = pop(@array);

# Printing the Popped element
print "Popped element is $popped_element";

# Printing the resultant array
print "\nResultant array after pop(): \n@array";
```

**Output:**

```
Popped element is Best
Resultant array after pop(): 
Geeks For Geeks

```