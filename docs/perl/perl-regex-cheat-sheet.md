# Perl | Regex 备忘单

> 原文:[https://www.geeksforgeeks.org/perl-regex-cheat-sheet/](https://www.geeksforgeeks.org/perl-regex-cheat-sheet/)

***[正则表达式](https://www.geeksforgeeks.org/perl-regular-expressions/)*** 是 [**Perl**](https://www.geeksforgeeks.org/introduction-to-perl/) 编程的重要组成部分。它用于搜索指定的文本模式。在这种情况下，一组字符一起构成了搜索模式。又称 ***regexp*** 。当用户学习正则表达式时，可能需要快速查看那些他不常使用的概念。为了提供这种便利，创建了一个包含不同类、字符、修饰符等的正则表达式备忘单。用于正则表达式中。

#### [字符类](https://www.geeksforgeeks.org/perl-regex-character-classes/)

[字符类](https://www.geeksforgeeks.org/perl-regex-character-classes/)用于匹配字符串。这些类允许用户匹配任何范围的字符，而用户事先并不知道这些字符。

| 班级 | 说明 |
| [abc。] | 它只包含指定字符中的一个，即“a”、“b”、“c”或“.” |
| [a-j] | 它包括从 a 到 j 的所有字符。 |
| [a-z] | 它包括从 a 到 z 的所有小写字符。 |
| [^az] | 它包括除 a 和 z 以外的所有字符。 |
| \w | 它包括像[a-z，a-z，0-9]这样的所有字符 |
| \d | 它匹配像[0-9]这样的数字 |
| [ab][^cde] | 匹配的是字符 a 和 b 后面不应该跟 c、d 和 e。 |
| \s | 它与[\f\t\n\r]匹配，即表单提要、制表符、换行符和回车符。 |
| \W | 的补码 |
| \D | \d 的补码 |
| \S | \s 的补码 |

**示例:**

```perl
# Perl program to demonstrate
# character class

# Actual String
$str = "45char";

# Prints match found if 
# its found in $str
# by using \w
if ($str =~ /[\w]/)
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

```perl
Match Found
```

#### 锚

锚点根本不匹配任何字符。相反，它们匹配字符之前、之后或之间的特定位置。

| 锚 | 说明 |
| ^ | 它匹配字符串的开头。 |
| $ | 它在字符串的末尾匹配。 |
| \b | 它在从\w 到\W 的字符串的单词边界匹配。 |
| \A | 它匹配字符串的开头。 |
| \Z | 它在字符串的结尾或换行符之前匹配。 |
| \z | 它只在字符串的末尾匹配。 |
| \G | 它在指定的位置位置()匹配。 |
| \p{…。} | Unicode 字符类，如 IsLower、IsAlpha 等。 |
| \P{…。} | Unicode 字符类的补充 |
| [:类:] | 像数字、小写、ascii 等字符类。 |

**示例:**

```perl
# Perl program to demonstrate
# use of anchors in regex

# Actual String
$str = "55";

# Prints match found if 
# its found in $str
# using Anchors / 
if ($str =~ /[[:alpha:]]/)
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

```perl
Match Not Found
```

#### 元字符

元字符用于匹配 Perl 正则表达式中的模式。所有的元字符必须是*转义的*。

| 特性 | 说明 |
| ^ | 检查字符串的开头。 |
| $ | 检查字符串的结尾。 |
| 。 | 除换行符以外的任何字符。 |
| * | 匹配 0 次或更多次。 |
| + | 匹配 1 次或更多次。 |
| ？ | 匹配 0 次或更多次。 |
| () | 用于分组。 |
| \ | 用于引号或特殊字符。 |
| [] | 用于字符集。 |
| {} | 用作重复修饰语。 |

#### 量词

这些用于检查特殊字符。量词有三种类型

*   **'？'**匹配 0 或 1 个字符。
*   **'+'** 匹配一个或多个出现的字符。
*   **' ***匹配字符出现次数为 0 或更多。

| 使用量词 | 说明 |
| a？ | 它检查“a”是出现 0 次还是 1 次。 |
| a+ | 它检查“a”是否出现 1 次或更多次 |
| a* | 它检查“a”是否出现 0 次或更多次 |
| {2，6} | 它检查“a”是否出现 2 到 6 次 |
| {2，} | 它检查“a”是否出现 2 到无限次 |
| {2} | 它检查“a”是否出现两次。 |

**示例:**

```perl
# Perl program to demonstrate
# use of quantifiers in regex

# Actual String
$str = "color";

# Prints match found if 
# its found in $str
# using quantifier ?
if ($str =~ /colou?r/)
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

```perl
Match Found
```

#### 修饰语

| 修饰语 | 说明 |
| \g | 它用于替换所有出现的字符串。 |
| \gc | 它允许在匹配失败后继续搜索。 |
| \s | 它将字符串视为一行。 |
| 我 | 它关闭了区分大小写。 |
| \x | 它忽略了所有的空白。 |
| (?#文本) | 它用于在代码中添加注释。 |
| (?:模式) | 它用于匹配非捕获组的模式。 |
| (?&#124;模式) | 它用于匹配分支测试的模式。 |
| (?=模式) | 它用于积极的前瞻断言。 |
| (?！模式) | 它用于否定的前瞻断言。 |
| (< =模式) | 它用于断言后面的肯定的外观。 |
| ( | 它用于断言后面的否定的外观。 |

#### 空白修饰符

| 修饰语 | 说明 |
| \t | 用于插入制表符空间 |
| \r | 回车符 |
| \n | 用于插入新行。 |
| \h | 用于插入水平空白。 |
| \v | 用于插入垂直空白。 |
| \L | 用于小写字符。 |
| \U | 用于大写字符。 |

#### 量词–修饰语

| 最高的 | 最小的 | 说明 |
| ？ | ？？ | 它可以出现 0 或 1 次 |
| + | +? | 它可以出现 1 次或更多次。 |
| * | *? | 它可以出现 0 次或更多次。 |
| {3} | {3}? | 必须精确匹配 3 次。 |
| {3, } | {3, }? | 必须至少匹配 3 次。 |
| {3, 7} | {3, 7}? | 必须匹配至少 3 次但不超过 7 次。 |

#### 分组和捕获

在正则表达式内部，这些组用' \1 '表示，在正则表达式外部，这些组用' $1 '表示。这些组可以通过变量赋值来获取，在列表上下文中称为*捕获*。分组结构 *(…)* 创建称为*捕获缓冲区*的捕获组。

| (…) | 这些用于分组和捕获。 |
| \1, \2, \3 | 在正则表达式匹配期间，这些用于捕获缓冲区。 |
| $1, $2, $3 | 在成功匹配期间，这些用于捕获变量。 |
| (?:…) | 这些用于分组而不捕获。(这些既没有设置这$1 也没有设置\1) |