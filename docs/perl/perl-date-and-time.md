# Perl |日期和时间

> 原文:[https://www.geeksforgeeks.org/perl-date-and-time/](https://www.geeksforgeeks.org/perl-date-and-time/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 是功能最丰富的编程语言之一。Perl 是可移植的和跨平台的。Perl 可以在 100 多个平台上运行，具有高度集成的文本处理能力。 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 包含了 C、sed、awk、sh 等不同语言的特性。这使得 Perl 更加有用和高效。

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 是一种易于使用的语言。它旨在高效和完整，而不是优雅和最小化。Perl 支持一些主要的编程范例以及面向对象的、过程的和实用的。
Perl 中的日期和时间可以通过使用一个预定义的 Perl 模块来处理，这个模块叫做 DateTime 模块。DateTime 是一个用于表示日期和时间的各种组合的类。Perl 中的 [DateTime](https://metacpan.org/pod/DateTime) 模块代表新风格日历，在创建之前(1582 年)在时间上向后扩展。
这通常被称为“公历”。
在本日历中，日历的第一天(纪元)是第一年的第一天，对应于(错误地)被认为是耶稣基督诞生的日期。

> **语法:**使用 DateTime

### localtime()

**`localtime()`** 函数在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中返回系统的当前日期和时间，如果调用时没有传递任何参数。

```perl
#!/usr/local/bin/perl  
$datetime = localtime();  
print "Local Time of the System : $datetime\n"; 
```

**Output:**

```perl
Local Time of the System : Fri Nov 15 07:21:05 2019

```