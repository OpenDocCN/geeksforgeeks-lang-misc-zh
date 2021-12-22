# Perl | sort()函数

> 原文:[https://www.geeksforgeeks.org/perl-sort-function/](https://www.geeksforgeeks.org/perl-sort-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 sort()函数用于对列表进行排序，可以使用排序方法，也可以不使用排序方法。该方法可以由用户以子程序或块的形式指定。如果没有指定子例程或块，那么它将遵循默认的排序方法。

> **语法:**
> 排序列表
> 排序块，列表
> 排序子程序，列表
> 
> **根据用户要求返回:**排序列表

**例 1:**

```
#!/usr/bin/perl

@array1 = ("a", "d", "h", "e", "b");

print "Original Array: @array1\n";
print ("Sorted Array: ", sort(@array1));
```

**Output:**

```
Original Array: a d h e b
Sorted Array: abdeh

```