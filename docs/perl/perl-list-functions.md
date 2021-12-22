# Perl |列表函数

> 原文:[https://www.geeksforgeeks.org/perl-list-functions/](https://www.geeksforgeeks.org/perl-list-functions/)

T2 Perl 中的列表是标量值的集合。我们可以使用索引访问列表的元素。索引以 0 开始(第 0 个索引指列表的第一个元素)。我们使用括号和逗号运算符来构造一个列表。在 Perl 中，标量变量以$符号开始，而列表变量以@符号开始。
列表提供了各种预定义的功能，可以轻松执行操作。其中一些功能如下:

*   **join() function**
    join() function is used to combine the elements of a List into a single string with the use of a separator provided to separate each element. This function returns the joined string. A separator can work only between the pairs. A separator can’t be placed at either end of the string. In order to join the strings without a separator, an empty parameter is passed to the function.

    > **语法:**连接(分隔符，列表)
    > 
    > **参数:**
    > 
    > *   **分离器:**用于在连接时分离每个元件
    > *   **列表:**转换为单个字符串
    > 
    > **返回:**一个连接字符串

    **示例:**

    ```perl
    #!/usr/bin/perl

    # Initializing list with alphabets A to Z
    @list = (A..Z);

    # Printing the original list
    print "List: @list\n";

    # Using join function introducing
    # hyphen between each alphabets
    print "\nString after join operation:\n";
    print join("-", @list);
    ```

    **输出:**

    ```perl
    List: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z

    String after join operation:
    A-B-C-D-E-F-G-H-I-J-K-L-M-N-O-P-Q-R-S-T-U-V-W-X-Y-Z

    ```

*   **reverse() function**
    Reverse() function in Perl returns the elements of List in reverse order in a list context. While in a scalar context, it returns a concatenated string of the values of List, with all characters in opposite order. It returns String in Scalar Context and List in List Context.

    > **语法:**反向列表
    > 
    > **参数:**
    > **列表:**列表待反转
    > 
    > **以相反的顺序返回:**元素

    **示例:**

    ```perl
    # Initializing a list
    @list = ("Raj", "E123", 12000);

    # Reversing the list
    @rname = reverse(@list);

    # Printing the reversed list
    print "Reversed list is @rname";

    # Initializing a scalar
    $string = "GeeksforGeeks";

    # Reversing a scalar
    $r = reverse($string);
    print "\nReversed string is $r";
    ```

    **输出:**

    ```perl
    Reversed list is 12000 E123 Raj
    Reversed string is skeeGrofskeeG

    ```

*   **map() function**
    map() function in Perl evaluates the operator provided as a parameter for each element of List. For each iteration, $_ holds the value of the current element, which can also be assigned to allow the value of the element to be updated. map() function runs an expression on each element of an array and returns a new array with the updated results. It returns the total number of elements generated in scalar context and list of values in list context.

    > **语法:**地图(操作，列表)
    > **参数:**
    > 
    > *   **操作:**对列表元素执行
    > *   **列表:**哪些元素需要更改

    **示例:**

    ```perl
    # Initializing a list
    @Dept = ('comp', 'inft', 'extc', 'mech');

    # Converting first character capital
    @upd1 = map(ucfirst, @Dept);

    # Printing list
    print "List with First char capital: ";
    foreach $i (@upd1) 
    {
       print "$i, ";
    }

    # Converting all characters capital
    @upd2 = map(uc, @Dept);

    # Printing list
    print "\nList with all char capital: ";
    foreach $i (@upd2) 
    {
       print "$i, ";
    }
    ```

    **输出:**

    ```perl
    List with First char capital: Comp, Inft, Extc, Mech, 
    List with all char capital: COMP, INFT, EXTC, MECH, 
    ```

*   **sort() function**
    sort() function in Perl is used to arrange the List according to the condition of sorting specified to the function. If no condition is specified, then it sorts according to normal alphabetical sequence.
    If a condition is specified then the function sorts the List according to the condition.

    > **语法:**排序(条件，列表)

    **例**

    ```perl
    # Initializing two lists
    @country = ('India', 'Qatar', 'Bangladesh', 'France', 'Italy');
    @capital = ('Delhi', 'Lahore', 'Dhaka', 'Paris', 'Rome');

    # Printing countries in sorted order
    print"Countries in sorted order: \n";
    print sort @country;
    print "\n";

    # Printing sorted country and capital values
    print "\nCombining both the lists in sorted order:\n";
    print sort @country, @capital;
    print "\n";

    # Initializing a list with number
    @list = (19, 4, 54, 33, 99, 2);

    # Sorting in descending order
    @s = sort{$b <=> $a} @list;
    print "\nPrinting numbers in sorted order:\n";
    foreach $i(@s)
    {
        print "$i, ";
    }
    ```

    **输出:**

    ```perl
    Countries in sorted order: 
    BangladeshFranceIndiaItalyQatar

    Combining both the lists in sorted order:
    BangladeshDelhiDhakaFranceIndiaItalyLahoreParisQatarRome

    Printing numbers in sorted order:
    99, 54, 33, 19, 4, 2, 
    ```