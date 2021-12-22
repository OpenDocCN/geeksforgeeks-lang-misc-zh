# Perl |引用、插值和转义字符串

> 原文:[https://www . geeksforgeeks . org/perl-引号内插和转义字符串/](https://www.geeksforgeeks.org/perl-quoted-interpolated-and-escaped-strings/)

Perl 中的字符串是一个标量变量，以($)符号开头，它可以包含字母、数字和特殊字符。字符串可以由一个单词、一组单词或多行段落组成。字符串由用户在单引号(')或双引号(")中定义。

**Quoted Strings**

在 Perl 中，字符串可以放在双引号(" ")之间或单引号(')之间。但是，单引号中定义的字符串和双引号中定义的字符串被区别对待。
**双引号字符串:**
双引号字符串被内插，即变量名(标量、数组和哈希值)被其原始值和转义序列(如/t、/n 等)替换。)做他们的工作。
也可以用 qq 操作符代替双引号字符串。
**单引号字符串:**
单引号字符串不插值。它们被解释为是，没有任何修改。Perl 中的 q 运算符提供了与单引号字符串相同的用途。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# An array of integers from 1 to 10
@list = (1..10);

# Non-interpolated string
$strng1 = 'Using Single quotes: @list';

# Interpolated string
$strng2 = "Using Double-quotes: @list";
print("$strng1\n$strng2");
```

**Output:** 

```perl
Using Single quotes: @list 
Using Double-quotes: 1 2 3 4 5 6 7 8 9 10
```

**Interpolation of Strings**

使用双引号对字符串进行插值有时会变得棘手，因为某些字符串包含的符号在插值时可能没有任何用处。例如:写电子邮件地址时使用的“@”符号。当电子邮件地址要存储在双引号字符串中时，会自动插入‘(@)符号，并将其作为数组名称的开头，然后用它替换。如果找到具有该名称的数组，则它将用数组值替换数组名称，或者如果不存在具有该名称的数组，则它将保留空白。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Assigning a variable with an email address
# using double-quotes
$email = "GeeksforGeeks0402@gmail.com";

# Printing the interpolated string
print($email);
```

**Output:** 

```perl
GeeksforGeeks0402.com
```

在上面的例子中，字符串($email)被内插，@gmail 被一个名为“@gmail”的数组替换，但是由于没有找到同名的数组，@gmail 被删除但没有被替换，因此打印了“GeeksforGeeks0402.com”。
在下面的例子中，@gmail 已经被预定义，因此被替换为@gmail。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Pre-defining the array
@gmail = (a..g);

# Assigning a variable with an email
# address using double-quotes
$email = "GeeksforGeeks0402@gmail.com";

# Printing the interpolated string
print($email);
```

**Output:** 

```perl
GeeksforGeeks0402a b c d e f g.com
```

这可以通过用单引号代替双引号来纠正。使用单引号将字符串赋给变量会删除插值，因此“@”不会被视为数组声明。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Assigning a variable with an email address
# using single-quotes
$email = 'GeeksforGeeks0402@gmail.com';

# Printing the non-interpolated string
print($email);
```

**Output:** 

```perl
GeeksforGeeks0402@gmail.com
```

上述插值问题的解决方案有一个缺点。如果需要用‘@’符号替换字符串中的变量值，该怎么办。那么这个方法就没有用了，因为单引号不允许替换变量的值。为了避免这种情况，使用了转义字符，即反斜杠(\)。反斜杠就插在“@”的前面，如下所示:

## Perl 语言

```perl
#!/usr/bin/perl

# Assigning a variable with an email
# address using double-quotes
# Note: Using '\' to escape the
# interpolation of '@'
$email = "GeeksforGeeks0402\@gmail.com";

# Printing the interpolated string
print($email);

# variable to be substituted
$name = "GeeksforGeeks";

# variable to store the string
$email2 = "\n$name\@gmail.com";

# Printing the interpolated string
print($email2);
```

**Output:** 

```perl
GeeksforGeeks0402@gmail.com
GeeksforGeeks@gmail.com
```

**Escaping the escape character**

反斜杠是转义字符，用于使用转义序列。当需要在插入的字符串中插入转义字符时，使用相同的反斜杠，以转义替换为“(空白)”的转义字符。这允许在内插字符串中使用转义字符。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Using Two escape characters to avoid
# the substitution of escape(\) with blank
$string1 = "Using the escape(\\) character";

# Printing the Interpolated string
print($string1);
```

**Output:** 

```perl
Using the escape(\) character
```

**Escaping double quotes**

在字符串中使用双引号表示字符串结束，因此不能直接插入。要在插入的字符串中插入双引号，在双引号之前使用反斜杠来转义其插入。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Escaping double-quotes with '\'
$string = "This page is \"Geeks For Geeks\".";

# Printing the interpolated string
print($string);
```

**Output:** 

```perl
This page is "Geeks For Geeks".
```