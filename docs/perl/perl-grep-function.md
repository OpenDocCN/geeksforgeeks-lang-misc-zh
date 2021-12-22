# Perl | grep()函数

> 原文:[https://www.geeksforgeeks.org/perl-grep-function/](https://www.geeksforgeeks.org/perl-grep-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 grep()函数用于从给定数组中提取任何元素，该数组计算给定正则表达式的真值。

> **语法:** grep(表达式，@Array)
> 
> **参数:**
> 
> *   **表达式:**它是用于在给定数组的每个元素上运行的正则表达式。
> *   **@Array :** 是调用 grep()函数的给定数组。
> 
> **返回:**给定数组中计算给定正则表达式真值的任何元素。

**例 1:**

```
#!/usr/bin/perl

# Initialising an array of some elements
@Array = ('Geeks', 'for', 'Geek');

# Calling the grep() function
@A = grep(/^G/, @Array);

# Printing the required elements of the array
print @A;
```

 **输出:**

```
GeeksGeek

```

在上面的代码中，正则表达式 **/^G/** 用于从给定的数组中获取以‘g’开头的元素，并丢弃剩余的元素。

**例 2:**

```
#!/usr/bin/perl

# Initialising an array of some elements
@Array = ('Geeks', 1, 2, 'Geek', 3, 'For');

# Calling the grep() function
@A = grep(/\d/, @Array);

# Printing the required elements of the array
print @A;
```

**输出:**

```
123

```

在上面的代码中，正则表达式 **/^d/** 用于从给定的数组中获取整数值并丢弃剩余的元素。

**例 3:**

```
#!/usr/bin/perl

# Initialising an array of some elements
@Array = ('Ram', 'Shyam', 'Rahim', 'Geeta', 'Sheeta');

# Calling the grep() function
@A = grep(!/^R/, @Array);

# Printing the required elements of the array
print @A;
```

**输出:**

```
ShyamGeetaSheeta

```

在上面的代码中，正则表达式**！/^R/** 用于获取不以‘r’开头的元素，丢弃以‘r’开头的元素。