# Perl–函数和子程序的区别

> 原文:[https://www . geesforgeks . org/perl-函数和子程序的区别/](https://www.geeksforgeeks.org/perl-difference-between-functions-and-subroutines/)

在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中，当一个代码脚本变得更大，即包含数百行代码时，管理这样的代码脚本变得很困难。为了避免这个困难，Perl 为用户提供了函数和子程序的概念。函数和子程序将复杂/大量的代码分解成更小更简洁的部分，使程序更易读。

通过允许我们重用之前在程序中编写的代码，它们减少了应用程序的大小和调试时间。Perl 函数和子程序用于在程序中重用代码。在我们的应用程序中，我们可以在几个地方使用不同参数的函数。

#### 什么是函数？

一个函数占用了许多参数，用它们做了一些事情，然后返回一个值。它可以内置于编程语言中，也可以由用户提供。

在 Perl 中，当我们定义一个函数时，我们指定名称和语句序列。稍后，当我们想要执行计算时，我们可以通过名称“调用”函数，该函数将运行函数定义中包含的语句序列。
Perl 中有很多内置的函数，也很方便。例如，“say”是一个内置函数。Perl 甚至允许我们建立自己的函数，它可以帮助我们执行我们想做的任务。

#### 什么是子程序？

子程序(或 sub)赋予我们为代码段命名的能力，这样当我们想在程序中再次使用它时，我们只需调用它的名字就可以使用它。

子程序以两种主要方式帮助我们用 Perl 进行编程:

*   首先，它们允许我们在程序中再次重用代码，这使得发现和修复错误变得更容易，从而使编写程序变得更快。
*   其次，它们允许我们将代码分成组织部分。每个子程序负责一个特定的任务。

在 Perl 中，将一段代码放入子例程有两种情况:

*   当我们知道代码将被用于计算或行动，这将发生不止一次。例如，将强名称转换为特定格式，或者将传入的数据记录转换为哈希，等等。
*   当我们的程序中有逻辑单元时，我们希望将其分解，使我们的程序更容易理解。

下表列出了函数和子程序之间的区别:

| 功能 | 子程序 |
| --- | --- |
| 函数的基本格式是:$myvalue = myfunction(参数，参数)； | 子程序的基本格式是:子子程序名{#子程序主体} |
| Perl 中的函数意味着内置在 Perl 中的东西。Perl 内置的主要参考文档叫做 perlfunc。 | Perl 中的子例程是一段代码，它可以接受参数，用参数执行一些操作，并可能返回有意义的值，但不是必须的。然而，它们总是用户定义的，而不是内置的。 |
| 函数是由 Perl 提供给我们的。 | 子程序是我们提供给 Perl 的代码块。 |
| 函数类似于子程序，只是它们返回值。
一个函数通常会进行一些计算，并将结果报告给调用者。 | 子程序执行任务，但不向调用程序报告任何事情。 |
| 函数不能改变实际参数的值。 | 子程序可以改变实际参数的值。 |
| 一个函数有确定性的输出，没有副作用。
 | 子程序没有任何这样的限制。 |

**使用函数和子程序反转字符串的示例程序:**

## 功能

```perl
#!/usr/bin/perl
# Perl program to reverse a string
# using pre-defined function

# Creating a string
$string = "GeeksForGeeks"; 
print "Original string: $string", "\n";
print "Reversed string: "; 

# Calling pre-defined function
print scalar reverse("$string"), "\n";
```

## 子程序

```perl
#!/usr/bin/perl
# Perl program to reverse a string
# using a subroutine

# Creating a string
my $string = 'GeeksforGeeks';

print 'Original string: ', $string, "\n";
print 'Reversed using Subroutine: ', 
    reverse_in_place($string), "\n";

# Creating a subroutine
sub reverse_in_place
{
    my ($string) = @_;
    my @array = split //, $string;
    my $n = scalar @array;

    for (0 .. $n / 2 - 1)
    {
        my $tmp    = $array[$_];
        $array[$_] = $array[$n - $_ - 1];
        $array[$n - $_ - 1] = $tmp;
    }
    return join('', @array);
}
```

**Output:**

```perl
Original string: GeeksforGeeks
Reversed using Subroutine:  skeeGrofskeeG

```