# 在 Perl 中对混合字符串进行排序

> 原文:[https://www . geesforgeks . org/sorting-混合字符串-in-perl/](https://www.geeksforgeeks.org/sorting-mixed-strings-in-perl/)

在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的排序可以通过使用预定义的函数“sort”来完成。该函数使用快速排序算法对传递给它的数组进行排序。

> **语法:**排序@数组
> 
> **返回:**一个排序数组

对包含混合形式字符串(即字母数字字符串)的数组进行排序可以通过使用 sort()函数以多种方式完成。

**示例:**

```
Input :  Key_8, pub_12, pri_4 (array of strings) 
Output :  pri_4 Key_8 pub_12

```

这种数组的排序是通过从字符串中提取数字来完成的，这可以通过两种方式完成:

*   **使用 substr()函数**:为了使用数字比较字符串，从字符串中获取数字是非常必要的。根据这些数字，我们将对字符串数组进行排序。substr()函数用于从字符串中提取这些数字。该函数将字符串中除数字以外的字符数作为参数。
    **注意:**数组中的所有字母数字字符串必须大小相同。
    **示例:**

    ```
    use strict;
    use 5.010;

    # Defining array values with 
    # alphanumeric strings
    my @x = qw(prin_4 Keys_8 pubg_12);

    # Use of sort and substr function 
    # to sort the array
    my @y = sort { substr($a, 5) <=> substr($b, 5) } @x;

    # Printing the sorted array 
    print join " ", @y;
    ```

    **输出:**

    ```
    prin_4 Keys_8 pubg_12

    ```

*   **Using Regular Expressions :** Executing above code is a tough job if the alphanumeric string is a little bit complex, hence, for more simplicity, we can use Regular Expressions.

    例如，如果数组由“Keys_8_keys”组成，那么很难处理这种情况，因此为了从字符串中正确过滤数字，使用了正则表达式。

    **注意:**这个方法不关心字母数字串的大小是否不同。

    ```
    use strict;
    use 5.010;

    # Sample string to extract 
    # number from
    my $str = 'Key_8_key';

    # Regular expression to extract the number
    my ($number) = $str =~ /(\d+)/;

    # Printing the extracted number
    print "Number Extracted from Key_8_key is $number\n";

    # Defining the array with 
    # Alphanumeric strings
    my @x = qw(pri_4 Key_8_key pubg_12);

    # Array before sorting
    print "\nArray Before sorting\n";
    print join " ", sort @x;

    # Calling the sort function
    # with Regular Expression
    my @y = sort { ($a =~ /(\d+)/)[0] <=> ($b =~ /(\d+)/)[0] } @x;

    # Printing the Array after sorting
    print "\n\nArray After sorting\n";
    print join " ", @y;
    ```

    **Output:**

    ```
    Number Extracted from Key_8_key is 8

    Array Before sorting
    Key_8_key pri_4 pubg_12

    Array After sorting
    pri_4 Key_8_key pubg_12

    ```

**不带数字的字符串:**如果数组由字符串组成，其中一些字符串没有数字，那么可以用 0 来代替那个数字。要检查字符串中是否没有数字，请使用以下代码:

```
 my @y = sort { (($a =~ /(\d+)/)[0] || 0)  (($b =~ /(\d+)/)[0] || 0) } @x; 

```

```
#!/usr/bin/perl
use strict;
use 5.010;

# Array with mixed type of strings
my @x = qw(pri_4 Key pubg_12);

# Function call with a Regular Expression
my @y = sort { (($a =~ /(\d+)/)[0] || 0) <=> 
               (($b =~ /(\d+)/)[0] || 0) } @x;

# Printing the sorted array
print join " ", @y;
```

**Output:**

```
Key pri_4 pubg_12

```

**使用子例程排序:**为了更好地模块化代码，我们可以在 Perl 中创建单独的函数或子例程，并使用该子例程执行排序操作。sort()函数以子程序名为参数，调用保存排序定义的子程序。

```
#!/usr/bin/perl
use strict;
use 5.010;

# Defining an array with strings
my @x = qw(Key_8 pri_4 pubg_12);

# Calling sort function to sort 
# array using subroutine
my @y = sort numbersort @x;

# Printing the sorted array
print join " ", @y;

# Subroutine to sort the array
sub numbersort 
{
    my ( $anum ) = $a =~ /(\d+)/;
    my ( $bnum ) = $b =~ /(\d+)/;
    ( $anum || 0 ) <=> ( $bnum || 0 );
}
```

**Output:**

```
pri_4 Key_8 pubg_12

```