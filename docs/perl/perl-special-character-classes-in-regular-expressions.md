# Perl |正则表达式中的特殊字符类

> 原文:[https://www . geesforgeks . org/perl-正则表达式中的特殊字符类/](https://www.geeksforgeeks.org/perl-special-character-classes-in-regular-expressions/)

在 Perl 中实现了许多不同的字符类，其中一些使用非常频繁，以至于为它们创建了一个特殊的序列。创建特殊序列的目的是使代码更易读、更简短。Perl 中的**特殊字符类**如下:

1.  **Digit \d[0-9]**: The **\d** is used to match any digit character and its equivalent to [0-9]. In the regex **/\d/** will match a single digit. The *\d* is standardized to “digit”. The main advantage is that the user can easily write in shorter form and can easily read it. There are two ways to use this special character class. Let’s take an example for better understanding to know how to match the character string.

    **示例:**

    ```perl
    /#[MNOPQ]-\d\d\d/

    ```

    上面给定的字符串将匹配如下。

    ```perl
    #M-12345
    #N-66666

    ```

    在这里，我们也可以通过把它放在字符类上来使用量词。

    **示例:**

    ```perl
    /#[MNOPQ]-\d{5}/

    ```

    上面给出的例子与前面的正则表达式相同，它允许破折号后有任意数量的数字，可以写成**/#【MNOPQ】-\ d+/**。

    第二种方法用于较大的字符类。 **\d** 放在方括号内，匹配单字符数字。

    **示例:**

    ```perl
    [\dABCDEFDEFGHIJKLMN]

    ```

    可以匹配单个数字，也可以匹配任何大写字母 A、B、C、D、E、F、G、H、I、J、K、L、M 或 n。可以使用破折号(-)以较短的形式书写。然后会是这样的:

    ```perl
    [\dA-N]

    ```

2.  **PO SIX character classes:** PO SIX are the standards to maintaining the compatibility between operating systems and defines the application programming interface(API), with command line shells and utility interfaces. It also specifies a number of **“groups of characters”** with a name such as (alpha, alnum, ascii, blank etc). The PO SIX character classes always exists in the form of **[:class:]** where class is the name and the *[:* and *:]* are the delimiters. POSIX character classes always appear inside the bracketed character classes. These classes are a convenient and explanatory way of listing a group of characters.

    **语法:**

    ```perl
    $string =~ /[[:class:]]/
    ```

    这里的类可以是 alpha、alnum、ascii 等。

    POSIX 字符类支持更大的括号字符类，如下所示:

    ```perl
    [01[:Class:]%]

    ```

    这里它将匹配“0”、“1”和任何字符类以及百分号。Perl 为不同的 PO SIX 字符类提供支持，如下表所示:

    | 班级 | 描述 |
    | --- | --- |
    | 希腊字母的第一个字母 | 任何字母字符(“[A-Za-z]”) |
    | alnum | 任何字母数字字符(“[A-Za-z0-9]”)。 |
    | 美国信息交换标准码 | ASCII 字符集中的任何字符。 |
    | 空白的 | 空格或水平制表符 |
    | cntrl | 任何控制字符。 |
    | 手指 | 任何十进制数字(“[0-9]”)。 |
    | 图表 | 任何可打印字符，不包括空格 |
    | 降低 | 任何小写字符(“[a-z]”) |
    | 泪点 | 任何图形字符 |
    | 空间 | 任何空白字符 |
    | 上面的 | 任何大写字符(“[A-Z]”) |
    | xdigit | 任何十六进制数字(“[0-9a-fA-F]”) |
    | 单词 | 一个 Perl 扩展(“[A-Za-z0-9_]”)，相当于“\w” |

3.  **Word character \w[0-9a-zA-Z_]**: The **\w** belongs to word character class. The *\w* matches any single alphanumeric character which may be an alphabetic character, or a decimal digit or punctuation character such as *underscore(_)*. It will match only single character word, not the whole word. If you want to match the whole word then use **\w+**.
4.  **Whitespace \s[\t\n\f\r ]**: The character class **\s** will match a single character i.e. a whitespace. It will also match the 5 characters i.e. **\t -horizontal tab**, **\n-the newline**, **\f-the form feed**, **\r-the carriage return**, and **the space**. In Perl v5.18, a new character to be introduced which is matches the **\cK – vertical tab** .
5.  **Negated character classes \D, \W, \S** : There are more than 110, 000 Unicode characters available in this world. To negate a character class just use **caret(^)** symbol. It will negate the specified character after the symbol or even a range. In negated character classes we use **[^\d]** to negate the digits from 0 to 9\. But in place of **[^\d]** we can use simply **\D** to negate the digits from 0 to 9\. Following table illustrate the special negated character classes:

    | 字符类 | 否定 | 意义 | 描述 |
    | --- | --- | --- | --- |
    | \d | \D | [^\d] | 匹配任何非数字字符 |
    | \s | \S | [^\s] | 匹配任何非空白字符 |
    | \w | \W | [^\w] | 匹配任何非“单词”字符 |

6.  **Unicode character classes:** The Unicode is a definition of “all” the existing characters and the Unicode Standard provides a unique number for each and every character, and it is platform independent. There are more than 100, 000 character available in this world and each character described as a character point. But some of the characters are grouped together.

    **语法:**

    ```perl
    \p{...any character...}

    ```

    该语法用于匹配其中一个组中的单个字符。如果您需要匹配除指定字符以外的任何内容，那么您可以使用相应的**\ P {…任何字符…}** 表达式。