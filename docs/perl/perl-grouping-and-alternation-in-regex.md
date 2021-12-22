# Perl | Regex 中的分组和交替

> 原文:[https://www . geesforgeks . org/perl-group-and-alternation-in-regex/](https://www.geeksforgeeks.org/perl-grouping-and-alternation-in-regex/)

***[正则表达式](https://www.geeksforgeeks.org/perl-regular-expressions/)*** 是 [**Perl**](https://www.geeksforgeeks.org/introduction-to-perl/) 编程的重要组成部分。它用于搜索指定的文本模式。在这种情况下，一组字符一起构成了搜索模式。又称 ***regexp*** 。随着功能的增加，使用正则表达式可能会变得越来越复杂。为了降低复杂性，Perl 为我们提供了更多的操作，如交替和分组。

### 间隔

这个名字本身就暗示了它的机制，首先也是最重要的，它像一个出现在“C”编程语言中的(&&)运算符。C 语言中的' && '运算符的工作原理是，直到它发现所有的条件语句都为真，它才返回 1，一旦发现假语句，它就返回 0。Perl 中的交替以两种方式同时工作。可以使用元字符“|”或“[]”进行替换。下面的例子将使事情变得清楚:

**例 1:**

```perl
#!/usr/bin/perl

# Initializing the string and checking it
# against few search patterns
my $str = "geeksforgeeks rocks...";

# prints 1 due to no match (=0)
print "1\n" if (($str =~ /gek|foor/) == 0); 

# for word search
if($str =~ /geek|for/) 
{
    print "I found {content}amp;.\n";
}
else
{
    print "no match"
}
```

**Output:**

```perl
1
I found geek.

```

因此，在上面的例子中，它首先检查“极客”，并在第一个替换模式中找到匹配项，一旦找到匹配项，就返回 1。但是它也会检查“for ”,如果它不在字符串中，它也不会被打扰，因为它已经返回了匹配状态。如果“for”匹配，它将检查“for”是否出现在字符串的最少位置，因为“geeks”中的“g”出现在位置 0，“for”中的“f”出现在位置 5，“geeks”存储在最后一个匹配模式中。查看以下示例:

```perl
 {content}amp; - Contains the string matched by the last pattern match.
```

**例 2:**

```perl
#!/usr/bin/perl

# Initializing the string and checking it
# against few search patterns
my $str = "geeksforgeeks rocks...";
print "1\n" if ($str =~ /for|eeks|rock|ge/);

# | for word search
if($str =~ /for|eeks|rock|ge/)
{
    print "I found {content}amp;.\n";
}

# for single character search
if ($str =~ /[gfrkc]/)
{
    print "{content}amp;"
}
```

**Output:**

```perl
1
I found ge.
g

```

### 分组

分组用于搜索以相似单词或模式为界限的模式，在开头、结尾或中间，它还返回位置最少的模式。分组使用元字符“()”完成。下面是一个能让事情变得清楚的例子:
**例子 1:**

```perl
#!/usr/bin/perl
# Initializing the string and checking it
# against few search patterns
my $str = "Blackbackground Brownbackground";
print "1\n" if ($str =~ /(Bron|Back)[a-z]+/);
if ($str =~ /(Brown|Black)[a-z]+/)
{
    print "I found {content}amp;.\n";
}

else
{
    print "no match"
}
```

**Output:**

```perl
I found Blackbackground.

```

为了更好地理解，请查看以下示例:

```perl
#!/usr/bin/perl
use warnings;
use strict;

# Initializing the string and checking it
# against few searching patterns

# array of strings
my @mail = ('Ab-@gmail.com',
            'd.f@yahoo.com',
            '0b_f@bing.com',
            'jet@hotmail.con',
            's/s@otmail.com');

for(@mail)
{
    # search pattern to check valid mail 
    # service providers followed with '.com'
    print "Valid : $_\n" 
    if($_ =~ /[a-zA-Z0-9-._]+@(gmail|yahoo|bing|hotmail)(.com)$/)
}
```

**Output:**

```perl
Valid : Ab-@gmail.com
Valid : d.f@yahoo.com
Valid : 0b_f@bing.com

```