# Perl |字符串运算符

> 原文:[https://www.geeksforgeeks.org/perl-string-operators/](https://www.geeksforgeeks.org/perl-string-operators/)

运算符是任何编程语言的基础。因此，如果不使用运算符，Perl 编程语言的功能是不完整的。用户可以将运算符定义为有助于对操作数执行特定数学和逻辑计算的符号。字符串是 [**标量**](https://www.geeksforgeeks.org/perl-scalars/) 变量，在 Perl 中以 **($)** 符号开始。字符串由用户在**单引号(')**或**双引号(")**中定义。Perl 中有不同类型的字符串运算符，如下所示:

*   **串联运算符(。)**
*   **重复运算符(x)**
*   **自动递增运算符(++)**

串联运算符(。)

Perl 字符串用一个**点(。)**符号。点(。)符号代替了 Perl 中的(+)符号。该运算符将两个标量变量作为操作数，并将它们组合成一个标量变量。两个标量，即左和右，将转换成一个字符串。
**例:**

## Perl 语言

```
# Perl program to demonstrate the
# Concatenation Operator(.) in String

#!/usr/bin/perl

# Input first string
$first_string = "Geeks";

# Input second string
$second_string = "forGeeks";

# Implement Concatenation operator(.)
$concat_string = $first_string.$second_string;

# displaying concatenation string result
print "String After Concatenation = $concat_string\n";
```

**输出:**

```
String After Concatenation = GeeksforGeeks
```

重复运算符(x)

x 运算符的左侧接受一个字符串，右侧接受一个数字。它将返回左侧的字符串，重复次数与右侧的值相同。重复取决于用户输入的数字。
**语法:**

```
"String" x number_of_times 
```

**示例:**

## Perl 语言

```
# Perl program to demonstrate the
# Repetition Operator (x) in String

#!/usr/bin/perl

# Input a string
$string = "GeeksforGeeks ";

# Repetition operator(x)
$str_result = $string x 5;

# Display output
# print string 5 times
print "$str_result";
```

**输出:**

```
GeeksforGeeks GeeksforGeeks GeeksforGeeks GeeksforGeeks GeeksforGeeks 
```

**注意:**在字符串中使用重复运算符(x)时可能出现的情况如下:

*   *$字符串 xnumber* :给出输出
*   *$字符串 x 数字*:给出输出
*   *$stringxnumber* :给出错误(字符串和 x 之间没有空格)
*   *$stringx 数字*:给出错误(字符串和 x 之间没有空格)

**需要记住的要点:**串联和重复运算符都可以与赋值(=)运算符一起使用，如下所示:

*   **串联赋值运算符(。=)**
*   **重复赋值运算符(x=)**

**示例:**

## Perl 语言

```
# Perl program to demonstrate the
# Concatenation and Repetition
# Assignment Operator in String

#!/usr/bin/perl

# Input first string
$string1 = "Geeks";

# Input second string
$string2 = "forgeeks"; 

$combine = $string1;  

# combine two string function (.=)
$combine .= $string2; 

# Display result
print $combine;

$str_result = "Sudo_Placements";

# Repetition operator(x)
$str_result x= 5;

# Display output
# print string 5 times
print "\n$str_result";
```

**输出:**

```
Geeksforgeeks
Sudo_PlacementsSudo_PlacementsSudo_PlacementsSudo_PlacementsSudo_Placements
```

自动递增运算符(++)

该运算符也可以应用于字符串。它是一元运算符，这就是为什么它只接受一个操作数作为字符串。使用字符的 ASCII 值，操作数(即字符串)的最后一个字符将增加 1。关于*+*运算符需要记住的重要一点是，如果字符串以 *'z '或【Z'* 结尾，那么++运算符的结果将分别是 *'a '或' A'* ，但其左边的字母也将递增 1。
**例:**

## Perl 语言

```
# Perl program to demonstrate
# Auto-increment Operator (++)

#!/usr/bin/perl

# Input  string
$st = "AYY";

$st++;

# Display output
print "After ++ : $st";

# Once again 
$st++;

# Display output
print "\nAgain After ++ : $st";
```

**输出:**

```
After ++ : AYZ
Again After ++ : AZA
```