# Perl 中的错误处理

> 原文:[https://www.geeksforgeeks.org/error-handling-in-perl/](https://www.geeksforgeeks.org/error-handling-in-perl/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的错误处理是对由于代码或编译器中的某些错误而导致执行困难的程序采取适当措施的过程。流程容易出错。例如，如果打开不存在的文件会引发错误，或者访问尚未声明的变量会引发错误。
如果出现错误，程序将暂停，因此使用错误处理，我们可以采取适当的措施，而不是完全暂停程序。错误处理是任何容易出错的语言的主要要求。

错误可以根据发生的时间进行分类:

1.  编译时错误
2.  运行时错误

**编译时错误:**是语法错误或文件引用缺失等错误导致程序无法成功编译。

**运行时间错误:**是程序运行时出现的错误，这些错误通常是产生不正确输出的逻辑错误。

## Perl 中的错误处理

Perl 提供了两个内置函数来生成致命异常和警告，它们是:

1.  模具()
2.  警告()

**die() :** 表示出现致命错误，即不允许所讨论的程序继续运行。

例如，使用 **`open()`** 访问文件时，在继续其他文件操作之前，会告知打开操作是否成功。

```perl
open FILE, "filename.txt" or die "Cannot open file: $!\n";
```

> **注:** ***$！*** 是一个预定义变量，返回系统返回的错误信息。

**warn() :** 与 **`die()`** 功能不同， **`warn()`** 生成警告而不是致命异常。

**例如:**

```perl
open FILE, "filename.txt" or warn "Cannot open file: $!\n";
```

### 可用于处理错误的其他方法

*   如果语句
*   除非功能
*   错误:“try”模块

**if 语句:**只有当条件成立时，代码块中的语句才会被执行。

## 实际抽取与汇报语言

```perl
if(-e $filename)){
  print "File exists";

} else {
  die "Cannot open the file. $!"
}
```

**除非函数:**代码块中的语句只有在表达式返回 false 时才会执行。

## 实际抽取与汇报语言

```perl
unless(-e $filename) {
   die "File Does not Exist! $!";
}
```

**错误:try:**它类似于 Java 编程语言中的 try 和 catch 块。

## 实际抽取与汇报语言

```perl
use Error ':try';

try{
  open FILE, "filename.txt" or die "File cannot be opened: $!";
  while () {
      # Do something
   }
   close FILE;
} catch Error::Simple with {
     my $err = shift;
     print "ERROR: $err";
};
```

## 模块内的错误

到目前为止，我们已经看到了 Perl 是如何处理错误并通知程序员的，但是如果一个模块中有错误需要通知程序员呢？这种错误会导致导入该特定模块的所有代码难以执行。

比如你做一个模块，比如说 **test.pm** ，我们做了一个错误的计算，所以会抛出一个错误消息，如下图所示:

## 实际抽取与汇报语言

```perl
package test;
sub functionName
{
   warn "Error in module!"
}
1;
```

```perl
use test;
functionName();
```

**输出:**

```perl
Error in module! at test.pm line 6
```

程序员可以使用这种错误处理技术来纠正模块中的所有错误。 **`Carp module()`** 可用于提供模块内报告错误的方法。

## 鲤鱼模块

它是模块警告和死亡的替代方案。它对用户定义的模块很有用，因为它们的行为有点像 **`die()`** 和 **`warn()`** ，但是带有一条由程序员添加的消息。
该 Carp 模块提供了以下功能:

1.  鲤鱼()
2.  cluck()
3.  croak()
4.  坦白()

**carp()函数:**该函数的工作方式类似于 warn 函数，在不退出脚本的情况下打印用户给出的消息。
T3】例:

## 实际抽取与汇报语言

```perl
package test;
use Carp;

sub functionName
{
   carp "Error in module!"
}
1;
```

```perl
use test;
functionName();
```

**输出:**

```perl
Error in module!  at test.pm line 8
```

**cluck()函数:**这个函数产生一个上下文，它是调用堆栈中每个调用的摘要。它遵循与 **`carp()`** 函数相同的过程，但是它打印导致调用特定函数的所有模块的堆栈。
**例:**

## 实际抽取与汇报语言

```perl
package Test;
use Carp qw(cluck);

sub function_name {
    cluck "Error in module!";
}
1;
```

```perl
use Test;
function_name();

```

**输出:**

```perl
Error in module! at Test.pm line 5
   Test::function_name() called at test.pl line 2
```

**croak()函数:**这个函数类似于 **`die()`** 函数，不同的是它会产生一个更短的消息，报告错误来自您的模块被调用的地方。
**例:**

## 实际抽取与汇报语言

```perl
package Test;
use carp;

sub functionName {
    croak "Error in module!";
}
1;
```

```perl
use Test;
functionName();
```

**输出:**

```perl
Error in module! at test.pl line 2
```

**坦白()功能:**这个功能类似于 **`cluck()`** 功能。它调用 die 函数，然后打印导致调用特定函数的所有模块的堆栈。
**例:**

## 实际抽取与汇报语言

```perl
package Test;
use Carp;

sub functionName {
    confess "Error in module!";
}
1;
```

```perl
use Test;
functionName();
```

**输出:**

```perl
Error in module! at Test.pm line 5
   Test::functionName() called at test.pl line 2
```