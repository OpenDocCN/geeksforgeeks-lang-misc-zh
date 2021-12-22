# Perl | split()函数

> 原文:[https://www.geeksforgeeks.org/perl-split-function/](https://www.geeksforgeeks.org/perl-split-function/)

***【split()】***是 [**Perl**](https://www.geeksforgeeks.org/introduction-to-perl/) 中的一个字符串函数，用来拆分或者你可以说是把一个字符串切成更小的段或者块。分割一个字符串有不同的标准，如单个字符、正则表达式、一组字符或未定义的值等..这个函数最大的优点是用户可以指定将字符串分成多少部分。

**语法:**

```perl
split /Pattern/, Expression, Limit

or

split /Pattern/, Expression

or

split /Pattern/

or

Split

```

在上面的语法中，**模式**被指定为一个正则表达式，它提供了拆分字符串的标准。**表情**是要被劈开的绳子。**极限**是一种限制，它阻止在字符串中发现的第(n-1)个模式的分裂。

**返回值:**该方法在**两个上下文**中返回值如下:

> **在数组上下文中:**这里它返回一个在表达式中找到的字段列表。如果未指定表达式，则返回$_。
> 
> **在标量上下文中:**这里它返回在表达式中找到的字段数，然后将这些字段存储在@_ 数组中。

使用 split()函数有**种不同的方式**如下:

#### 

*   Split on a character
*   Split in an unlimited string
*   Split in a limited string
*   Split on an undefined value
*   Split (pattern) on a [regular expression](https://www.geeksforgeeks.org/perl-regular-expressions/)
*   Split on [hash](https://www.geeksforgeeks.org/perl-hashes/)
*   Split in space

### 字符上的拆分

用户可以在不同的字符上断开或拆分字符串，如**逗号(，** **)反斜杠(\)** 等。当您必须从另一个程序或文件中解析数据时，通常会使用这种类型的拆分。不要使用 split()解析 *CSV(逗号分隔值)*文件。如果数据中有逗号，则使用**文本::CSV** 代替。

**示例:**

```perl
# Perl program to demonstrate the splitting on character

#!/usr/bin/perl
use strict;
use warnings;

# Here character is comma(, )
my $str = 'Geeks, for, Geeks';

# using split() function
my @spl = split(', ', $str);

# displaying result using foreach loop
foreach my $i (@spl) 
{
    print "$i";
}
```

**Output:**

```perl
GeeksforGeeks

```

### 无限制地在字符串之间拆分

这也和角色的分裂一样。这里字符串的数据用两个**隔开！！**。

**示例:**

```perl
# Perl program to demonstrate the
# splitting among string without Limit

#!/usr/bin/perl
use strict;
use warnings;

# string which is separated by !! sign
my $str = 'GFG!!Geeks!!55!!GeeksforGeeks';

# using split function without Limit
my @spl = split('!!', $str);

# displaying string after splitting
foreach my $i (@spl) 
{
    print "$i\n";
}
```

**Output:**

```perl
GFG
Geeks
55
GeeksforGeeks

```

### 带极限的字符串拆分

这也和角色的分裂一样。这里字符串的数据用两个**隔开！！**。在这里，用户可以通过在 split 函数中传递第三个参数来限制字符串将被拆分成的部分的数量，该参数将是一个正整数值。在下面的示例中，用户将*限制作为 3* 传递，因此它将限制字符串拆分为 3，即使出现了 4 次*！！*在弦上。

**示例:**

```perl
# Perl program to demonstrate the 
# splitting on string with Limit

#!/usr/bin/perl
use strict;
use warnings;

# string which is separated by !! sign
my $str = 'GFG!!Geeks!!55!!GeeksforGeeks';

# using split function with Limit
my @spl = split('!!', $str, 3);

# displaying string after splitting
foreach my $i (@spl) 
{
    print "$i\n";
}
```

**Output:**

```perl
GFG
Geeks
55!!GeeksforGeeks

```

### 对未定义的值进行拆分

如果用户试图对一个未定义的值进行拆分，那么字符串将对每个字符进行拆分。

**示例:**

```perl
# Perl program to demonstrate the 
# splitting on undefined value

#!/usr/bin/perl
use strict;
use warnings;

# string to be split
my $str = 'GeeksforGeeks GFG';

# using split function
my @spl = split(undef, $str);

# displaying string after splitting
foreach my $i (@spl) 
{
    print "$i\n";
}
```

**输出:**

```perl
G
e
e
k
s
f
o
r
G
e
e
k
s

G
F
G

```

**运行时错误:**

> 在/home/38 eceda 726 bcb7e 68 FB 7 b 41 ee 5b 8d 9 . pl 第 12 行的 regexp 编译中使用未初始化的值。

### 模式或正则表达式上的拆分

有时，用户可能想要在一个模式(正则表达式)或特定类型的字符上拆分字符串。这里，我们将使用特殊的字符类来创建数字(整数)模式，如下所示:

**示例:**

```perl
# Perl program to demonstrate the 
# splitting on a pattern(regex)

#!/usr/bin/perl
use strict;
use warnings;

# string to be split
my $str = 'Geeks1for2Geeks';

# using split function
# \d+ will match one or more
# integer numbers & placed 
# between two //
my @spl = split(/\d+/, $str);

# displaying string after splitting
foreach my $i (@spl) 
{
    print "$i\n";
}
```

**Output:**

```perl
Geeks
for
Geeks

```

### 分裂成一团

用户可以将数据或字符串拆分成哈希而不是数组。基本上，散列是一个键/值对。在拆分之前，用户必须了解哈希。

**示例:**

```perl
# Perl program to demonstrate the 
# splitting into the hash

#!/usr/bin/perl
use strict;
use warnings;

# hash to be split
my $has = 'GFG=1;GEEKS=2;PROGEEK=3';

# using split function
my %spl = split(/[=;]/, $has);

# after splitting displaying the values
foreach my $i (keys %spl) 
{
    print "$i:$spl{$i}\n";
}
```

**Output:**

```perl
GFG:1
GEEKS:2
PROGEEK:3

```

### 空间上的分裂

这里的空格不仅仅是指**这个空格，还包括换行符、制表符等。**

****示例:****

```perl
# Perl program to demonstrate the 
# splitting on space

#!/usr/bin/perl
use strict;
use warnings;

# string to be splitted
my $str = "ProGeek\n\nSudo\nPlacements";

# using split function
my @spl = split(' ', $str);

# Displaying result by printing
# 'GFG' either side of the 
# value, so that user can see 
# where it split
foreach my $i (@spl)
{
    print "GFG${i}GFG\n";
}
```

****Output:**

```perl
GFGProGeekGFG
GFGSudoGFG
GFGPlacementsGFG

```** 

### **要记住的要点**

*   **As split() function also *returns the value in scalar context*. So for storing the return values user have to define some scalar values according to the number of sections of splitting. In below example there will be 4 values after splitting so here user will define the 4 scalars values and store the return values.

    **示例:**

    ```perl
    # Perl program to demonstrate the 
    # splitting on string and storing 
    # values in scalars

    #!/usr/bin/perl
    use strict;
    use warnings;

    # string which is separated by !! sign
    my $str = 'GFG!Sudo!GeeksforGeeks!ProGeek';

    # using split function and 
    # storing values in scalars
    my ($sc1, $sc2, $sc3, $sc4) = split('!', $str);

    # displaying string after splitting
    print "$sc1\n$sc2\n$sc3\n$sc4";
    ```

    **Output:**

    ```perl
    GFG
    Sudo
    GeeksforGeeks
    ProGeek

    ```** 
*   **There may be a situation when user don’t pass in a string to split, then by default split() function will use the **$_** and if user don’t pass a Expression i.e. the string to split on then it will use **‘ ‘(a space)**.

    **示例:**

    ```perl
    # Perl program to demonstrate the 
    # split() function and context

    #!/usr/bin/perl
    use strict;
    use warnings;

    # using foreach loop containing string values
    foreach ('G F G', 'Geeks for Geeks')
    {
        # using split() function
        my @spl = split;

        # displaying values to be split
        print "Split $_:\n";

        foreach my $i (@spl)
        {
            print " $i\n";
        }
    }
    ```

    **Output:**

    ```perl
    Split G F G:
     G
     F
     G
    Split Geeks for Geeks:
     Geeks
     for
     Geeks

    ```** 
*   **If the delimiter is present at the starting of the string which is to be split, then the first element of return values will be empty and that will store into the array. In below example we have this situation and we are printing the empty value of resulted array:

    **示例:**

    ```perl
    # Perl program to demonstrate the 
    # split() function with the Delimiter
    # at the start of the string

    #!/usr/bin/perl
    use strict;
    use warnings;

    # string containing delimiter(, ) 
    # at the starting 
    my $str = ', GFG, Geeks';

    # using split function
    my @spl = split(', ', $str);

    # printing "Array_Element: " with each 
    # returned value so that you can see
    # the empty one
    foreach my $i (@spl) 
    {
        print "Array_Element: $i\n";
    }
    ```

    **Output:**

    ```perl
    Array_Element: 
    Array_Element: GFG
    Array_Element: Geeks

    ```** 
*   **If you want *to keep the delimiter* in result also then simply put that delimiter inside the parentheses.

    **示例:**

    ```perl
    # Perl program to demonstrate the 
    # split() function and keeping 
    # the delimiter

    #!/usr/bin/perl
    use strict;
    use warnings;

    # string to be split
    my $str = 'Geeks1for2Geeks';

    # using split function
    # \d+ will match one or more
    # integer numbers & placed 
    # between two // and () to 
    # keep the delimiter in result
    my @spl = split(/(\d+)/, $str);

    # displaying string after splitting
    foreach my $i (@spl) 
    {
        print "$i\n";
    }
    ```

    **Output:**

    ```perl
    Geeks
    1
    for
    2
    Geeks

    ```**