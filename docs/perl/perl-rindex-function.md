# Perl | rindex()函数

> 原文:[https://www.geeksforgeeks.org/perl-rindex-function/](https://www.geeksforgeeks.org/perl-rindex-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 rindex()函数的操作类似于 [index()](https://www.geeksforgeeks.org/perl-index-function/) 函数，只是它返回字符串(或文本)中最后出现的子字符串(或模式)的位置。如果指定了位置，则返回该位置处或之前的最后一个匹配项。

> **语法:**
> #在给定位置的文本中搜索段落
> 索引文本、模式、位置
> 
> #在文本中搜索 pat
> 索引文本，模式
> 
> **参数:**
> 
> *   **文本:**要搜索子串的字符串。
> *   **pat:** 要搜索的子串。
> *   **索引:**起始索引(由用户设置或默认取零)。
> 
> **返回:**
> -1 表示故障，否则返回最后出现的位置。

**例 1:**

```
#!/usr/bin/perl -w

$pos = rindex("WelcomeToGeeksforGeeksWorld", "eks");
print "Position of eks: $pos\n";

# Use the first position found as the offset 
# to the next search.

# Note that the length of the target string is
# subtracted from the offset to save time.
$pos = rindex("WelcomeToGeeksforGeeksWorld", 
                          "eks", $pos - 3 );
print "Position of eks: $pos\n";
```

**Output:**

```
Position of eks: 19
Position of eks: 11

```

**例 2:**

```
#!/usr/bin/perl -w

$pos = rindex("GeeksforGeeks", "eks");
print "Position of eek: $pos\n";

# Use the first position found as the 
# offset to the next search.

# Note that the length of the target string is
# subtracted from the offset to save time.
$pos = rindex("GeeksForGeeks", "eks", $pos - 2);
print "Position of eek: $pos\n";
```

**Output:**

```
Position of eek: 10
Position of eek: 2

```