# Perl |子程序或函数

> 原文:[https://www . geesforgeks . org/perl-子程序-或-函数/](https://www.geeksforgeeks.org/perl-subroutines-or-functions/)

一个 Perl 函数或子例程是一组共同执行特定任务的语句。在每种编程语言中，用户都希望重用代码。因此，用户将这段代码放在函数或子例程中，这样就不需要反复编写代码。在 Perl 中，术语*函数、子例程和方法是相同的*，但是在某些编程语言中，它们被认为是不同的。子程序这个词在 Perl 编程中使用最多，因为它是使用关键字 ***sub*** 创建的。每当调用该函数时，Perl 都会停止执行其所有程序，并跳转到该函数来执行它，然后返回到它之前运行的代码部分。可以避免使用 return 语句。

**定义子程序:**在 Perl 中定义子程序的一般形式如下-

```perl
sub subroutine_name
{
    # body of method or subroutine
}

```

**调用子程序:**在 Perl 中，子程序可以通过将参数列表传递给它来调用，如下所示-

```perl
subroutine_name(aruguments_list);
```

上述调用子例程的方式仅适用于 Perl 及更高版本。在 Perl 5.0 之前，有另一种调用子例程的方法，但是不建议使用，因为它绕过了子例程原型。

```perl
&subroutine_name(aruguments_list);
```

**示例:**

```perl
# Perl Program to demonstrate the 
# subroutine declaration and calling

#!/usr/bin/perl

# defining subroutine
sub ask_user {
   print "Hello Geeks!\n";
}

# calling subroutine
# you can also use
# &ask_user();
ask_user();
```

**输出:**

```perl
Hello Geeks!
```

**将参数传递给子程序:**这用于将值作为参数传递。这是使用特殊列表数组变量 *'$_'* 完成的。这将分配给函数$_[0]，$_[1]等等。

**示例:**

```perl
# Perl Program to demonstrate the 
# Passing parameters to subroutines

#!/usr/bin/perl

# defining subroutine
sub area 
{
    # passing argument    
    $side = $_[0];

    return ($side * $side);
}

# calling function
$totalArea = area(4);

# displaying result
printf $totalArea;
```

**输出:**

```perl
16
```

**使用子程序的优势:**

*   它帮助我们重用代码，并使发现错误和调试的过程变得容易。
*   它有助于以结构化格式组织代码。代码块以分段格式组织。
*   它增加了代码的可读性。