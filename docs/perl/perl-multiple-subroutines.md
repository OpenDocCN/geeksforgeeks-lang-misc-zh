# Perl |多个子程序

> 原文:[https://www.geeksforgeeks.org/perl-multiple-subroutines/](https://www.geeksforgeeks.org/perl-multiple-subroutines/)

先决条件: [Perl |子程序或函数](https://www.geeksforgeeks.org/perl-subroutines-or-functions/)

一个 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 函数或子例程是一组共同执行特定任务的语句。在每种编程语言中，用户都希望重用代码。因此，用户将这段代码放在函数或子例程中，这样就不需要反复编写代码。
在 Perl 中，函数、子例程和方法这些术语是相同的，但是在某些编程语言中，它们被认为是不同的。子程序这个词在 Perl 编程中使用得最多，因为它是使用关键字 sub 创建的。每当有对函数的调用时，Perl 都会停止执行它的所有程序，并跳转到函数来执行它，然后返回到它之前运行的代码部分。可以避免使用 return 语句。

**定义子程序:**

在 Perl 中定义子例程的一般形式如下-

```perl
sub subroutine_name
{
    # body of method or subroutine
}
```

在 Perl 中，一个程序可以保存多个同名的子程序而不会产生错误，因为 Perl 允许编写多个同名的子程序，除非它们有不同的[签名](https://www.geeksforgeeks.org/function-signature-in-perl/)。这可以通过对具有相同名称的每个子例程使用不同的 arity 来定义。

**子程序的 Arity:**Perl 子程序可以有相同的名称，除非它们有不同的 Arity 集合。Arity 指的是子例程包含的参数数量。这些参数可以是也可以不是不同的数据类型。只要子程序的结构不同，Perl 程序就不会产生任何错误。

**使用‘multi’关键字:**
使用关键字‘multi’可以创建 Perl 中的多个子程序。这有助于创建多个同名的子例程。

**示例:**

```perl
multi Func1($var){statement};
multi Func1($var1, $var2){statement1; statement2;}

```

在创建内置函数和像 Perl 这样的编程语言中的大多数操作符时，使用多个子程序是非常常见的。这有助于降低程序的复杂性，因为每隔一个子程序不用不同的名字。无论需要什么代码语句，只需传递该函数所需的参数数量，工作就会完成。在这种情况下，编译器将选择子例程的版本，该子例程的函数签名与为执行而调用的签名相匹配。

各种程序，如数的阶乘、斐波那契数列等。需要多个函数来解决问题。使用多个子程序将有助于降低这类程序的复杂性。

**例 1:** 斐波那契数列的和。

```perl
#!/usr/bin/perl
# Program to print sum of fibonacci series

# Function for $n = 0
multi Fibonacci_func(0)
{
    1; # returning 1
}

# Function for $n = 1
multi Fibonacci_func(1)
{
    1; # returning 1
}

# Recursive function to calculate Sum
multi Fibonacci_func(Int $n where $n > 1)
{
    Fibonacci_func($n - 2) + 
    Fibonacci_func($n - 1);
}

# Printing the sum 
# using Function Call
print Fibonacci_func(17);
```

**输出:**

```perl
2584
```

上例使用*多个子程序*计算斐波那契数列的和。

**例 2:** 一个数的阶乘

```perl
#!/usr/bin/perl
# Program to print factorial of a number

# Factorial of 0
multi Factorial(0)
{
    1; # returning 1
}

# Recursive Function 
# to calculate Factorial
multi Factorial(Int $n where $n > 0)
{
    $n * Factorial($n - 1); # Recursive Call
}

# Printing the result 
# using Function Call
print Factorial(15);
```

**输出:**

```perl
3628800
```

在上面给出的例子中，程序使用“multi”关键字来声明多个同名但不同的子程序。