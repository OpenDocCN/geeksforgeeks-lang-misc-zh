# Perl | chomp()函数

> 原文:[https://www.geeksforgeeks.org/perl-chomp-function/](https://www.geeksforgeeks.org/perl-chomp-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 chomp()函数用于从输入字符串中删除最后一个尾随换行符。

> **语法:** chomp(字符串)
> 
> **参数:**
> **字符串:**要删除尾随换行符的输入字符串
> 
> **返回:**从其所有参数中删除的尾随换行符总数

**例 1:**

```perl
#!/usr/bin/perl

# Initialising a string
$string = "GfG is a computer science portal\n";

# Calling the chomp() function
$A  = chomp($string);

# Printing the chopped string and 
# removed trailing newline character
print "Chopped String is : $string\n";
print "Number of Characters removed : $A";
```

**Output:**

```perl
Chopped String is : GfG is a computer science portal
Number of Characters removed : 1

```

在上面的代码中，可以看到输入字符串包含一个换行符(\n)，该换行符被 chomp()函数删除。

**例 2:**

```perl
#!/usr/bin/perl

# Initialising two strings
$string1 = "Geeks for Geeks\n\n";
$string2 = "Welcomes you all\n";

# Calling the chomp() function
$A  = chomp($string1, $string2);

# Printing the chopped string and 
# removed trailing newline character
print "Chopped String is : $string1$string2\n";
print "Number of Characters removed : $A\n";
```

**Output:**

```perl
Chopped String is : Geeks for Geeks
Welcomes you all
Number of Characters removed : 2

```

在上面的代码中，可以看到输入字符串 1 包含两个换行符(\n\n)，其中只有最后一个换行符被 chomp()函数删除，第二个换行符被使用，这可以在输出中看到。