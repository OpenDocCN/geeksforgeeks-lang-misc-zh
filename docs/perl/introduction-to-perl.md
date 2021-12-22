# Perl 简介

> 原文:[https://www.geeksforgeeks.org/introduction-to-perl/](https://www.geeksforgeeks.org/introduction-to-perl/)

[Perl](https://www.geeksforgeeks.org/perl-programming-language/) 是一种通用、高级解释和动态编程语言。它是拉里·沃尔在 1987 年开发的。没有正式的完整形式的 [Perl](https://www.geeksforgeeks.org/perl-programming-language/) ，但仍然，最常用的扩展是“ ***实用提取和报告语言*** ”。一些程序员也将 Perl 称为“病态的折衷垃圾列表者”或“几乎所有真正讨人喜欢的东西”。首字母缩略词“实用提取和报告语言”被广泛使用，因为 Perl 最初是为文本处理而开发的，比如从指定的文本文件中提取所需的信息，以及将文本文件转换成不同的形式。

[Perl](https://www.geeksforgeeks.org/perl-programming-language/) 支持过程编程和面向对象编程。Perl 在语法上与 C 非常相似，对于了解**[c++](https://www.geeksforgeeks.org/c-plus-plus/)**的用户来说很容易。

**Perl 的进化:**

这一切都始于拉里·沃尔正在进行一项任务，从大量有交叉引用的文本文件中生成报告。然后他开始用 *awk* 来完成这个任务，但是很快他发现这个任务还不够。因此，他没有为这项任务编写实用程序，而是编写了一种新的语言，即 Perl，并为它编写了解释器。他用 C 语言编写了 Perl 语言，其中一些概念取自 awk、sed 和 LISP 等。在开始的时候，Perl 仅仅是为系统管理和文本处理而开发的，但是在后来的版本中，Perl 获得了处理正则表达式和网络套接字等的能力。目前，Perl 因其处理正则表达式的能力而广受欢迎。Perl 的第一个版本是 1987 年 12 月 18 日发布的 **1.0** 。Perl 的**最新版本是 5.28** 。 **Perl 6** 与 Perl 5 不同，因为它是 Perl 5 的完全面向对象的重新实现。

#### 

为什么是 [Perl](https://www.geeksforgeeks.org/perl-programming-language/) ？

[Perl](https://www.geeksforgeeks.org/perl-programming-language/) 受欢迎和受欢迎的原因有很多。下面提到的原因很少:

*   **易于启动:** [Perl](https://www.geeksforgeeks.org/perl-programming-language/) 是一种高级语言，因此它更接近于其他流行的编程语言，如 C、C++等，因此变得对任何人来说都易于学习。
*   **文本处理:**作为“实用提取和报告语言”的缩写，表明 Perl 具有很高的文本操作能力，可以轻松地从不同的文本文件中生成报告。此外，它可以将文件转换成其他形式。
*   **包含最好的特性:** Perl 包含了不同语言的特性，如 C、sed、awk 和 sh 等。这使得 Perl 更加有用和高效。
*   **系统管理:**由于拥有不同的脚本语言能力，Perl 使得系统管理的任务变得非常容易。与其依赖于多种语言，不如使用 Perl 来完成整个系统管理任务。尽管如此，Perl 也用于网络编程、网络自动化、图形用户界面编程等。
*   **Web 和 Perl:** Perl 可以嵌入到 Web 服务器中以增加其处理能力，并且它有 DBI 包，这使得 Web-数据库集成非常容易。

**从 Perl 编程开始:**

*   **找解释器:**网上有各种 [IDEs](https://ide.geeksforgeeks.org/) 不用安装就可以运行 Perl 程序。
*   **Windows:** 有各种 ide 运行 Perl 程序或脚本:**T3】PadreT5、**T7】Eclipse 带 EPIC 插件** 等。**

#### 

用 Perl 编程

由于 Perl 在语法上与其他广泛使用的语言非常相似，所以用 Perl 进行编码和学习更容易。程序可以在任何广泛使用的文本编辑器中用 Perl 编写，如**记事本++** 、 **gedit** 等。写完程序后保存扩展名为 ***的文件。pl*** 或 ***。PL*** 要运行程序，请在命令行上使用 **perl file_name.pl** 。

**示例:**一个简单的程序打印*欢迎来到 GFG！*

```
# Perl program to print Welcome to GFG!
#!/usr/bin/perl

# Below line will print "Welcome to GFG!"
print "Welcome to GFG!\n";
```

**输出:**

```
Welcome to GFG!
```

**注释:**注释用于增强代码的可读性。解释器将忽略注释条目，并且不执行它们。注释可以是单行或多行。

*   **Single line Comment:**

    **语法:**

    ```
    # Single line comment
    ```

*   **Multi-line comment:**

    **语法:**

    ```
    = Multi line comments
    Line start from  = is interpreted as the
    starting of multiline comment and =cut is 
    consider as the end of multiline comment
    =cut
    ```

**打印:**在 Perl 中，在控制台上显示结果或任何指定的输出是一个函数。

**引号:**在 Perl 中，可以使用*单引号(')*或*双引号(" "*)。使用单引号不会插入任何变量或特殊字符，但是使用双引号会插入。

**\n:** 用于使用反斜杠(\)字符转义任何类型字符的新行字符。

**/usr/bin/perl:** 总是以#开头的是实际的 perl 解释器二进制！。这在 Perl 脚本模式编程中使用。

> **注意:** Perl 是区分大小写的编程语言，这就是为什么 *$Geeks* 和 *$geeks* 是两个不同的标识符。

**Perl 的优势:**

*   Perl 提供对跨平台的支持，并且它与标记语言如 HTML、XML 等兼容。
*   它在文本处理，即正则表达式中非常有效。它还提供了套接字功能。
*   它是免费的开源软件，在和 [*GNU 通用公共许可证(GPL)*](https://en.wikipedia.org/wiki/GNU_General_Public_License) 下获得许可。
*   它是一种可嵌入的语言，这就是为什么它可以嵌入到网络服务器和数据库服务器中。
*   它在[**【CPAN(综合 Perl 档案网)**](https://en.wikipedia.org/wiki/CPAN) 上支持超过 25，000 个开源模块，这些模块为标准库提供了许多强大的扩展。例如，XML 处理、图形用户界面和数据库集成等。

**Perl 的缺点:**

*   由于**[【CPAN】](https://en.wikipedia.org/wiki/CPAN)**模块，Perl 不支持可移植性。
*   程序运行缓慢，每次进行更改时都需要解释程序。
*   在 Perl 中，相同的结果可以通过几种不同的方式实现，这些方式会使代码变得不整洁和不可读。
*   与其他语言相比，可用性系数较低。

**应用:**

*   Perl 语言的主要应用之一是处理文本文件和分析字符串。
*   Perl 也用于 *[CGI(公共网关接口)](https://en.wikipedia.org/wiki/Common_Gateway_Interface)* 脚本。
*   用于网页开发，图形用户界面开发。
*   Perl 的文本处理能力也用于生成 SQL 查询。