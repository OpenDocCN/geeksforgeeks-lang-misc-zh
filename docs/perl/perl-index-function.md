# Perl | index()函数

> 原文:[https://www.geeksforgeeks.org/perl-index-function/](https://www.geeksforgeeks.org/perl-index-function/)

此函数返回给定子串(或模式)在字符串(或文本)中第一次出现的位置。我们可以指定开始位置。默认情况下，它从开始搜索(即从索引零开始)。

> **语法:**
> #从给定索引
> 索引(文本、段落、索引)中搜索段落
> 
> #在文本中搜索拍子
> 索引(文本，拍子)
> 
> **参数:**
> 
> *   **文本**:要搜索子串的字符串。
> *   **pat** :要搜索的子串。
> *   **索引**:起始索引(由用户设置或默认取零)。
> 
> **失败时返回:**
> -1，否则返回匹配字符串的位置。

**例 1:**

```
#!/usr/bin/perl

# String from which Substring 
# is to be searched 
$string = "Geeks are the best";

# Using index() to search for substring
$index = index ($string, 'the');

# Printing the position of the substring
print "Position of 'the' in the string: $index\n";
```

**Output:**

```
Position of 'the' in the string: 10

```

**例 2:**

```
#!/usr/bin/perl

# String from which Substring 
# is to be searched 
$string = "Geeks are the best";

# Defining the starting Index
$pos = 3;

# Using index() to search for substring
$index = index ($string, 'Geeks', $pos);

# Printing the position of the substring
print "Position of 'Geeks' in the string: $index\n";
```

**Output:**

```
Position of 'Geeks' in the string: -1

```

这里，在第二个例子中，位置被设置为“3”，即从第三个位置开始搜索的起始索引。因此，在字符串中找不到子字符串。