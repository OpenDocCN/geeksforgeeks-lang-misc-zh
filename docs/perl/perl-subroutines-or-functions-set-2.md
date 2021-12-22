# Perl |子程序或函数| Set–2

> 原文:[https://www . geesforgeks . org/perl-子程序-或-函数-set-2/](https://www.geeksforgeeks.org/perl-subroutines-or-functions-set-2/)

先决条件:[Perl 中的子程序或函数](https://www.geeksforgeeks.org/perl-subroutines-or-functions/)

一个 Perl 函数或子例程是一组共同执行特定任务的语句。在每种编程语言中，用户都希望重用代码。因此，用户将这段代码放在函数或子例程中，这样就不需要反复编写代码。*在本文中，我们将讨论以下概念:*

*   **将散列传递给子程序**
*   **将列表传递给子程序**
*   **子程序返回值**
*   **子程序中的局部和全局变量**
*   **子程序调用中不同数量的参数**

**将散列传递给子程序:**散列也可以传递给子程序，子程序会自动转换成键值对。
**例:**

## Perl 语言

```
# Perl program to demonstrate the
# passing of hash to subroutines

#!/usr/bin/perl

# Subroutine definition
sub Display_hash {

   # hash variable to store
   # the passed arguments
   my (%hash_var) = @_;

   # to display the passed list elements
   foreach my $key (keys %hash_var )
   {
      my $val = $hash_var{$key};
      print "$key : $val\n";
   }
}

# defining hash
%hash_para = ('Subject' => 'Perl', 'Marks' => 97);

# calling Subroutine with hash parameter
Display_hash(%hash_para);
```

**Output:** 

```
Marks : 97
Subject : Perl
```

**将列表传递给子程序:**我们知道 **@_** 是一个函数或子程序内部的特殊数组变量，所以它用来将列表传递给子程序。Perl 有一种不同的方式来接受和解析数组和列表，这使得很难从 **@_** 中提取离散元素。为了将列表与其他标量参数一起传递，有必要将列表作为最后一个参数。
**例:**

## Perl 语言

```
# Perl program to demonstrate the
# passing of lists to subroutines

#!/usr/bin/perl

# Subroutine definition
sub Display_List {

   # array variable to store
   # the passed arguments
   my @para_list = @_;

   # to print the passed list elements
   print "Given list is @para_list\n";
}

# passing scalar argument
$sc = 100;

# passing list
@li = (10, 20, 30, 40);

# Calling Subroutine with scalar
# and list parameter
Display_List($sc, @li);
```

**Output:** 

```
Given list is 100 10 20 30 40
```

**从子程序返回值:**子程序也可以像 C、C++、Java 等其他编程语言一样返回值。如果用户不会从子程序手动返回值，那么子程序将自动返回值。在这种情况下，自动返回值将是子例程中执行的最后一次计算。返回值可以是标量、数组或散列。
**例:**

## Perl 语言

```
# Perl Program to demonstrate the
# returning values subroutine

#!/usr/bin/perl

# subroutine definition
sub Sum {

   # To get total number
   # of parameters passed.
   $num = scalar(@_);
   $s = 0;

   foreach $i (@_)
   {
      $s += $i;
   }

   # returning sum
   return $s;
}

# subroutine calling and storing result
$result = Sum(30, 2, 40);

# displaying the result
print "Sum of the given numbers : $result\n";
```

**Output:** 

```
Sum of the given numbers : 72
```

**子程序中的局部和全局变量:**默认情况下，Perl 程序中的所有变量都是全局变量。但是借助**我的**关键字，你可以在一个块内创建*本地或私有的*变量。私有变量的作用域有限，比如在块之间(if、while、for、foreach 等)。)和方法等。*外块或方法*，这些变量不能使用。
**例:**

## Perl 语言

```
# Perl program to demonstrate the Local
# and Global variables in subroutine

#!/usr/bin/perl

# A Global variable
$str = "GeeksforGeeks";

# subroutine definition
sub Geeks {

   # Private variable by using my
   # keyword for Geeks function
   my $str;

   $str = "GFG";
   print "Inside the Subroutine: $str\n";
}

# Calling Subroutine
Geeks();

print "Outside the Subroutine: $str\n";
```

**Output:** 

```
Inside the Subroutine: GFG
Outside the Subroutine: GeeksforGeeks
```

**子程序调用中参数个数不同:** Perl 没有为我们提供任何声明子程序参数的内置设施，这使得向函数传递任意个数的参数变得非常容易。
**例:**

## Perl 语言

```
# Perl program to demonstrate the variable
# number of parameters to the subroutine

#!/usr/bin/perl

use strict;
use warnings;

# defining subroutine
sub Multiplication {

    # private variable containing
    # default value as 1
    my $mul = 1;

    foreach my $val (@_)
    {
        $mul *= $val;
    }

    return $mul;
}

# Calling subroutine with 4 parameters
print Multiplication(8, 2, 3, 4);

print "\n";

# Calling subroutine again but
# with 3 parameters
print Multiplication(3, 5, 4);
```

**Output:** 

```
192
60
```

**注意:**一般来说，将多个数组或哈希作为参数传递给子程序会导致它们丢失各自的标识。类似地，从子例程返回多个数组或散列也会导致它们丢失各自的标识。我们可以通过参考文献来解决这些问题。