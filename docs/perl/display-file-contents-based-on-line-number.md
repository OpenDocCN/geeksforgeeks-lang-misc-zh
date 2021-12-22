# 根据行号显示文件内容

> 原文:[https://www . geesforgeks . org/display-file-contents-based-online-number/](https://www.geeksforgeeks.org/display-file-contents-based-on-line-number/)

编写一个 Perl 程序，根据命令行参数给出的行号，以排序顺序(升序)显示文件内容。请注意，行号可以是任何顺序，如果行号很大，就会抛出错误。

> **语法:** perl `**Filename.pl**` `**File_to_be_read.abc**` `**x y z**`
> 这里，
> **Filename.pl** 是包含 perl 脚本
> **File _ to _ be _ read . ABC**是要读取的文件的名称。该文件可以是任何类型。文字、脚本等。
> **x y z** 是要打印的行号。

**方法:**
对行号进行排序，不包括第一个参数，即文件名。一旦排序，使用单个语句 **(my @file = < FNAME > )** 将文件的全部内容读入数组。现在循环遍历排序后的行号，并通过将行号作为索引传递给文件数组来显示文件内容，如(**print " $ file[$ var-1]\ n "；**)。

**示例 1:** **考虑一个文件 Hello.txt**

```
#!/usr/bin/perl
use warnings;
use strict;

# Check if line numbers are given as an input
if (@ARGV < 2)
{
    die "usage: pick file_name line_no1 line_no2 ...";
}

open FNAME, $ARGV[0] or die "cannot open file";

# Exclude the first argument 
# for sorting line numbers
shift (@ARGV); 
my @line_numbers = sort { $a <=> $b } @ARGV; 

# Read whole file content into an array 
# and removes new line using chomp()
chomp (my @file = <FNAME>);

foreach my $var (@line_numbers) 
{
    if ($var> $#file)
    {
        print "Line number $var is too large\n";
        next;
    }
    print "$file[$var-1]\n";
}
close FNAME;
```

**输出:**
![](img/bd2cab9b547c25e3ded27cc5e9dbfb7c.png)

**例 2:** **读取同一个脚本文件**

```
#!/usr/bin/perl
use warnings;
use strict;

# Check if line numbers are given as an input
if (@ARGV < 2)
{
    die "usage: pick file_name line_no1 line_no2 ...";
}

open FNAME, $ARGV[0] or die "cannot open file";

# Exclude the first argument 
# for sorting line numbers
shift (@ARGV); 
my @line_numbers = sort { $a <=> $b } @ARGV; 

# Read whole file content into an array 
# and removes new line using chomp()
chomp (my @file = <FNAME>);

foreach my $var (@line_numbers) 
{
    if ($var> $#file)
    {
        print "Line number $var is too large\n";
        next;
    }
    print "$file[$var-1]\n";
}
close FNAME;
```

**输出:**
![](img/eaac8872c246769c1d71d69fa4d130f9.png)

**如果传递的行号不在文件中:**
![](img/daf011ee70c9acfaa1aebc42f2951662.png)