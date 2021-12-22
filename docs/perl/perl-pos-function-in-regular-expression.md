# 正则表达式中的 Perl | pos()函数

> 原文:[https://www . geesforgeks . org/perl-pos-function-in-正则表达式/](https://www.geeksforgeeks.org/perl-pos-function-in-regular-expression/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 **pos()** 函数用于使用 Regex 中的“m”修饰符返回最后一场比赛的位置。
pos 函数可以和 Regex 中的字符类一起使用，返回给定字符串中所有需要的子字符串位置的列表。全局运算符“g”也可以与“m”修饰符一起使用，在整个文本中搜索子字符串。

> **语法:** pos(字符串)
> **参数:**应用正则表达式
> **后的字符串返回:**匹配子字符串
> 的位置

**示例 1:** 使用子字符串

## Perl 语言

```perl
#!/usr/bin/perl

# Program to print position of a substring
$String = "Geeks For Geeks";

print" Position of 'G' in string:\n";

# Regex to search for substring
# using m modifier
while($String =~ m/G/g)
{

    # Finding the position of substring
    # using pos() function
    $position = pos($String);
    print "$position\n";
}
```

**Output:** 

```perl
Position of 'G' in string:
1
11
```

**示例 2:** 使用角色类

## Perl 语言

```perl
#!/usr/bin/perl

# Program to print position of a substring
$String = "Geeks For Geeks";

print "Position of all Uppercase characters:\n";

# Regex to search for
# all the upper case characters
# using character class
while($String =~ m/[A-Z]/g)
{

    # Finding the position of substring
    # using pos() function
    $position = pos($String);
    print "$position, ";
}

print "\nPosition of all Lowercase characters:\n";

# Regex to search for
# all the lower case characters
# using character class
while($String =~ m/[a-z]/g)
{

    # Finding the position of substring
    # using pos() function
    $position = pos($String);
    print "$position, ";
}
```

**Output:** 

```perl
Position of all Uppercase characters:
1, 7, 11, 
Position of all Lowercase characters:
2, 3, 4, 5, 8, 9, 12, 13, 14, 15,
```

**例 3:** 空间位置

## Perl 语言

```perl
#!/usr/bin/perl

# Program to print position of a substring
$String = "Geeks For Geeks";

# Regex to search for
# all the spaces
while($String =~ m/\s/g)
{

    # Finding the position of substring
    # using pos() function
    $position = pos($String);
    print "$position\n";
}
```

**Output:** 

```perl
6
10
```

**使用\G 断言从指定位置匹配:**
**\ G**Perl Regex 中的断言用于匹配从 pos()函数指定的位置开始的子串，直到 Regex 中指定的匹配字符。这将返回由“m”修饰符指定的字符的第一次出现的位置。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining the default string
$_ = "Geeks World is the best";

# Terminating character
# using m modifier
m/o/g;

# Specifying the starting position
$position = pos();

# Using \G Assertion
m/\G(.*)/g;

# Printing the position
# and the remaining string
print "$position $1";
```

**Output:** 

```perl
8 rld is the best
```

在上面的示例中，匹配子字符串的第一次出现的位置与剩余的字符串一起打印。如果需要为匹配字符的下一次出现重新开始计数位置，只需将$1 中的剩余字符串存储到默认字符串中。
**例:**

## Perl 语言

```perl
#!/usr/bin/perl

# Defining the default string
$_ = "Geeks World is the best among all";

# Terminating character
# using m modifier
m/o/g;

# Specifying the starting position
$position = pos();

# Using \G Assertion
m/\G(.*)/g;

# Printing the position
# and the remaining string
print "$position $1\n";

# To start counting from the matched character
# until the next possible match
$_ = $1;
m/o/g;

$position = pos();

# Using \G Assertion
m/\G(.*)/g;

# Printing the position
# and the remaining string
print "$position $1\n";
```

**Output:** 

```perl
8 rld is the best among all
19 ng all
```