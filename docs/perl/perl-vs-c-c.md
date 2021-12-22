# Perl vs C/C++

> 原文:[https://www.geeksforgeeks.org/perl-vs-c-c/](https://www.geeksforgeeks.org/perl-vs-c-c/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 是一种通用、高级解释的动态编程语言。它是拉里·沃尔在 1987 年开发的。Perl 没有正式的首字母缩略词，但最常用的首字母缩略词是“实用提取和报告语言”。一些程序员也将 Perl 称为“病态的折衷垃圾列表者”或“几乎所有真正讨人喜欢的东西”。首字母缩略词“实用提取和报告语言”被广泛使用，因为 Perl 最初是为文本处理而开发的，比如从指定的文本文件中提取所需的信息，以及将文本文件转换成不同的形式。它支持过程式和面向对象编程。
[C++](https://www.geeksforgeeks.org/c-plus-plus/) 是一种通用编程语言，现在广泛用于竞技编程。它具有命令式、面向对象和泛型编程特性。C++运行在很多平台上，如视窗、Linux、Unix、Mac 等。
*下面是 Perl 和 c/c++的一些主要区别:*

<figure class="table">

| 特征 | Perl 语言 | C/C++ |
| --- | --- | --- |
| **驱动功能(主())** | 在 Perl 中不需要显式的驱动函数。 | C/C++代码需要 main()函数来执行，否则代码不会编译。 |
| **编译过程** | Perl 是一种解释的编程语言。 | C++是一种通用的面向对象编程语言。 |
| **关闭** | Perl 可以使用包含不可到达的私有数据的闭包作为对象。 | C/C++不支持闭包，在闭包中闭包可以被认为是可以作为变量存储的函数。 |
| **文件扩展名** | Perl 脚本是使用。pl 扩展。例如 perlDocument.pl | 那个。c 和。cpp 文件扩展名分别用于保存 c 和 c++代码。示例:myFile.c 和 myFile.cpp |
| **牙套** | 在 Perl 中，必须在 if 语句的“then”部分加上大括号。
Ex:
if(条件)
{语句；} | 在 C/C++中，没有必要在 if 和 lopps 后面放大括号。
Ex:
if(条件)
语句； |
| **字符串声明** | Perl 使用单引号来声明字符串。使用双引号强制对字符串中的内容进行求值。
示例:$ x = ' geeksforgeeks | C/C++使用双引号来声明字符串。
示例:string s = " geeksforgeeks |
| **评论** | 对于内联注释，我们在 Perl 中使用#号。
例如#内嵌 Perl 中的注释
 | C/C++使用//作为内联注释。
例如//内联-C/c++中的注释。
 |

</figure>

**c++和 Perl 中两个数相加的程序**T2】

## C++

```
// C++ program to add two numbers
#include <stdio.h>

// Function to perform addition
// operation
int add(int x, int y)
{
    int res = x + y;
    return res;
}

// Driver Code
int main()
{
    int choice = 3;
    int choice2 = 5;

    int res = add(choice, choice2);
    printf("The result is %d", res);
    return 0;
}
```

## Perl 语言

```
#!/usr/bin/perl

# Perl program to add two numbers
$choice = 3;
$choice2 = 5;
$res = add($choice, $choice2);
print "The result is $res";

# Subroutine to perform
# addition operation
sub add
{
    ($x, $y) = @_;
    $res = $x + $y;
    return $res;
}
```

**输出:**

```
The result is 8
```