# Perl |通过引用传递

> 原文:[https://www.geeksforgeeks.org/perl-pass-by-reference/](https://www.geeksforgeeks.org/perl-pass-by-reference/)

当一个变量通过引用传递时，函数对函数中的原始数据进行操作。通过引用传递允许函数改变变量的原始值。

当参数数组@_ 中元素的值改变时，相应参数的值也将改变。这就是通过引用传递参数的作用。

在下面给出的例子中，当我们在子程序示例中更新数组@a 的元素时，它也改变了参数的值，这些参数将反映在整个程序中。因此，当通过引用调用参数时，改变它们在函数中的值也会改变它们在主程序中的值。

**例 1:**

```perl
#!/usr/bin/perl

# Initialising an array 'a' 
@a = (0..10); 

# Array before subroutine call
print("Values of an array before function call: = @a\n");

# calling subroutine 'sample'
sample(@a);

# Array after subroutine call
print("Values of an array after function call: = @a");

# Subroutine to represent 
# Passing by Reference
sub sample
{ 
    $_[0] = "A";

    $_[1] = "B";
}
```

**输出:**

```perl
Values of an array before function call: = 0 1 2 3 4 5 6 7 8 9 10
Values of an array after function call: =  A B 2 3 4 5 6 7 8 9 10

```

以下是该程序的工作原理

1.  定义了一个由 0 到 10 的值组成的数组。
2.  此外，该数组被传递给“sample”子例程。
3.  已经定义了子例程“sample”。其中，第一个和第二个参数的值通过参数数组@_ 进行更改。
4.  调用子例程后会显示数组@a 的值。现在标量的前两个值分别更新为 A 和 B。

**例 2:**

```perl
#!/usr/bin/perl

# Initializing values to scalar
# variables x and y
my $x = 10;
my $y = 20;

# Values before subroutine call
print "Before calling subroutine x = $x, y = $y \n";

# Subroutine call
sample($x, $y);

# Values after subroutine call
print "After calling subroutine x = $x, y = $y ";

# Subroutine sample 
sub sample
{
    $_[0] = 1;
    $_[1] = 2;
}
```

**输出:**

```perl
Before calling subroutine x = 10, y = 20 
After calling subroutine x = 1, y = 2 

```