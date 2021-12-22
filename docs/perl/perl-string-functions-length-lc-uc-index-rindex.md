# Perl | String 函数(长度、lc、uc、index、rindex)

> 原文:[https://www . geesforgeks . org/perl-string-functions-length-LC-UC-index-rindex/](https://www.geeksforgeeks.org/perl-string-functions-length-lc-uc-index-rindex/)

Perl 中的字符串是包含在某些类型的引号中的字符序列。Perl 字符串可以包含 UNICODE、ASCII 和转义序列字符。Perl 像任何其他编程语言一样，提供各种函数来操作字符串。Perl 的一些字符串函数如下:

*   长度()
*   lc()
*   uc()
*   索引()
*   rindex()

**length():** 这个函数用于查找字符串中的字符数。这个函数返回字符串的长度。下面是说明这种方法的程序。

*   **Example 1:**

    ```
    # Perl program to demonstrate 
    # string length function

    # string
    my $s = "geeksforgeeks";

    # using length function &
    # displaying length
    print(length($s),"\n"); 
    ```

    **输出:**

    ```
    13

    ```

*   **Example 2:**

    ```
    # Perl program to demonstrate 
    # string length function

    # string
    my $s = "#$%HeLLo CSHARP &+#*";

    # using length function &
    # displaying length
    print(length($s),"\n");  
    ```

    **输出:**

    ```
    19

    ```

**lc():** 这个函数返回字符串的小写版本。下面是说明这种方法的程序。

*   **Example 1:**

    ```
    # Perl program to demonstrate 
    # string lc function

    # string
    my $s = "GEEKSFORGEEKS\n";

    # using lc function &
    # displaying result
    print("To lower case: ");
    print(lc($s),"\n");
    ```

    **输出:**

    ```
    To lower case: geeksforgeeks

    ```

*   **Example 2:**

    ```
    # Perl program to demonstrate 
    # string lc function

    # string
    my $s = "GEEKS\n";

    # using lc function &
    # displaying result
    print("To lower case: ");
    print(lc($s),"\n");
    ```

    **输出:**

    ```
    To lower case: geeks

    ```

**uc():** 这个函数返回字符串的大写版本。下面是说明这种方法的程序。

*   **Example 1:**

    ```
    # Perl program to demonstrate 
    # string uc function

    # string
    my $s = "geeksforgeeks";

    # using uc function &
    # displaying result
    print("To Upper Case: ");
    print(uc($s),"\n");
    ```

    **输出:**

    ```
    To Upper Case: GEEKSFORGEEKS

    ```

*   **Example 2:**

    ```
    # Perl program to demonstrate 
    # string uc function

    # string
    my $s = "GeekS\n";

    # using uc function &
    # displaying result
    print("To Upper Case: ");
    print(uc($s),"\n");
    ```

    **输出:**

    ```
    To Upper Case: GEEKS

    ```

**index():** 此方法将从字符串中的指定位置搜索子字符串，并返回子字符串在字符串中第一次出现的位置。如果位置被省略，它将从字符串的开头开始搜索。此方法将采用两个参数，即原始字符串和必须搜索的子字符串。

**示例:**

```
# Perl Program to illustrate 
# the index() function

# !/usr/bin/perl
use warnings;
use strict;

# string
my $st = "GeeksforGeeks\n";

# substring
my $subs = "for";

# using index function
my $r = index($st, $subs);

# displaying result
print(qq\The substring $subs found at position $r in string $st\);
```

**输出:**

```
The substring for found at position 5 in string GeeksforGeeks

```

**rindex()** 该函数与 index()相同，只是它返回字符串中最后一次出现的文本。此外，可以给出第三个参数，该参数返回该位置之前或该位置处的位置。它从字符串的末尾开始搜索，而不是从开头开始搜索。下面是说明这种方法的程序。

**例 1:**

```
# Perl Program to illustrate 
# the rindex() function

# !/usr/bin/perl
use warnings;
use strict;

# string
my $st = "GeeksforGeeks\n";

# substring
my $subs = "for";

# using rindex function
my $r = rindex($st, $subs);

# displaying result
print(qq\The substring $subs found at position $r in string $st\);
```

**输出:**

```
The substring for found at position 5 in string GeeksforGeeks

```

**例 2:**

```
# Perl Program to illustrate 
# the rindex() function with 
# three parameters

# !/usr/bin/perl

# using rindex() function 
$p = rindex("GeeksForGFGGeeksgeeksforGFG", "GFG");

print "Founded position of GFG $p\n";

# Use the first position found 
# as the offset to the next search.
# The length of the target string
# is subtracted from the offset 
# to save time.
$p = rindex("GeeksForGFGGeeksgeeksforGFG", "GFG", $p-7);
print "Founded position of GFG $p\n";
```

**输出:**

```
Founded position of GFG 24
Founded position of GFG 8

```