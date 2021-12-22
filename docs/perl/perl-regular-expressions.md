# Perl |正则表达式

> 原文:[https://www.geeksforgeeks.org/perl-regular-expressions/](https://www.geeksforgeeks.org/perl-regular-expressions/)

***Perl 中的正则表达式(Regex 或 Regexp 或 RE)*** 是一个特殊的文本字符串，用于描述给定文本中的搜索模式。Perl 中的 Regex 链接到宿主语言，与 PHP、Python 等中的 regex 不一样。有时它被称为***【Perl 5 兼容正则表达式】*** 。要使用正则表达式，绑定运算符如**= ~“**(正则表达式运算符)和**！~'** (取反的 Regex 运算符)被使用。在转向绑定操作符之前，让我们来看看构建模式。

**构建模式:**在 Perl 中，可以使用**m/**运算符构建模式。在这个操作符中，所需的模式简单地放在两个斜杠之间，绑定操作符用于搜索指定字符串中的模式。

**使用 m//和绑定操作符:**绑定操作符大多与 *m//* 操作符一起使用，以便匹配出所需的模式。Regex 运算符用于将字符串与正则表达式进行匹配。语句的左侧将包含一个字符串，该字符串将与包含指定模式的右侧相匹配。否定正则表达式运算符用于检查字符串是否不等于右侧指定的正则表达式。

*   **程序 1:** 举例说明‘m//’和’= ~’的用法如下:

    ```
    # Perl program to demonstrate
    # the m// and =~ operators

    # Actual String
    $a = "GEEKSFORGEEKS";

    # Prints match found if 
    # its found in $a
    if ($a =~ m[GEEKS]) 
    {
        print "Match Found\n";
    }

    # Prints match not found 
    # if its not found in $a
    else 
    {
        print "Match Not Found\n";
    }
    ```

    **输出:**

    ```
    Match Found

    ```

*   **程序 2:** 举例说明‘m//‘and’的用法！~ '如下:

    ```
    # Perl program to demonstrate
    # the m// and !~ operators

    # Actual String
    $a = "GEEKSFORGEEKS";

    # Prints match found if 
    # its not found in $a
    if ($a !~ m[GEEKS]) 
    {
        print "Match Found\n";
    }

    # Prints match not found 
    # if it is found in $a
    else
    {
        print "Match Not Found\n";
    }
    ```

    **输出:**

    ```
    Match Not Found

    ```

**正则表达式的用途:**

*   它可用于统计字符串中指定模式的出现次数。
*   它可用于搜索与指定模式匹配的字符串。
*   它还可以用其他指定的字符串替换搜索到的模式。