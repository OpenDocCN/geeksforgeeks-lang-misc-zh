# Perl | Regex 中的锚点

> 原文:[https://www.geeksforgeeks.org/perl-anchors-in-regex/](https://www.geeksforgeeks.org/perl-anchors-in-regex/)

Perl [Regex](https://www.geeksforgeeks.org/perl-regular-expressions/) 中的锚点根本不匹配任何字符。相反，它们匹配字符之前、之后或之间的特定位置。这些用于检查的不是字符串，而是它的位置边界。
以下是 Perl 正则表达式中的各个锚点:

```perl
'^' '{content}apos;, '\b', '\A', '\Z', '\z', '\G', '\p{....}', '\P{....}', '[:class:]'
```

**^或\A** :匹配字符串开头的模式。

> **语法:** (/^pattern/，/\Apattern/)。

**示例:**

```perl
#!/usr/bin/perl
$str = "guardians of the galaxy";

# prints the pattern as it is
# starting with 'guardians'
print "{content}amp;\n" if($str =~ /^guardians/);

# prints the pattern 'gua'
print "{content}amp;\n" if($str =~ /\Agua/);

# prints nothing because 
# the 0th position doesn't start with 'a'
print "{content}amp;" if($str =~ /^ans/)
```

**Output:**

```perl
guardians
gua

```