# Perl |比较标量

> 原文:[https://www.geeksforgeeks.org/perl-comparing-scalars/](https://www.geeksforgeeks.org/perl-comparing-scalars/)

#### 先决条件:[Perl 中的标量](https://www.geeksforgeeks.org/perl-scalars/)

Perl 有两种类型的比较运算符集。就像其他数学运算符一样，这些运算符不是执行运算，而是比较标量。有两种类型的 Perl 比较运算符集。
一个是**数值标量值**，一个是**字符串标量值**。下表说明了这两种类型:

| 数字的 | 线 | 描述 |
| --- | --- | --- |
| == | 情商 | 等于 |
| ！= | -不知道 | 不等于 |
| < | 它 | 小于 |
| > | 大型旅行车的 | 大于 |
| <= | 务实贸易(Labor Exchange)ˌ低爆速炸药(Low Explosive)ˌ职业介绍所(Labour Exchange) | 小于或等于 |
| >= | 通用电气公司 | 大于或等于 |

**以上数值和字符串标量比较运算符的说明:**

*   **== and eq** : This operator is used to check the equality. In the following code, outputs of codes after using == and eq is compared and showing how it work for numeric and string scalars differently.

    **例 1:**

    ```
    # Perl program to illustrate
    # == operator

    # taking two numeric scalars
    $x = 5;
    $y = 5;

    # using "==" operator
    if($x == $y)
    {
        print "== works with numeric value!";
    }
    ```

    **输出:**

    ```
    == works with numeric value!

    ```

    **例 2:**

    ```
    # Perl program to illustrate
    # == and eq operator

    # string scalar
    $str = "geekforgeeks";

    if($str == "GEEKSFORGEEKS")
    {
        print "== doesn't work with string values!";

    }

    # comparing with capital string
    if($str eq "GEEKSFORGEEKS")
    {
        print "eq works with string values!";
    }
    ```

    **输出:**

    ```
    == doesn't work with string values!

    ```

    **说明:**在示例 2 的输出中，因为$str 和 GEEKSFORGEEKS 不相等，所以不会执行 Last print 语句。另外，“G”和“G”的 ASCII 码是不同的。因此，==适用于数值，但不适用于字符串值，eq 仅适用于字符串标量。

*   **!= and ne**

    在下面的代码中，比较了使用后的输出！=和 ne，并显示了哪一个适合字符串，哪一个适合数值标量值。

    **例 1:**

    ```
    # Perl program to demonstrate the 
    # != operator

    # numeric scalars
    $x = 5;
    $y = 10;

    # using != operator
    if($x != $y)
    {
        print "!= works with numeric value!";
    }
    ```

    **输出:**

    ```
    != works with numeric value!

    ```

    **例 2:**

    ```
    # Perl program to demonstrate the 
    # != and ne operator

    # string scalar
    $str = "geekforgeeks";

    # using != operator
    if($str != "GEEKSFORGEEKS")
    {
        print "\n!= doesn't work with string values!";

    }

    # comparing with capital string
    if($str ne "GEEKSFORGEEKS")
    {
        print"ne works with string values!";
    }
    ```

    **输出:**

    ```
    ne works with string values!

    ```

    **说明:**在第二个例子中，不会执行第一个 print 语句，因为！=将两个字符串都转换为 0。因此！=适用于数值，但不适用于字符串值，ne 适用于字符串标量。

*   **(> or gt) And (< or lt)**

    在下面的代码中，我们将比较使用(>或 gt)和(

    **例 1:**

    ```
    # Perl program to demonstrate the 
    # (> or gt) And (< or lt)
    # operator

    # numeric scalars
    $x = 4;
    $y = 5;

    # using (> or gt) And (< or lt)
    if(($x < $y) and ($x lt $y) )
    {
        print "< and lt works with numeric value!";
    }

    if(($y > $x) and ($y gt $x) )
    {
        print "\n> and gt works with numeric value!";
    }
    ```

    **输出:**

    ```
    < and lt works with numeric value!
    > and gt works with numeric value!

    ```

    **例 2:**

    ```
    # Perl program to demonstrate the 
    # (> or gt) And (< or lt)
    # operator

    # string scalar
    $str = "geekforgeeks";

    if($str < "GEEKSFORGEEKS")
    {
        print "< doesn't work with string values!";
    }

    # comparing with capital string
    if($str lt "GEEKSFORGEEKSZZZ")
    {
        print"lt works with string values!";
    }

    # comparing with capital string
    if($str gt "GEEKSFORGEEKSZZZ")
    {
        print"gt works with string values!";
    }

    # comparing with capital string
    if($str lt "kEEKSFORGEEKS")
    {
        print"\nlt works with string values!";
    }
    ```

    **输出:**

    ```
    gt works with string values!
    lt works with string values!

    ```

    **解释:**上面的代码告诉我们一些关于 Perl 如何处理字符串的有趣的事情。第一个例子的输出非常明显，因为字符串和数值运算符都以同样的方式对待数值标量。
    但是在第二个输出中，“lt”并没有像我们预期的那样表现。假设 Perl 的“lt”运算符不区分大小写，但我们甚至在后面加上了“ZZZ”，即使在这种情况下,$str 也不小于引号中的字符串，下一个输出显示它更大。从第二个例子输出的第二行
    可以清楚地看到这一点，Perl 的字符串运算符只需首先检查字符串的第一个字符，然后比较 ASCII 码。因为在 ASCII 表中，大写字母排在第一位。Perl 编译器匹配第一个字母，然后匹配其余字母。

*   **(>= or ge) And (<= or le)**

    这些操作符也处理 ASCII 值，在字符串操作符的情况下进行检查。如果是数值运算符，则检查该值。

    **示例:**

    ```
    # Perl program to demonstrate the 
    # (>= or ge) And (<= or le)
    # operator

    # numeric scalars
    $x = 5;
    $y = 10;

    if(($x <= $y) and ($y >= $x))
    {
        print "<= and>= works";
    }

    # string scalar
    $str= "geeksforgeeks";

    if (($str le "keeksforgeeks") and ($str ge "feeksforgeeks"))
    {
        print "\nle and ge works!";
    }

    ```

    **输出:**

    ```
    <= and>= works
    le and ge works!

    ```

    **需要记住的要点:**

    *   **Numeric operator will always convert String values to 0.** When we compare two string scalars with Numeric operators like ==, >= or <= then it will always convert the scalars to 0 or 0.0\. Since they are not a string. And hence it will be true in case of ==, >= or <= as shown in the below example:

        ```
        # Perl program to illustrate 
        # above point

        # numeric scalars
        $x = "BBB";
        $y = "aaa";

        if (($x == $y and ($x <= $y) and ($x >= $y)))
        {
            print "True";
        }
        ```

        **输出:**

        ```
        True

        ```

        **解释:**在上面的代码中，“aaa”在各个方面都小于 BBB(小写，也是 ASCII 的 a 大于 B)，但是两个字符串仍然是相等的，因为数值比较运算符将字符串转换为 0。

    *   **String operator doesn’t compare numeric values, instead it compares there ASCII values.** String operators compare ASCII values for numeric values. In the following example “9 gt 17” is true but “17 gt 9” will give the result as false.

        ```
        # Perl program to illustrate 
        # above point

        # numeric scalar
        $x = 9;
        $y = 17;

        if ($x gt $y)
        {
            print "True";
        }
        ```

        **输出:**

        ```
        True

        ```