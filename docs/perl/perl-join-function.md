# Perl | join()函数

> 原文:[https://www.geeksforgeeks.org/perl-join-function/](https://www.geeksforgeeks.org/perl-join-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 join()函数使用 VAR 的值将 LIST 的元素组合成单个字符串来分隔每个元素。这实际上是分裂的对立面。

请注意，VAR 仅放置在列表中的元素对之间；它不会放在字符串的第一个元素之前或最后一个元素之后。请提供一个空字符串而不是 undef，以便在没有分隔符的情况下将字符串连接在一起。

> **语法:**连接(VAR，LIST)
> 
> **参数:**
> 
> *   **VAR :** 要放在列表元素之间的分隔符。
> *   **列表:**要转换为字符串的列表。
> 
> **返回:**返回连接的字符串

**例 1:**

```perl
#!/usr/bin/perl

# Joining string with a separator
$string = join( "-", "Geeks", "for", "Geeks" );
print"Joined String is $string\n";

# Joining string without a separator
$string = join( "", "Geeks", "for", "Geeks" );
print"Joined String is $string\n";
```

 **输出:**

```perl
Joined String is Geeks-for-Geeks
Joined String is GeeksforGeeks

```

**例 2:**

```perl
#!/usr/bin/perl

# Joining string with '~' separator
$string = join( "~", "Geeks", "for", "Geeks" );
print"Joined String is $string\n";

# Joining string with '***' separator
$string = join( "***", "Geeks", "for", "Geeks" );
print"Joined String is $string\n";
```

**输出:**

```perl
Joined String is Geeks~for~Geeks
Joined String is Geeks***for***Geeks
```