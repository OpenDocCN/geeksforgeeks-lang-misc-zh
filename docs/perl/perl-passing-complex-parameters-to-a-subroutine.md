# Perl |将复杂参数传递给子程序

> 原文:[https://www . geesforgeks . org/perl-将复杂参数传递给子程序/](https://www.geeksforgeeks.org/perl-passing-complex-parameters-to-a-subroutine/)

**先决条件:** [Perl |子程序或函数](https://www.geeksforgeeks.org/perl-subroutines-or-functions/)

一个 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 函数或子例程是一组共同执行特定任务的语句。在每种编程语言中，用户都希望重用代码。因此，用户将代码段放在函数或子例程中，这样就不需要一次又一次地重写相同的代码。由于这个原因，函数或子程序在每种编程语言中都被使用。这些函数或子程序可以采用各种不同类型的数据结构作为参数。其中一些解释如下:

1.  **Pass the list or array to the subroutine**
2.  **Pass the reference to subroutine**
3.  **Pass the hash to the subroutine**
4.  **Pass the file handle to the subroutine**

**将列表或数组传递给子程序:**数组或列表可以作为参数传递给子程序，数组变量@_ 用于接受子程序或函数内部的列表值。

**示例 1:** 这里，一个单独的列表被传递给子程序，并显示它们的元素。

```perl
#!/usr/bin/perl 

# Defining Subroutine
sub Display_List 
{ 

    # array variable to store 
    # the passed arguments 
    my @List1 = @_; 

    # Printing the passed list elements 
    print "Given list is @List1\n"; 
} 

# Driver Code

# passing list 
@list = (1, 2, 3, 4); 

# Calling Subroutine with 
# list parameter 
Display_List(@list); 
```

**输出:**

```perl
Given list is 1 2 3 4

```