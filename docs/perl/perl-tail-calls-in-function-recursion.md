# 函数递归中的 Perl |尾调用

> 原文:[https://www . geesforgeks . org/perl-tail-函数内调用-递归/](https://www.geeksforgeeks.org/perl-tail-calls-in-function-recursion/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/)中的递归是不使用`**for**`循环或`**while**`循环的任何函数，而是在程序执行过程中调用自己，对应的函数称为**递归函数**。

**尾部递归**函数是递归的一种特殊情况，其中函数调用语句作为过程的最终动作执行。所以 **`**return loop(..);**`** 会起作用，但是 **`**return loop() + operation;**`** 不会。**尾部递归(或尾端递归)**特别有用，并且在实现中通常很容易处理。尾递归的实现主要是为了避免堆栈数据结构占用空间，堆栈数据结构跟踪前一个递归调用语句返回的数据。

以下是几个更好理解这个概念的例子:

**例子 1:**

```
#!/usr/bin/perl 

# Perl Program to calculate Factorial 

# Recursion without tail call
sub recurse_fact 
{ 
    my $x = $_[0]; 

    # checking if that value is 0 or 1 
    if ($x == 0 || $x == 1) 
    { 
        return 1; 
    } 

    # Recursively calling function with 
    # the next value which is one less
    # than current one 
    else
    { 
        return $x * recurse_fact($x - 1); 
    } 
} 

# Recursion using Tail Call
sub tail_recurse_fact 
{ 
    my ($ans, $x) = @_; 

    # checking if that value is 0 or 1 
    if ($x == 0 || $x == 1) 
    { 
        return $ans; 
    } 

    # Recursively calling function with 
    # the next value which is one less
    # than current one 
    else
    { 
        return tail_recurse_fact($ans * $x, $x - 1); 
    } 
} 

# Driver Code 
$a = 5; 

# Function call and printing result after return 
print "Factorial of a number $a ", 
          "through recursion is ", recurse_fact($a);

print "\nFactorial of a number $a ", 
       "through tail-recursion is ", 
           tail_recurse_fact(1, $a); 
```

**Output:**

```
Factorial of a number 5 through recursion is 120
Factorial of a number 5 through tail-recursion is 120

```

在非尾部版本中，编译器需要跟踪要与之相乘的数字，而在尾部调用版本中，编译器可以意识到剩下要做的唯一工作是另一个函数调用，它可以忘记当前函数中使用的所有变量和状态。

**实施例 2:**

```
#!/usr/bin/perl

# Perl program to demonstrate the
# use of tail-recursion
use strict;
use warnings;

sub recurse_fib
{
    my $n = shift;

    if ($n == 1 or $n == 2) 
    {
        return 1 
    }

    # recursive calling
    return (recurse_fib($n - 1) + 
            recurse_fib($n - 2));         
}

sub tail_recurse_fib 
{
    my ($n, $a, $b) = @_;

    if ($n == 1) 
    {
        return $a
    }
    if ($n == 2) 
    {
        return $b
    }
    else 
    {
        # tail recursive calling
        return tail_recurse_fib($n - 1, $b, $a + $b)         
    }         
}

# Driver code
$a = 10;
print "Fibonacci upto $a through recursion is ", 
                                recurse_fib($a);
print "\nFibonacci upto $a through tail-recursion is ", 
                            tail_recurse_fib($a, 1, 1); 
```

**Output:**

```
Fibonacci upto 10 through recursion is 55
Fibonacci upto 10 through tail-recursion is 55

```

**使用`goto`语句演示 Tail 递归:** `**goto**`将编译器从当前运行的子程序转移到给定名称的子程序。这将替换函数调用，并以同样的方式创建递归过程。

```
# Perl program to demonstrate the
# use of tail-recursion
use warnings;

sub recurse
{
    my $i = shift;
    return if $i == 0;
    recurse($i - 1);
}

sub tail_recurse 
{
    my $i = shift;
    return if $i == 0;
    @_ = ($i - 1);
    goto &tail_recurse;
}

# Driver Code
print "recursing\n";
recurse(200);

print "tail_recursing\n";
tail_recurse(200);
```

**输出:**

```
recursing
tail_recursing

```

在上面的例子中，`**recurse**`函数将产生一个致命的“深度递归”错误，而`**tail_recurse**`将正常工作。

### 尾部呼叫的消除

尾部递归优于非尾部递归，因为尾部递归可以被现代编译器优化。现代编译器对尾部递归代码的优化称为**尾部调用消除**。尾部调用消除节省堆栈空间。它将函数**调用**替换为**转到**语句。这真的不是淘汰，而是**优化**。

有时候深度递归方法是解决问题最简单的方法，但是如果你递归超过几百次调用，你就会遇到 Perl 的“深度递归”错误。这就是为什么在 Perl 中尾部递归被用于非尾部递归代码的原因。

如果我们仔细看看上面讨论的函数，我们可以用 goto 删除最后一次调用。下面是尾部呼叫消除的例子。

**示例 1:一个数的阶乘**

```
#!/usr/bin/perl 

# Perl Program to calculate Factorial 
sub tail_recurse_fact 
{ 
    my $ans = shift; 
    my $x = shift; 

    # checking if that value is 0 or 1 
    if ($x == 0 || $x == 1) 
    { 
        return $ans; 
    } 

    # Recursively calling function with 
    # the next value which is one less 
    # than current one 
    else
    { 
        @_ = ($x * $ans, $x - 1);
        goto &tail_recurse_fact; 
    } 
} 

# Driver Code 
$a = 5; 

# Function call and printing result after return
print "Factorial of a number $a ", 
     "through tail-recursion is ", 
         tail_recurse_fact(1, $a); 
```

**Output:**

```
Factorial of a number 5 through tail-recursion is 120

```

**例 2:斐波那契厄普**

```
#!/usr/bin/perl

# Perl program to demonstrate the
# use of tail-recursion-elimination
use strict;
use warnings;

sub tail_recurse_fib
{
    my $n = shift;
    my $a = shift;
    my $b = shift;

    if ($n == 1) 
    {
        return $a
    }
    if ($n == 2) 
    {
        return $b
    }
    else 
    {
        @_ = ($n - 1, $b, $a + $b);

        # tail recursive calling
        goto &tail_recurse_fib;        
    }         
}

# Driver code
$a = 10;
print "Fibonacci upto $a through tail-recursion is ",
                          tail_recurse_fib($a, 1, 1); 
```

**Output:**

```
Fibonacci upto 10 through recursion is 55
Fibonacci upto 10 through tail-recursion is 55

```