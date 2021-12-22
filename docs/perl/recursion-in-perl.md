# Perl 中的递归

> 原文:[https://www.geeksforgeeks.org/recursion-in-perl/](https://www.geeksforgeeks.org/recursion-in-perl/)

递归是一种机制，当一个函数一次又一次地调用自己，直到满足所需的条件。当函数调用语句写在同一个函数中时，这样的函数称为递归函数。
传递给函数的参数是从默认数组@_ 中检索的，而每个值都可以被$_[0]，$_[1]等访问。
**例 1:** 下面的例子求出一个数的阶乘。

```
Factorial of any number n is (n)*(n-1)*(n-2)*....*1.
e.g.:
4! = 4*3*2*1 = 24
3! = 3*2*1 = 6
2! = 2*1 = 2
1! = 1
0! = 0
```

## Perl 语言

```
#!/usr/bin/perl

# Perl Program to calculate Factorial
sub fact
{

# Retrieving the first argument
# passed with function calling
my $x = $_[0];

# checking if that value is 0 or 1
if ($x == 0 || $x == 1)
{
    return 1;
}

# Recursively calling function with the next value
# which is one less than current one
else
{
    return $x * fact($x - 1);
}
}

# Driver Code
$a = 5;

# Function call and printing result after return
print "Factorial of a number $a is ", fact($a);
```

**程序工作原理如下:**
**步骤 1-** 当标量 a 的值为 0 或 1 时，函数将返回 1，因为两者的值都为 0！还有 1！是 1。
**步骤 2-** 当标量 a 的值为 2 时，fac(x-1)调用 fac(1)，该函数返回 1。
所以，是 2*阶乘(1) = 2*1 = 2。所以，它将返回 2。
**步骤 3-** 类似地，当每次调用时将更高的值传递给函数时，参数值将减少 1，并计算直到该值达到 1。
**示例 2:** 下面的示例计算斐波那契数列，直到给定的数字。

## Perl 语言

```
#!/usr/bin/perl

# Perl Program to print Fibonacci series
sub fib
{
    # Retrieving values from the parameter
    my $x = shift;
    my $y = shift;

    # Number till which the series is to be printed
    my $n = shift;

    # Check for the end value
    if ($y > $n)
    {
        return 1;
    }

    # Printing the number
    print " $y";

    # Recursive Function Call
    fib($y, $x + $y, $n);    
}

# Driver Code

# Number till which series is to be printed
$a = 5;

# First two elements of the series
$c = 0;
$d = 1;

print "$c";

# Function call with required parameters
fib($c, $d, $a);
```

**下面是程序的工作原理:**
**步骤 1-** 函数 fib()用 3 个参数调用，起始值为 0 和 1，而$n 是一个数字，直到要打印一个系列为止
**步骤 2-** 这些值以数组的形式传输，使用 shift 键检索这些值。
**步骤 3-** 在每次调用时，首先使用 shift 检索两个值，并将这些值存储在标量 x 和 y 中。现在，这两个值相加，得到序列中的下一个值。该步骤一直持续到数值达到用户提供的结束值