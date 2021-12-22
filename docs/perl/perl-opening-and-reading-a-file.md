# Perl |打开和读取文件

> 原文:[https://www . geesforgeks . org/perl-打开并读取文件/](https://www.geeksforgeeks.org/perl-opening-and-reading-a-file/)

文件句柄是一种内部 Perl 结构，它将物理文件与一个名称相关联。所有文件句柄都具有读/写访问权限，因此一旦文件句柄连接到文件，就可以进行读/写操作。但是，在关联文件句柄时，将指定打开文件句柄的模式。

**Opening a File**

打开功能用于打开新文件或现有文件。

> **语法:**打开 FILEHANDLE，VAR

这里，FILEHANDLE 是打开函数返回的句柄，VAR 是具有文件名和打开文件模式的表达式。
下表显示了可以打开文件和访问各种操作的模式。
**r+9

| model | describe |
| Or r < | Read-only access |
| W or > | Create, write and truncate |
| Or > > | Write, append and create |** 

**Reading a file**

一旦一个 FILEHANDLE 被分配了一个文件，就可以进行读、写、追加等各种操作。读取文件有许多不同的方法。

*   使用文件句柄操作符
*   使用 getc 函数
*   使用读取功能

*   **The FileHandle Operator**
    The main method of reading the information from an open filehandle is using the operator **< >**. When < > operator is used in a list context, it returns a list of lines from the specified filehandle. The example below reads one line from the file and stores it in the scalar.

    让文件**“gfg . txt”**的内容如下:

    ```perl
    GeeksforGeeks
    Hello Geek
    Geek a revolution
    Geeks are the best

    ```

    **例:GFG.pl**

    ```perl
    # Opening the file 
    open(fh, "GFG.txt") or die "File '$filename' can't be opened";

    # Reading First line from the file
    $firstline = <fh>;
    print "$firstline\n";
    ```

    **输出:**
    ![](img/2a03082858a1b09e1ff8bb58d06c37f4.png)

*   **getc Function**
    The getc function returns a single character from the specified FILEHANDLE, or STDIN if none is specified

    > **语法:** getc FILEHANDLE

    ```perl
    # Opening the file 
    open(fh, "GFG.txt") or die "File '$filename' can't be opened";

    # Reading First char from the file
    $firstchar = getc(fh);
    print "$firstchar\n";
    ```

    **输出:**
    ![](img/cd51e6f5e989527ec8d9fa6dc54613e6.png)

    如果有错误或者文件句柄在文件的末尾，那么它返回 undef。

*   **read Function**
    The read function is used to read binary data from a file using filehandle.

    > **语法**
    > 读取文件句柄，标量，长度，偏移量
    > 读取文件句柄，标量，长度

    这里，LENGTH 表示要读取的数据的长度，如果没有指定 OFFSET，数据将放在 SCALAR 的开头。否则，数据将被放在 SCALAR 中的 OFFSET 字节之后。文件读取成功后，函数返回读取的字节数，文件末尾为零，如果有错误，则返回 undef。

    **Reading Multiple line at a time**

    下面的例子读取文件句柄指定的文件内容，直到到达文件结尾(EOF)。

    **示例:File.pl**

    ```perl
    # Opening the file
    open(FH, "GFG.txt")or die "Sorry!! couldn't open";
    print "Reading file \n";

    # Reading the file till FH reaches EOF
    while(<FH>)
    {
        # Printing one line at a time
        print $_;
    }
    close;
    ```

    **输出:**
    ![](img/2b6b6eb1433d5235b3d9a265ac1cf175.png)

    **Exception Handling in Files**

    异常有两种处理方式

    *   如果文件无法打开，将引发异常
    *   如果文件无法打开并继续运行，则发出警告
    *   **Throw an Exception**
        When filehandle could not be assigned a valid file pointer at that time die gets executed printing the message and kills the current program.
        **Example :**

        ```perl
        # Initializing filename 
        $filename = 'GFG1.txt';

        # Prints an error and exits if file not found
        open(fh, '<', $filename) or die "Couldn't Open file $filename";
        ```

        **输出:**
        ![](img/13ed6a36636a4afca0a6f7af60bfcd70.png)

        如果找不到文件，上面的代码会打印一个错误，并从代码中退出。

    *   **Give a warning**
        When filehandle could not be assigned a valid file pointer it just prints warning message using warn function and keeps running.
        **Example :**

        ```perl
        # Initializing filename
        $filename = 'GFG.txt';
        # Opening a file and reading content
        if(open(fh, '<', $filename))
        {
            while(<fh>)
            {
                print $_;
            }
        }

        # Executes if file not found
        else
        {
          warn "Couldn't Open a file $filename";
        }
        ```

        **输出:**
        ![](img/30eb70c58cfadfb9438dd37a208a0c27.png)