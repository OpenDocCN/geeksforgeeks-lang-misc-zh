# Perl |追加到文件中

> 原文:[https://www.geeksforgeeks.org/perl-appending-to-a-file/](https://www.geeksforgeeks.org/perl-appending-to-a-file/)

当使用“>”以写模式打开文件时，现有文件的内容将被删除，而使用 print 语句添加的内容将被写入文件。在这种模式下，写入点将被设置到文件的末尾。因此，文件的旧内容保持不变，任何使用 print 语句写入文件的内容都会添加到文件的末尾。但是，除非文件以+> >模式打开，指示追加和读取，否则无法执行读取操作。

**示例:**

```perl
# Opening a file in read mode
# to display existing content 
open(FH, "Hello.txt") or 
     die "Sorry!! couldn't open";

# Reading and printing the existing
# content of the file
print"\nExisiting Content of the File:\n";
while(<FH>)
{
    print $_;
}

# Opening file in append mode
# using >>
open(FH, ">>", "Hello.txt") or 
die "File couldn't be opened";

# Getting the text to be appended 
# from the user
print "\n\nEnter text to append\n";
$a = <>;

# Appending the content to file
print FH $a;

# Printing the success message
print "\nAppending to File is Successful!!!\n";

# Reading the file after appending
print "\nAfter appending, Updated File is\n";

# Opening file in read mode to 
# display updated content
open(FH, "Hello.txt") or 
     die "Sorry!! couldn't open";
while(<FH>)
{
    print $_;
}
close FH or "couldn't close";
```

**原始文件:**

![](img/a33a6f726496227b2711988460857ecd.png)

**追加到文件:**

![](img/8a60408fff503b652c8fb8836ddee130.png)
**更新文件:**

![](img/ff55a7b13bc91af2e7054135986ae3e3.png)

下面是程序的工作原理:-
步骤 1:以读取模式打开文件，查看文件的现有内容。
第二步:打印文件的已有内容。
第三步:在追加模式下打开文件，向文件中添加内容。
第四步:从用户处获取要追加到文件中的文本
第五步:向文件中追加文本
第六步:再次读取文件，查看更新内容。
第 7 步:关闭文件