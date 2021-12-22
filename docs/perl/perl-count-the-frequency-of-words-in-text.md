# Perl |统计文字中单词的出现频率

> 原文:[https://www . geeksforgeeks . org/perl-count-in-text-word-frequency/](https://www.geeksforgeeks.org/perl-count-the-frequency-of-words-in-text/)

计算字符串中所有单词的频率是任何编程语言的基本操作。文本中每个单词的出现频率可以被计算并存储在一个散列中以供进一步使用。在 Perl 中，我们可以这样做，首先将字符串的单词拆分成一个数组。我们使用函数 *split / /* ，它用“”分割字符串。但是两个单词之间的空格可以超过一个，因此使用 */\s+/* 。这里 *\s+* 表示一次或多次出现' '。现在，我们遍历通过将文本拆分成单词而创建的新数组。这一次，我们在遍历数组时增加了单词的计数。

*   **Example:** To demonstrate Count the frequency of words in string

    ```perl
    # Perl program for counting words in a string

    $actual_text = "GFG GeeksforGeeks GFG" ;

    # Creating words array by splitting the string
    @words= split / /, $actual_text;

    # Traversing the words array and 
    # increasing count of each word by 1
    foreach $word(@words) 
    {
        $count{$word}++;
    }

    # Printing the word and its actual count
    foreach $word (sort keys %count) 
    {
        print $word, " ", $count{$word}, "\n";
    }
    ```

    **输出:**

    ```perl
    GFG 2
    GeeksforGeeks 1

    ```

**/\s+/和/ /** 的区别:' \ s+'可以用作一个或多个空格的分隔符。然而/ /只是用 1 个空格分隔单词。下面的代码表示如果两个单词之间的文本有一个以上的空格时的区别。

*   **Example:** To demonstrate the difference between /\s+/ and / /

    ```perl

    # Perl program for counting words in a string using / / 

    # A text with two spaces rather than one
    $actual_text = "GeeksforGeeks  welcomes you to GeeksforGeeks portal" ;

    # splitting the word with / /
    @words= split / /, $actual_text;

    # Counting the occurrence of each word  
    foreach $word (@words)
    {
        $count{$word}++;
    }

    foreach $word (sort keys %count)
    {
        print $word, " ", $count{$word}, "\n";
    }
    ```

    **输出:**

    ```perl
    1
    GeeksforGeeks 2
    portal 1
    to 1
    welcomes 1
    you 1

    ```

    **注:**多出来的' '也算一个字。

**使用命令/\s+/拆分单词:**这里空格不算单独的单词。

*   **Example:**

    ```perl

    #Perl program for counting words in a string using /\s+/

    # Actual string with two spaces
    $actual_text = "GeeksforGeeks  welcomes you to GeeksforGeeks portal" ;

    #S plitting the text using /\s+/ command
    @words = split /\s+/, $actual_text;

    # counting the occurrence of each word  
    foreach $word (@words) 
    {
        $count{$word}++;
    }

    foreach $word (sort keys %count)
    {
        print $word, " ", $count{$word}, "\n";
    }
    ```

    **输出:**

    ```perl
    GeeksforGeeks 2
    portal 1
    to 1
    welcomes 1
    you 1

    ```

    **注:**多余的' '不算一个字。