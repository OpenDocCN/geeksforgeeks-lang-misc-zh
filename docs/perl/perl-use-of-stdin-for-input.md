# Perl |使用 STDIN 进行输入

> 原文:[https://www.geeksforgeeks.org/perl-use-of-stdin-for-input/](https://www.geeksforgeeks.org/perl-use-of-stdin-for-input/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 允许程序员接受用户的输入来执行操作。这使得用户更容易给出自己的输入，而不仅仅是程序员提供的硬编码输入。然后可以使用[打印()](https://www.geeksforgeeks.org/perl-print-operator/)功能处理和打印该输入。

使用**<【STDIN】>**可以通过键盘输入到一个 Perl 程序中。这里，STDIN 代表`**Standard Input**`。虽然没有必要将 STDIN 放在“钻石”或“飞船”操作符之间，即< >。这样做是标准做法。 **< >** 操作符也可以用来写入文件。< STDIN >也可以用在[标量和列表上下文](https://www.geeksforgeeks.org/perl-stdin-in-scalar-and-list-context/)中。

> **语法:**$ x =<STDIN>；或$ x =<>；

**例:**

```
#!/usr/bin/perl -w 
use strict;
use warnings;

print"Enter some text:";
my $string = <STDIN>;

print "You entered $string as a String";
```

**输入:**

```
GeeksForGeeks
```

**输出:**

```
Enter some text: GeeksForGeeks
You Entered GeeksForGeeks
as a String
```

在上面的代码中，给出输入后，需要按回车键。这个回车用来告诉编译器执行下一行代码。但是，<stdin>将按下的回车键作为给定输入的一部分，因此当我们打印该行时。在输入字符串后将自动打印一个新行。为了避免这种情况，使用了一个函数 **`chomp()`** 。该函数将删除用户提供的输入末尾的换行符。</stdin>

**例:**

```
#!/usr/bin/perl -w 
use strict;
use warnings;

print"Enter some text:";
my $string = <STDIN>;
chomp $string;

print "You entered $string as a String";
```

**输入:**

```
GeeksForGeeks
```

**输出:**

```
Enter some text: GeeksForGeeks
You Entered GeeksForGeeks as a String
```