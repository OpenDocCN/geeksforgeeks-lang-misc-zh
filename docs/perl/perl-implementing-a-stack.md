# Perl |实现堆栈

> 原文:[https://www.geeksforgeeks.org/perl-implementing-a-stack/](https://www.geeksforgeeks.org/perl-implementing-a-stack/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的堆栈是一种线性数据结构，遵循**后进先出**(后进先出)或 **FILO** (先进后出)的顺序。
简单来说，栈是一个数组，其中插入和删除只发生在称为栈顶的一端。
**推**是将元素插入堆栈的过程。
**弹出**是移除堆栈最顶层元素的过程。

**Making a stack**

用 Perl 创建堆栈相当简单。我们只需要声明一个数组。
堆栈可以是空的，如下所示:

```
@stack;
```

或者它可以被初始化:

```
@stack = (1, 2, 3);
```

**Pushing items to a stack**

可以使用**推送()**功能或**拼接()**功能进行推送。

*   使用**推送()**推送:

> **语法:**推送(@stack，list)；
> T3】参数:
> 
> *   @ stack–要在其上执行推送的堆栈。
> *   列表–要推入堆栈的元素。这些元素可以是标量、数组、散列或它们的任意组合。

**示例:**

```
#!/usr/bin/perl

# Intitialising the Stack
@stack = (1..3);

# Original stack
print "Original Stack: @stack";

# Scalar to be pushed
$scalar = "scalar";

# Array to be pushed
@array = ("a", "r", "r", "a", "y");

# Hash to be pushed
%hash = ("Geeks" => 10, 
         "for Geeks" => 20);

# scalars, arrays and hashes can be
# inserted at the same time
push(@stack, ($scalar, @array, %hash)); 

# Updated Stack after 
# Push operations
print("\nUpdated Stack: @stack");
```

**Output:**

```
Original Stack: 1 2 3
Updated Stack: 1 2 3 scalar a r r a y Geeks 10 for Geeks 20

```

*   Pushing using **splice()**:

    > **语法:**拼接(@stack，标量(@stack)，0，list)；
    > T3】参数:
    > 
    > *   函数的作用是:在@stack 的末尾追加“list”。
    > *   “list”可以是标量、数组或哈希。

    **示例:**

    ```
    #!/usr/bin/perl

    # Intitialising the Stack
    @stack = (1..3);

    # Original stack
    print "Original Stack: @stack";

    # Scalar to be pushed
    $scalar = "scalar";

    # Array to be pushed
    @array = ("a", "r", "r", "a", "y");

    # Hash to be pushed
    %hash = ("Geeks" => 10, 
             "for Geeks" => 20);

    # scalars, arrays and hashes can be
    # inserted at the same time
    splice(@stack, scalar(@stack), 0, 
           ($scalar, @array, %hash));

    # Updated Stack after 
    # Push operations
    print("\nUpdated Stack: @stack");
    ```

    **Output:**

    ```
    Original Stack: 1 2 3
    Updated Stack: 1 2 3 scalar a r r a y Geeks 10 for Geeks 20

    ```

    **Popping elements from a Stack**

    可以使用 pop()函数或拼接()函数进行弹出。

    *   Popping using **pop()**:

        > **语法:**$ popped _ element = pop(@ stack)；
        > T3】参数:
        > 
        > *   函数的作用是:返回弹出的元素。
        > *   $popped_element 包含从堆栈中弹出的元素。

        **示例:**

        ```
        #!/usr/bin/perl

        # Intitialising the Stack
        @stack = (1..3);

        # Original stack
        print "Original Stack: @stack";

        # Topmost element i.e. 3 is 
        # removed and returned
        $popped_element = pop(@stack); 

        # Printing popped element
        print "\nPopped element: $popped_element";

        # Updated Stack after 
        # Pop operation
        print("\nUpdated Stack: @stack");
        ```

        **Output:**

        ```
        Original Stack: 1 2 3
        Popped element: 3
        Updated Stack: 1 2

        ```

        *   If the stack is empty, **undef** is returned. undef is analogous to NULL in Java and None in Python. However, no error is raised.

            **示例:**

            ```
            #!/usr/bin/perl

            # Creating a Stack
            @stack;

            # undef is returned since the 
            # stack is empty. 
            # No error is raised.
            $popped_element = pop(@stack); 

            # Printing popped element
            # Since it contains no value,
            # hence a blank space is returned
            print "Popped element: $popped_element";
            ```

            **Output:**

            ```
            Popped element: 

            ```

    *   Popping using **splice():**:

        > **语法:**$ popped _ element = splice(@ stack，-1)；
        > T3】参数:
        > 
        > *   函数的作用是:移除堆栈的最后一个元素，然后返回。
        > *   $popped_element 存储返回值。

        **示例:**

        ```
        #!/usr/bin/perl

        # Intitialising the Stack
        @stack = (1..3);

        # Original stack
        print "Original Stack: @stack";

        # popping using splice()
        $popped_element = splice(@stack, -1);

        # Printing popped element
        print "\nPopped element: $popped_element";

        # Updated Stack after 
        # Pop operation
        print("\nUpdated Stack: @stack");
        ```

        **Output:**

        ```
        Original Stack: 1 2 3
        Popped element: 3
        Updated Stack: 1 2

        ```

        *   An error is raised, if the stack is empty. The following code raises an error:

            ```
            use warnings;
            #!/usr/bin/perl

            use warnings;

            # Creating a Stack
            @stack;

            # popping using splice()
            # An error is raised here
            $popped_element = splice(@stack, -1); 

            # Printing popped element
            print "\nPopped element: $popped_element";

            # Updated Stack after 
            # Pop operation
            print("\nStack: @stack");
            ```

            **运行时错误:**

            > 在/home/59c 7 c 19979 aa 9e 46564 CD 145 d5fe 5601 . pl 第 6 行的 void 上下文中无用地使用变量。
            > 试图修改不可创建的数组值，下标-1 在/home/59c 7c 19979 aa 9e 46564 CD 145 d5fe 5601 . pl 第 10 行。