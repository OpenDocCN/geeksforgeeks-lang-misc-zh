# Perl |数字及其类型

> 原文:[https://www.geeksforgeeks.org/perl-number-and-its-types/](https://www.geeksforgeeks.org/perl-number-and-its-types/)

Perl 中的数字是一个数学对象，用于计数、测量和执行各种数学运算。代表数字的符号称为数字。这些数字除了用于数学运算外，还用于排序(以序列号的形式)。

**示例:**

```perl
1, 2, -4, 5.6, -7.9, 057, 1.67e-10, 0xFFFF
```

这些数字根据其用途可以分为不同的类型:

*   **整数:** Perl 整数表示为以 10 为基数的十进制数。这些数字可以是正数，也可以是负数。但是，Perl 使用“_”来表示大整数，以增加可读性。

    > **示例:** 123，154，454 表示为 123 _ 154 _ 454

    ```perl
    #!/usr/bin/perl

    # Positive Integer
    $x = 20;

    # Negative Integer
    $y = -15;

    # Big Integer Number
    $z = 123_154_454;

    # Printing these numbers
    print("Positive Integer: ", $x, "\n");

    print("Negative Integer: ", $y, "\n");

    print("Big Integer: ", $z, "\n");
    ```

    **输出:**

```perl
Positive Integer: 20
Negative Integer: -15
Big Integer: 123154454

```