# Perl |有用的文件处理功能

> 原文:[https://www . geesforgeks . org/perl-有用-文件处理-函数/](https://www.geeksforgeeks.org/perl-useful-file-handling-functions/)

Perl 最初是为文本处理而开发的，比如从指定的文本文件中提取所需的信息，以及将文本文件转换成不同的形式。这些操作可以通过使用各种内置的文件功能来执行。

**示例:**

```
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

以下是在 Perl 中处理文件的一些有用的函数:

| 功能 | 描述 |
| **[glob()](https://www.geeksforgeeks.org/perl-glob-function/)** | 用于打印作为参数传递给它的目录中的文件 |
| **[告诉()](https://www.geeksforgeeks.org/perl-tell-function/)** | 使用文件句柄获取文件中读指针的位置 |
| **[【getc()](https://www.geeksforgeeks.org/perl-getc-function/)** | 用于从文件中读取下一个字符，该文件的文件句柄作为参数传递给它 |
| **[【逆()](https://www.geeksforgeeks.org/perl-reverse-function/)** | 在列表上下文中使用时，以相反的顺序返回列表，并返回列表值的串联字符串，在标量上下文中使用时，字符串的每个字符的顺序相反 |
| **[更名为()](https://www.geeksforgeeks.org/perl-rename-function/)** | 将文件的旧名称重命名为用户指定的新名称 |