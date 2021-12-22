# Perl |退出脚本

> 原文:[https://www.geeksforgeeks.org/perl-exiting-from-a-script/](https://www.geeksforgeeks.org/perl-exiting-from-a-script/)

exit()函数计算传递给它的表达式，并从 Perl 解释器中退出，同时将该值作为退出值返回。exit()函数并不总是立即退出，而是在终止程序之前调用结束例程。如果没有表达式传递给退出函数，则返回默认值 0。exit()函数的使用是有限的，不应用于从子程序退出。要退出子程序，使用 die 或 return。

> **语法:**退出(值)
> 
> **参数:**函数调用时返回的值
> 
> **返回:**传递给它的值，如果在没有参数的情况下调用函数，则返回 0

**示例:**

```
# Getting the user's bid for
# an online auction
print "Enter your bid";
$bid = <STDIN>;

# Exit function returns $bid
# if bid is less than 1000
if ($bid < 1000)
{
    exit $bid;
}

else
{
    # Prints this message if bid is 
    # greater than or equal to 1000
    print "\nThanks for Participating";
}
```

以上代码是如何工作的
**第一步:**从用户那里获取一个出价值。
**第二步:**如果出价低于 1000，退出返回出价值并终止程序。
**步骤 3:** 如果出价大于或等于 1000，则打印此消息。

**将参数传递给退出函数**
可以将参数传递给退出函数，该参数存储在系统变量中。

**注意:**传递给退出函数的值可以是任意随机值，不需要是任何特定值。
下面的示例显示了如何将值传递给退出函数:
**示例:**

```
# Opening a file
if(!open(fh,"<","Filename.txt"))
{
    # This block passing an error code 56 
    # to exit function indicating file 
    # could not be opened.
    print "Could not open file";
    exit 56;
}

# Passing a success code 1 to 
# the exit function
exit 1;
```

![](img/04ca203e4ddeba71055c5667e1390ea1.png)

以下是上述程序的工作原理:-
**步骤 1:** 以读取模式打开文件。
**步骤 2:** 当无法打开文件时，如果 block 执行，则调用退出函数，并将错误代码值 56 传递给系统。
**步骤 3:** 如果打开文件成功，则返回 1。

为了查看 Linux/Unix 上退出函数返回的值 **$？使用**。**呼应$？**在终端上执行，以便查看退出功能返回的值。