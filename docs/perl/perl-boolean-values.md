# Perl |布尔值

> 原文:[https://www.geeksforgeeks.org/perl-boolean-values/](https://www.geeksforgeeks.org/perl-boolean-values/)

在大多数编程语言中，真和假被认为是布尔值。但是 Perl 没有为“真”和“假”提供布尔类型。一般来说，当函数返回真或假时，程序员可以使用术语“布尔”。像条件语句(if，while 等。)将为标量值返回 true 或 false。

**例:**

## Perl

```
# Perl Code to demonstrate the boolean values

# variable assigned value 0
$k = 0;

# checking whether k is true or false
if ($k)
{
    print "k is True\n";
}
else
{
    print "k is False\n";
}

# variable assigned value 2
$m = 2;

# checking whether m is true or false
if ($m)
{
    print "m is True\n";
}
else
{
    print "m is False\n";
}
```

**输出:**

```
k is False
m is True
```

**真值:**在 Perl 语言中，除零之外的任何非零数字都是真值。字符串常量，如*“真”*、*“假”*、*“*”(以空格为字符的字符串)、*“00”*(2 个或更多个 0 字符)和*“0 \ n”*(字符串中的一个零后跟一个换行符)等。还要考虑 Perl 中的真值。

*   **Example:**

## Perl

```
# Perl Code to demonstrate the True values

# variable assigned value 5
$a = 5;

# checking whether a is true or false
if ($a)
{
    print "a is True\n";
}
else
{
    print "a is False\n";
}

# string variable assigned white
# space character
$b = ' ';

# checking whether b is true or false
if ($b)
{
    print "b is True\n";
}
else
{
    print "b is False\n";
}

# string variable assigned 'false'
# value to it
$c = 'false';

# checking whether c is true or false
if ($c)
{
    print "c is True\n";
}
else
{
    print "c is False\n";
}

# string variable assigned "0\n"
# value to it
$d = "0\n";

# checking whether d is true or false
if ($d)
{
    print "d is True\n";
}
else
{
    print "d is False\n";
}
```

**输出:**

```
a is True
b is True
c is True
d is True
```

**假值:** *空字符串*或 s *字符串包含单个数字 0* 或*unde*值和零被认为是 perl 中的假值。

*   **Example:**

## Perl

```
# Perl Code to demonstrate the False values

# variable assigned value 0
$a = 0;

# checking whether a is true or false
if ($a)
{
    print "a is True\n";
}
else
{
    print "a is False\n";
}

# string variable assigned empty string
$b = '';

# checking whether b is true or false
if ($b)
{
    print "b is True\n";
}
else
{
    print "b is False\n";
}

# string variable assigned undef
$c = undef;

# checking whether c is true or false
if ($c)
{
    print "c is True\n";
}
else
{
    print "c is False\n";
}

# string variable assigned ""
# value to it
$d = "";

# checking whether d is true or false
if ($d)
{
    print "d is True\n";
}
else
{
    print "d is False\n";
}
```

**输出:**

```
a is False
b is False
c is False
d is False
```

**注意:**对于用户必须比较两个不同变量的条件检查，如果它们不相等，则返回*假*否则返回*真*。

*   **Example:**

## Perl

```
# Perl Program demonstrate the conditional check

# variable initialized with string
$x = "GFG";

# using if statement
if ($x eq "GFG")
{
    print "Return True\n";
}
else
{
    print "Return False\n";
}
```

**输出:**

```
Return True
```