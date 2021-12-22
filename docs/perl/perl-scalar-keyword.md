# Perl |标量关键字

> 原文:[https://www.geeksforgeeks.org/perl-scalar-keyword/](https://www.geeksforgeeks.org/perl-scalar-keyword/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的标量关键字用于将表达式转换为标量上下文。这是对标量上下文表达式的有力评估，即使它在列表上下文中运行良好。

> **语法:**标量表达式
> **返回:**一个标量值

**例 1:**

## Perl 语言

```
#!/usr/bin/perl -w

# Defining Arrays
@array1 = ("Geeks", "For", "Geeks");
@array2 = (1, 1, 0, 0, 9, 6);

# Concatenation of both arrays
@array3 = (@array1, @array2);

# Printing the Concatenated Array
# in List form
print "Array in List form: @array3\n";

# Conversion of Arrays to scalar context
@array3 = (scalar(@array1), scalar(@array2));

# Conversion to scalar returns
# the number of elements in the array
print "Array in scalar form: @array3\n";
```

**Output:** 

```
Array in List form: Geeks For Geeks 1 1 0 0 9 6
Array in scalar form: 3 6
```

**例 2:**

## Perl 语言

```
#!/usr/bin/perl -w

# Defining Arrays
@array1 = ("Welcome", "To", "Geeks");
@array2 = (1, 1, 0, 0, 9, 6);

# concatenation of both arrays
@array3 = ( @array1, @array2 );

# Printing the Concatenated Array
print "Concatenation of Arrays: @array3\n";

# Conversion of Arrays to scalar context to
# Evaluate Difference between size of arrays
@array3 = (scalar(@array2) - scalar(@array1));

# Printing the size Difference
print "Difference in number of elements: @array3\n";
```

**Output:** 

```
Concatenation of Arrays: Welcome To Geeks 1 1 0 0 9 6
Difference in number of elements: 3
```