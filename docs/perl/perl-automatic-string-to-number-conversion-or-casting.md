# Perl |自动字符串到数字的转换或转换

> 原文:[https://www . geesforgeks . org/perl-自动字符串到数字的转换或转换/](https://www.geeksforgeeks.org/perl-automatic-string-to-number-conversion-or-casting/)

Perl 有一种不同的方式来处理运算符，因为这里运算符定义了操作数的行为，但是在其他编程语言中，操作数定义了运算符的行为。转换是指将特定变量的数据类型转换为另一种数据类型。例如，如果有一个字符串“1234”，并将其转换为 int 数据类型后，输出将是一个整数 1234。Perl 中字符串到整数的转换有很多种方式。一种是使用 ***打字*** ，另一种是使用 ***冲刺*** 功能。有时人们不在 Perl 中使用单词转换，因为整个转换是自动的。

#### 

打字

当我们将一种数据类型的值赋给另一种数据类型时，就会发生类型转换。如果数据类型兼容，那么 Perl 会进行自动类型转换。如果不兼容，则需要显式转换它们，这称为显式类型转换。有两种类型的类型转换:

*   **Implicit Typecasting:** Implicit type conversion is done by the compiler itself. There is no need for the user to mention a specific type conversion using any method. The compiler on its own determines the data type of the variable if required and fixes it. In Perl when we declare a new variable and assign a value to it, it automatically converts it into a required data type.

    **例 1:**

    ```perl
    # Perl code to demonstrate implicit 
    # type casting

    # variable x is of int type
    $x = 57;

    # variable y is of int type
    $y = 13;

    # z is an integer data type which
    # will contain the sum of x and y
    # implicit or automatic conversion
    $z = $x + $y;

    print "z is ${z}\n";

    # type conversion of x and y integer to 
    # string due to concatenate function
    $w = $x.$y;

    # w is a string which has the value: 
    # concatenation of string x and string y
    print "w is ${w}\n";
    ```

    **输出:**

    ```perl
    z is 70
    w is 5713

    ```

*   **Explicit Typecasting:** In this conversion the user can cast a variable to a particular data type according to requirement. Explicit type conversion is required if the programmer wants a particular variable to be of a particular data type. It is important for keeping the code consistent so that no variable causes an error due to type conversion.

    **示例:**下面执行显式类型转换，其中字符串(或任何数据类型)被转换为指定类型(比如 int)。

    ```perl
    # Perl code to demonstrate Explicit 
    # type casting

    # String type
    $string1 = "27";

    # conversion of string to int 
    # using typecasting int()
    $num1 = int($string1);

    $string2 = "13";

    # conversion of string to int
    # using typecasting int()
    $num2 = int($string2);

    print "Numbers are $num1 and $num2\n";

    # applying arithmetic operators 
    # on int variables 
    $sum = $num1 + $num2;

    print"Sum of the numbers = $sum\n";
    ```

    **输出:**

    ```perl
    Numbers are 27 and 13
    Sum of the numbers = 40

    ```

#### 

sprintf 函数

这个 sprintf 函数返回一个标量值，一个格式化的文本字符串，根据代码进行类型转换。sprintf 命令是一个格式化程序，根本不打印任何东西。

```perl
# Perl code to demonstrate the use 
# of sprintf function

# string type
$string1 = "25";

# using sprintf to convert 
# the string to integer
$num1 = sprintf("%d", $string1);

$string2 = "13";

# using sprintf to convert 
# the string to integer
$num2 = sprintf("%d", $string2);

# applying arithmetic operators
# on int variables 
print "Numbers are $num1 and $num2\n";

$sum = $num1 + $num2;
print"Sum of the numbers = $sum\n";
```

**输出:**

```perl
Numbers are 25 and 13
Sum of the numbers = 38

```