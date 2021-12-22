# Perl | getc 函数

> 原文:[https://www.geeksforgeeks.org/perl-getc-function/](https://www.geeksforgeeks.org/perl-getc-function/)

**getc()** 函数在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中用于从文件中读取下一个字符，文件句柄作为参数传递给它。如果没有传递文件句柄，那么它将接受一个字符作为用户的输入。

> **语法:** getc(文件句柄)
> 
> **参数:**
> **待读文件的文件句柄:**
> 
> **返回:**从文件中读取的字符或文件结束时未定义的字符

**例 1:**

```perl
#!/usr/bin/perl 

# Opening a File in Read-only mode 
open(fh, "<", "File_to_be_read.txt"); 

# Reading next character from the file
$ch = getc(fh)

# Printing the read character
print"Character read from the file is $ch";

# Closing the File 
close(fh); 
```

**输出:**
![](img/312384cb6e2e0742ce7a171023f0f3f4.png)

**例 2:**

```perl
#!/usr/bin/perl 

# Value to be entered by the user
$ch = getc(STDIN);

# Printing the entered value
print"Value entered: $ch";
```

**输出:**
![](img/2e630ce31fa9e784b8d0a87437be5b1a.png)