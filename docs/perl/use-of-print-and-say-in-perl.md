# 在 Perl 中使用 print()和 say()

> 原文:[https://www.geeksforgeeks.org/use-of-print-and-say-in-perl/](https://www.geeksforgeeks.org/use-of-print-and-say-in-perl/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 使用语句和表达式来评估由用户提供的或在代码中作为硬编码输入给出的输入。这个被求值的表达式不会显示给程序员，因为它已经在编译器中被求值了。为了显示这个求值的表达式，Perl 使用了`**print()**`函数和`**say()**`函数。这些函数可以将传递给它们的任何内容显示为参数。

### 打印()操作员–

Perl 中的 **[print](https://www.geeksforgeeks.org/perl-print-operator/)** 运算符用于打印作为参数传递给它的 List 中的表达式的值。Print 运算符打印作为参数传递给它的任何东西，无论它是字符串、数字、变量还是任何东西。双引号("")用作此运算符的分隔符。

**语法:**

```
print "";
```

**例:**

```
#!/usr/bin/perl -w 

# Defining a string 
$string1 = "Geeks For Geeks"; 
$string2 = "Welcomes you all";

print "$string1";
print "$string2";
```

**输出:**

```
Geeks For GeeksWelcomes you all

```