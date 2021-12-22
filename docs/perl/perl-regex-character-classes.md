# Perl | Regex 字符类

> 原文:[https://www.geeksforgeeks.org/perl-regex-character-classes/](https://www.geeksforgeeks.org/perl-regex-character-classes/)

字符类用于匹配字符串。这些类允许用户匹配任何范围的字符，而用户事先并不知道这些字符。要匹配的字符集总是写在**方括号[]** 之间。一个字符类总是与一个字符完全匹配。如果没有找到匹配，那么整个正则表达式匹配失败。

**示例:**

> 假设你有很多像 **#g#** 、 **#e#** 、 **#k#** 、 **#k#** 、 **#s#** 、 **#这样的弦。#** 或 **#@#** 您必须匹配一个 **#** 字符，该字符后跟“ **g** ”、“ **e** ”、“ **k** ”、“ **s** ”、“**”。**'，或' **@** '，后面跟着另一个 **#** 字符，然后尝试 regex **/[#geeks@。#]/** 符合要求。它将以 **#** 开始匹配，然后匹配 **[]** 中的任意字符，之后匹配另一个 **#** 。此正则表达式将不匹配“ **##** ”或“ **#ge#** ”或“ **#gg#** ”等。因为如前所述，字符类总是在两个“ **#** ”字符之间恰好匹配一个字符。

**要点:**

*   点(。)在字符类内部，失去了它的特殊意义即“*除了换行符*之外的一切”。
*   点(。)可以匹配单个点(。)仅在字符类中。
*   大多数特殊字符在字符类中失去了它们的特殊意义，但是有一些字符在字符类中获得了一些特殊意义。

**示例:**

```
# Perl program to demonstrate
# character class

# Actual String
$str = "#g#";

# Prints match found if 
# its found in $str
if ($str =~ /[#geeks@.#]/)
{
    print "Match Found\n";
}

# Prints match not found 
# if it is not found in $str
else
{
    print "Match Not Found\n";
}
```

**输出:**

```
Match Found
```

**字符类中的范围:**要匹配一长串字符非常难键入，因为用户可能会跳过一两个字符。因此，为了使任务变得容易，我们将使用范围。通常，破折号(-)用于指定范围。

**示例:**

```
To specify range [abcdef] you can use /[a-f]/
```

**要点:**

*   使用 **-(破折号)符号指定范围。**
*   用户还可以组合多种字符、数字等。比如[0-9a-gA-g]。这里的“**–**”允许用户取范围内指定的任意数量的字符或数字
*   如果用户想要在给定的字符串中匹配破折号(-)那么他可以简单地将其放在**方括号[]** 之间。
*   要匹配字符串中的右方括号，只需在它前面加上 **\** ，即 **\]** ，并将其放在**方括号[]** 之间。

**示例:**

```
# Perl program to demonstrate
# range in character class

# Actual String
$str = "61geeks";

# Prints match found if 
# its found in $str
# using range
if ($str =~ /[0-7a-z]/) 
{
    print "Match Found\n";
}

# Prints match not found 
# if its not found in $str
else
{
    print "Match Not Found\n";
}
```

**输出:**

```
Match Found
```

**否定字符类:**要否定字符类，只需使用 **caret(^)** 符号。它将否定符号后的指定字符，甚至是一个范围。如果您将插入符号(^)作为字符类中的第一个字符，这意味着字符类可以匹配除字符类中提到的字符之外的任何一个字符。

**示例:**

```
# Perl program to demonstrate
# negated character class

# Actual String
$str = "geeks56";

# using negated character class
# Prints match found if 
# its found in $str
if ($str =~ /[^geeks0-7]/) 
{
    print "Match Found\n";
}

# Prints match not found 
# if its not found in $str
else
{
    print "Match Not Found\n";
}
```

**输出:**

```
Match Not Found
```