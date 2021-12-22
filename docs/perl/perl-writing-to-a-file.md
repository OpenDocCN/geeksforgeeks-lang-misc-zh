# Perl |写入文件

> 原文:[https://www.geeksforgeeks.org/perl-writing-to-a-file/](https://www.geeksforgeeks.org/perl-writing-to-a-file/)

filehandle 是一个用于读写文件的变量。此文件句柄与文件相关联。

为了写入文件，它以写模式打开，如下所示:

```
open (FH, ‘>’, “filename.txt”);
```

如果文件存在，那么它会用新内容截断文件的旧内容。否则将创建一个新文件并添加内容。

**print() function**

print()函数用于将内容写入文件。

> **语法:** **打印**文件句柄字符串

这里，文件句柄在打开文件时与文件相关联，字符串保存要写入文件的内容。

**示例:**

```
# Opening file Hello.txt in write mode
open (fh, ">", "Hello.txt");

# Getting the string to be written
# to the file from the user
print "Enter the content to be added\n";
$a = <>;

# Writing to the file
print fh $a;

# Closing the file
close(fh) or "Couldn't close the file"; 
```

**写入文件前:**
![](img/01f1746ef102cb7f5eb6e5fa4e713ab8.png)

**执行代码写:**
![](img/a14bdc5d5a140b7f0f0a8af7198d7a7e.png)

**更新文件:**
![](img/75f31265153f1b09c0e6d52d969eafd8.png)

程序工作原理如下:
**第一步:**以写模式打开 Hello.txt 文件。
**第二步:**从标准输入键盘获取文本。
**步骤 3:** 将存储在“$a”中的字符串写入文件句柄“FH”
**指向的文件中步骤 4:** 关闭文件。

**将内容从一个文件复制到另一个文件:**

**代码执行前:**
**源文件:**
![](img/a46c505fca477e9a9aad84d137d897c4.png)
**目标文件:**
![](img/2578583d98c0cb68252423e5c479e766.png)

**示例:**
下面的示例从源文件中读取内容并将其写入目标文件。

```
# Source File 
$src = 'Source.txt';

# Destination File
$des = 'Destination.txt';

# open source file for reading
open(FHR, '<', $src);

# open destination file for writing
open(FHW, '>', $des); 

print("Copying content from $src to $des\n");
while(<FHR>)
{
   print FHW $_; 
}

# Closing the filehandles
close(FHR);
close(FHW);

print "File content copied successfully!\n";
```

**执行代码:**
![](img/7a726f2d9ee744365cea58d406c0cdf2.png)

**更新目的文件:**
![](img/0c4ad2b530b9e54aeffef2fb338df023.png)

程序是这样工作的:-
**第一步:**以读模式打开两个文件 Source.txt，以写模式打开 Destination.txt。
**步骤 2:** 从 FHR 读取内容，FHR 是文件句柄读取内容，而 FHW 是文件句柄将内容写入文件。
**第三步:**使用打印功能复制内容。
**步骤 4:** 读取文件完成后，关闭 conn。

**Error Handling and Error Reporting**

有两种方法可以处理错误

*   如果文件无法打开，抛出异常(处理错误)
*   如果文件无法打开并继续运行，则发出警告(错误报告)

**抛出异常(使用 die 函数)**
当无法为 filehandle 分配有效的文件指针时，执行 Die 打印消息并终止当前程序。
**例:**

```
# Initializing filename  
$filename = 'Hello.txt'; 
# $filename = 'ello.txt';

# Prints an error and exits 
# if file not found 
open(fh, '<', $filename) or 
     die "Couldn't Open file $filename"; 
```

![](img/f936e2a332e9bf7f3f8117d36e206bea.png)

在上面的代码中，当文件存在时，它只是简单地执行，没有错误，但如果文件不存在，那么它会产生一个错误，代码终止。

**发出警告(使用警告功能)**
当无法为文件句柄分配有效的文件指针时，它仅使用警告功能打印警告消息并继续运行。
**例:**

```
# Initializing filename 
$filename = 'GFG.txt'; 

# Opening a file and reading content 
if(open(fh, '<', $filename)) 
{ 
    while(<fh>) 
    { 
        print $_; 
    } 
} 

# Executes if file not found 
else
{ 
  warn "Couldn't Open a file $filename"; 
} 
```

文件存在时:
![](img/bdfc1f273c3d020486926d5ed3a6f79c.png)

当文件不存在时:
![](img/b3947a2e4c21771646cf50d90582f078.png)