# 在 Perl 中对散列进行排序

> 原文:[https://www.geeksforgeeks.org/sorting-hash-in-perl/](https://www.geeksforgeeks.org/sorting-hash-in-perl/)

**先决条件: [Perl | Hashes](https://www.geeksforgeeks.org/perl-hashes/)**

一组键/值对被称为哈希。哈希结构中的每个键都是唯一的，并且是类型字符串。与这些键相关联的值是标量。这些值可以是数字、字符串或引用。哈希是用我的关键字声明的。让我们考虑一个例子来理解散列排序的概念。

**例子:**考虑一个班级学生名字和他们平均分数的散列。这里，学生的名字是关键，他们的平均成绩是数值。使用`keys` 函数返回的学生姓名上的 *foreach 循环*打印该散列。

```perl
# Perl program to demonstrate 
# the concept of hash
use strict;
use warnings;
use 5.010;

# Creating a hash of studentnames 
# and their average score
my %studentnames = (
Martha => 14,
Vivek => 27,
Earl => 31,
Marty => 16.5,
Jason => 25.2,
Socrates => 29.5,
Uri => 19.6,
Nitin => 30,
Plato => 39,
);

# displaying the keys and values of Hash
# using the foreach loop and keys function 
# output may be different each 
# time when you run the code
foreach my $name (keys %studentnames) {

    # printing the keys and values of hash
    printf "%-8s %s\n", $name, $studentnames{$name};
}
```

**输出:**

```perl
Marty    16.5
Jason    25.2
Plato    39
Vivek    27
Socrates 29.5
Martha   14
Earl     31
Uri      19.6
Nitin    30

```

**注意:**输出可能包含任何随机顺序，具体取决于系统和 Perl 的版本。

***哈希可以通过如下多种方式排序:***

*   **根据哈希键的 ASCII 值对哈希进行排序:**一般来说，排序是基于 ASCII 表的。这意味着排序会将所有大写字母放在所有小写字母的前面。这是排序的默认行为。上面的示例代码是根据其键的 ASCII 值排序的。
*   **Sorting the Hash according to the alphabetical order of its keys:** Here, the keys are sorted alphabetically.

    **示例:**

    ```perl
    # Perl program to demonstrate 
    # sorting of the hash according 
    # alphabetical order of its keys
    use strict;
    use warnings;
    use 5.010;

    # Creating a hash of studentnames 
    # and their average score
    my %studentnames = (
    Martha => 14,
    Vivek => 27,
    Earl => 31,
    Marty => 16.5,
    Jason => 25.2,
    Socrates => 29.5,
    Uri => 19.6,
    Nitin => 30,
    Plato => 39,
    );

    # sorting the hash according 
    # alphabetical order of its keys
    foreach my $name (sort {lc $a cmp lc $b} keys %studentnames) 
    {
        printf "%-8s %s\n", $name, $studentnames{$name};
    }
    ```

    **输出:**

    ```perl
    Earl     31
    Jason    25.2
    Martha   14
    Marty    16.5
    Nitin    30
    Plato    39
    Socrates 29.5
    Uri      19.6
    Vivek    27

    ```

*   **Sorting according to the values of Hash:** You can also sort the hash according to the values of hash as follows:

    **示例 1:** 根据 ASCII 表对哈希值进行排序。

    ```perl
    # Perl program to demonstrate 
    # sorting of the hash according
    # to the values of Hash
    use strict;
    use warnings;
    use 5.010;

    # Creating a hash of studentnames 
    # and their average score
    my %studentnames = (
    Martha => 14,
    Vivek => 27,
    Earl => 31,
    Marty => 16.5,
    Jason => 25.2,
    Socrates => 29.5,
    Uri => 19.6,
    Nitin => 30,
    Plato => 39,
    );

    # sorting of the hash according
    # to ASCII code of values of Hash
    foreach my $name (sort values %studentnames) 
    {
        say $name;
    }
    ```

    **输出:**

    ```perl
    14
    16.5
    19.6
    25.2
    27
    29.5
    30
    31
    39

    ```

    **例 2:** 根据哈希值的数值排序如下:

    ```perl
    # Perl program to demonstrate 
    # sorting of the hash according
    # to the values of Hash
    use strict;
    use warnings;
    use 5.010;

    # Creating a hash of studentnames 
    # and their average score
    my %studentnames = (
    Martha => 14,
    Vivek => 27,
    Earl => 31,
    Marty => 16.5,
    Jason => 25.2,
    Socrates => 29.5,
    Uri => 19.6,
    Nitin => 30,
    Plato => 39,
    );

    # sorting of the hash according
    # to the numerical value of
    # Values of hash
    foreach my $name (sort {$a<=>$b} values %studentnames) 
    {
        say $name;
    }
    ```

    **输出:**

    ```perl
    14
    16.5
    19.6
    25.2
    27
    29.5
    30
    31
    39

    ```

*   **Sort the keys of the hash according to the values:** You can also sort the keys of hash according to the given values.

    **示例 1:** 在下面的程序中，< = >被称为*宇宙飞船操作员*。如果您反复运行代码，那么您可以注意到输出中的差异。有时你会在*之前找到*柏拉图*，反之亦然。*

    ```perl
    # Perl program to demonstrate the
    # Sorting of keys of the hash 
    # according to the values
    use strict;
    use warnings;
    use 5.010;

    # Creating a hash of studentnames 
    # and their average score
    my %studentnames = (
    Martha => 14,
    Vivek => 27,
    Earl => 31,
    Marty => 16.5,
    Jason => 25.2,
    Socrates => 29.5,
    Uri => 19.6,
    Nitin => 45,
    Plato => 45,
    );

    # Sort the keys of the hash
    # according to the values
    # Here $a and $b are the 
    # placeholder variable of sort
    foreach my $name (sort {$studentnames{$a} <=> 
           $studentnames{$b}} keys %studentnames) 
    {
        printf "%-8s %s\n", $name, $studentnames{$name};
    }
    ```

    **输出:**

    ```perl
    Martha   14
    Marty    16.5
    Uri      19.6
    Jason    25.2
    Vivek    27
    Socrates 29.5
    Earl     31
    Plato    45
    Nitin    45

    ```

    **例 2:** 为了求解上述代码，具有相同值的键可以根据 ASCII 表排序如下:

    ```perl
    # Perl program to demonstrate the
    # Sorting of keys of the hash 
    # according to the values
    use strict;
    use warnings;
    use 5.010;

    # Creating a hash of studentnames 
    # and their average score
    my %studentnames = (
    Martha => 14,
    Vivek => 27,
    Earl => 31,
    Marty => 16.5,
    Jason => 25.2,
    Socrates => 29.5,
    Uri => 19.6,
    Nitin => 45,
    Plato => 45,
    );

    # keys that have the same value 
    # will be sorted according the 
    # ASCII table
    foreach my $name (sort { $studentnames{$a} <=> $studentnames{$b} or
                                    $a cmp $b } keys %studentnames) {
        printf "%-8s %s\n", $name, $studentnames{$name};
    }
    ```

    **输出:**

    ```perl
    Martha   14
    Marty    16.5
    Uri      19.6
    Jason    25.2
    Vivek    27
    Socrates 29.5
    Earl     31
    Nitin    45
    Plato    45

    ```

    **说明:**这里可以看到重点*尼廷*和*柏拉图*是按照 ASCII 表排序的。不管您运行代码多少次，输出都将保持不变。