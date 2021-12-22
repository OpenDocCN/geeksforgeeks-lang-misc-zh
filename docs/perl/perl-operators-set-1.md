# Perl |运算符| Set–1

> 原文:[https://www.geeksforgeeks.org/perl-operators-set-1/](https://www.geeksforgeeks.org/perl-operators-set-1/)

运算符是任何编程语言的主要构件。运算符允许程序员对操作数执行不同类型的操作。在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中，不同类型的操作数(如标量和字符串)的运算符符号会有所不同。操作员可以根据其不同的功能进行分类:

*   [<u>算术运算符</u>](https://www.geeksforgeeks.org/perl-operators-set-1/#Arithmetic%20Operators)
*   [<u>关系运算符</u>](https://www.geeksforgeeks.org/perl-operators-set-1/#Relational%20Operators)
*   [<u>逻辑运算符</u>](https://www.geeksforgeeks.org/perl-operators-set-1/#Logical%20Operators)
*   [<u>逐位运算符</u>](https://www.geeksforgeeks.org/perl-operators-set-1/#Bitwise%20Operators)
*   [<u>分配操作员</u>](https://www.geeksforgeeks.org/perl-operators-set-1/#Assignment%20Operators)
*   [<u>三元算子</u>](https://www.geeksforgeeks.org/perl-operators-set-1/#Ternary%20Operator)

**算术运算符**

这些用于对操作数执行算术/数学运算。

*   **加法:** ' *+* '运算符用于将两个操作数的值相加。例如:

```perl
$a = 5;
$b = 10;
print $a + $b;
Here Result will be 15
```

*   **减法:**'*–*'运算符用于从左手操作数中减去右手操作数。例如:

```perl
$a = 10;
$b = 5;
print $a - $b;
Here Result will be 5
```

*   **乘法:** ' *** '运算符用于将运算符两侧的值相乘。例如:

```perl
$a = 5;
$b = 10;
print $a * $b;
Here Result will be 50
```

*   **除法运算符:** ' */* '运算符在第一个操作数除以第二个操作数时返回余数。例如:

```perl
$a = 30;
$b = 15;
print $a / $b;
Here Result will be 3
```

*   **模数运算符:** ' *%* '运算符用于将左操作数与右操作数相除，并返回余数。例如:

```perl
$a = 10;
$b = 15;
print $a % $b;
Here Result will be 5
```

*   **指数运算符:** ' **** '运算符用于对操作数进行指数(幂)计算。例如:

```perl
$a = 2;
$b = 3;
print $a**$b;
Here Result will be 8
```

**程序:**演示算术运算符

## Perl 语言

```perl
# Perl Program to illustrate the Arithmetic Operators

# Operands
$a = 10;
$b = 4;

# using arithmetic operators
print "Addition is: ", $a + $b, "\n";
print "Subtraction is: ", $a - $b, "\n" ;
print "Multiplication is: ", $a * $b, "\n";
print "Division is: ", $a / $b, "\n";
print "Modulus is: ", $a % $b, "\n";
print "Exponent is: ", $a ** $b, "\n";
```

**输出:**

```perl
Addition is: 14
Subtraction is: 6
Multiplication is: 40
Division is: 2.5
Modulus is: 2
Exponent is: 10000
```

**关系运算符**

关系运算符用于比较两个值。这些运算符将返回 1 **(真)或 0(假)**。有时这些操作员也被称为**平等操作员**。这些运算符有不同的符号来操作字符串。要了解比较运算符在字符串上的操作，可以参考 [**这个**](https://www.geeksforgeeks.org/perl-comparing-scalars/) 。

*   **等于运算符:“= =”**检查两个值是否相等。如果等于，则返回 1，否则不返回任何内容。
*   **不等于运算符:“！='** 检查两个值是否相等。如果不相等，则返回 1，否则不返回任何内容。
*   **等于运算符的比较:'< = > '** 如果左操作数小于右操作数，则返回-1，如果等于则返回 0，否则返回 1。
*   **大于运算符:“>”**如果左操作数大于右操作数，则返回 1，否则不返回任何内容。
*   **小于运算符:“<”**如果左操作数小于右操作数，则返回 1，否则不返回任何内容。
*   **大于等于运算符:“>=”**如果左操作数大于或等于右操作数，则返回 1，否则不返回任何内容。
*   **小于等于运算符:“<=”**如果左操作数小于或等于右操作数，则返回 1，否则不返回任何内容。

**程序:**说明 Perl 中的关系运算符

## Perl 语言

```perl
# Perl Program to illustrate the Relational Operators

# Operands
$a = 10;
$b = 60;

# using Relational Operators
if ($a == $b)
{
   print "Equal To Operator is True\n";
}
else
{
   print "Equal To Operator is False\n";
}

if ($a != $b)
{
   print "Not Equal To Operator is True\n";
}
else
{
   print "Not Equal To Operator is False\n";
}

if ($a > $b)
{
   print "Greater Than Operator is True\n";
}
else
{
   print "Greater Than Operator is False\n";
}

if ($a < $b)
{
   print "Less Than Operator is True\n";
}
else
{
   print "Less Than Operator is False\n";
}

if ($a >= $b)
{
   print "Greater Than Equal To Operator is True\n";
}
else
{
   print "Greater Than Equal To Operator is False\n";
}

if ($a <= $b)
{
   print "Less Than Equal To Operator is True\n";
}
else
{
   print "Less Than Equal To Operator is False\n";
}
if ($a <=> $b)
{
   print "Comparison of Operator is True\n";
}
else
{
   print "Comparison of Operator is False\n";
}
```

**输出:**

```perl
Equal To Operator is False
Not Equal To Operator is True
Greater Than Operator is False
Less Than Operator is True
Greater Than Equal To Operator is False
Less Than Equal To Operator is True
Comparison of Operator is True
```

**逻辑运算符**

这些运算符用于组合两个或多个条件/约束，或者补充所考虑的原始条件的评估。

*   **逻辑与:**当所考虑的两个条件都满足时，**和**运算符返回真。例如，当 a 和 b 都为真(即非零)时，a 和 b 都为真。也可以使用 **& &** 。
*   **逻辑或:**当所考虑的条件中的一个(或两个)满足时，运算符“**或“**”返回真。例如，如果 a 或 b 中的一个为真(即非零)，则$a 或$b 为真。当然，当 a 和 b 都为真时，它给出的结果是“真”。也可以使用 **||**
*   **逻辑非:**如果满足所考虑的条件，“非”运算符将给出 1。例如，如果$d 为 0，not($d)为真。

**程序:**演示逻辑运算符的工作原理:

## Perl 语言

```perl
# Perl Program to illustrate the Logical Operators

# Operands
$a = true;
$b = false;

# AND operator
$result = $a && $b;
print "AND Operator: ", $result,"\n";

# OR operator
$result = $a || $b;
print "OR Operator: ", $result,"\n";

# NOT operator
$d = 0;
$result = not($d);
print "NOT Operator: ", $result;
```

**输出:**

```perl
AND Operator: false
OR Operator: true
NOT Operator: 1
```

**按位运算符**

这些运算符用于执行按位运算。它首先将数字转换为位，并对操作数执行位级操作。

*   **&(按位“与”)**将两个数字作为操作数，并对两个数字的每一位进行“与”。仅当两位都为 1 时，“与”的结果才为 1。例如

```perl
$a = 13;    // 1101
$b = 5;   //  0101
$c = $b & $a;   
print $c;
Here Output will be 5

Explanation:

$a = 1 1 0 1
$b = 0 1 0 1
---------------
$c = 0 1  0 1
---------------
```

*   **|(按位“或”)**将两个数字作为操作数，并对两个数字的每一位进行“或”。“或”的结果是 1，两位中的任何一位都是 1。例如

```perl
$a = 13;    // 1101
$b = 5;     // 0101
$c = $b | $a;   
print $c;
Here Output will be 13

Explanation:
$a = 1 1 0 1
$b = 0 1 0 1
---------------
$c = 1 1  0 1
---------------
```

*   **^(按位异或)**将两个数字作为操作数，并对两个数字的每一位进行异或运算。如果两位不同，异或的结果是 1。例如

```perl
$a = 13;  // 1101
$b = 5;   // 0101
$c = $b ^ $a;
print $c;
Here Output will be 9

Explanation:
$a = 1 1 0 1
$b = 0 1 0 1
-------------
$c = 1 0 0 1
-------------
```

*   **~(补码运算符)**这是一元运算符，充当翻转位。它的工作是反转位，并由于有符号的二进制数而使用 2 的补码形式给出结果。
*   **( < <)二进制左移位运算符**将取两个数字，左移位第一个操作数的位，第二个操作数决定移位的位数。它将左操作数乘以右操作数指定的次数。例如:

```perl
$a = 60;
$c = $a << 2;
print $c;

Output: 240

Explanation:
60 * 2  =  120 ---(1)
120 * 2 = 240  ---(2)
```

*   **( > >)二进制右移运算符**取两个数，右移第一个操作数的位，第二个操作数决定移位的位数。它将左操作数除以右操作数指定的次数。例如:

```perl
$a = 60;
$c = $a >> 2;
print $c;
Output: 15

Explanation:
60 / 2   = 30   ---(1)
30 / 2   =  15  ---(2)
```

**程序:**演示按位运算符的工作原理:

## Perl 语言

```perl
# Perl Program to illustrate the Bitwise operators
#!/usr/local/bin/perl
use integer;

# Operands
$a = 80;
$b = 2;

# Bitwise AND Operator
$result = $a & $b;
print "Bitwise AND: ", $result, "\n";

# Bitwise OR Operator
$result = $a | $b;
print "Bitwise OR: ", $result, "\n";

# Bitwise XOR Operator
$result = $a ^ $b;
print "Bitwise XOR: ", $result, "\n";

# Bitwise Complement Operator
$result = ~$a;
print "Bitwise Complement: ", $result, "\n";

# Bitwise Left Shift Operator
$result = $a << $b;
print "Bitwise Left Shift: ", $result, "\n";

# Bitwise Right Shift Operator
$result = $a >> $b;
print "Bitwise Right Shift: ", $result, "\n";
```

**输出:**

```perl
Bitwise AND: 0
Bitwise OR: 82
Bitwise XOR: 82
Bitwise Complement: -81
Bitwise Left Shift: 320
Bitwise Right Shift: 20
```

**分配操作员**

赋值运算符用于给变量赋值。赋值运算符的左侧操作数是一个变量，而赋值运算符的右侧操作数是一个值。
不同类型的赋值运算符如下所示:

*   **"= "(简单赋值)**:这是最简单的赋值运算符。该运算符用于将右边的值赋给左边的变量。
    例:

```perl
$a = 10;
$b = 20;
```

*   **“+=”(添加赋值)**:这个运算符是“+”和“=”运算符的组合。该运算符首先将左边变量的当前值与右边的值相加，然后将结果赋给左边的变量。
    例:

```perl
($a += $b) can be written as ($a = $a + $b)
```

*   如果最初存储在 a 中的值是 5。然后($a += 6) = 11。
*   **"-= "(减法赋值)**:这个运算符是'-'和' = '运算符的组合。该运算符首先从右边的值中减去左边变量的当前值，然后将结果赋给左边的变量。
    例:

```perl
($a -= $b) can be written as ($a = $a - $b)
```

*   如果最初存储在 a 中的值是 8。然后($a -= 6) = 2。
*   **"*= "(乘法赋值)**:该运算符是' * '和' = '运算符的组合。该运算符首先将左边变量的当前值乘以右边的值，然后将结果赋给左边的变量。
    例:

```perl
($a *= $b) can be written as ($a = $a * $b)
```

*   如果最初存储在 a 中的值是 5。然后($a *= 6) = 30。
*   **"/= "(除法赋值)**:这个运算符是'/'和' = '运算符的组合。该运算符首先将左边变量的当前值除以右边的值，然后将结果赋给左边的变量。
    例:

```perl
($a /= $b) can be written as ($a = $a / $b)
```

*   如果最初存储在 a 中的值是 6。然后($a /= 2) = 3。
*   **“% =”(模数赋值)**:这个运算符是“%”和“=”运算符的组合。该运算符首先用右边的值对左边变量的当前值取模，然后将结果赋给左边的变量。
    示例:

```perl
($a %= $b) can be written as ($a = $a % $b)
```

*   如果最初存储在 a 中的值是 6。然后($a %= 2) = 0。
*   **“** =”(指数赋值)**:这个运算符是“* *”和“=”运算符的组合。该运算符首先用右边的值对左边变量的当前值进行指数运算，然后将结果赋给左边的变量。
    例:

```perl
($a **= $b) can be written as ($a = $a ** $b)
```

*   如果最初存储在 a 中的值是 6。然后($a **= 2) = 36。

**程序:**演示分配操作员的工作

## Perl 语言

```perl
# Perl program to demonstrate the working
# of Assignment Operators
#!/usr/local/bin/perl

# taking two variables & using
# simple assignments operation
$a = 8;
$b = 5;

# using Assignment Operators
print "Addition Assignment Operator: ", $a += $b, "\n";

$a = 8;
$b = 4;
print "Subtraction Assignment Operator: ", $a -= $b, "\n" ;

$a = 8;
$b = 4;
print "Multiplication Assignment Operator: ", $a*=$b, "\n";

$a = 8;
$b = 4;
print "Division Assignment Operator: ",$a/=$b, "\n";

$a = 8;
$b = 5;
print "Modulo Assignment Operator: ", $a%=$b,"\n";

$a = 8;
$b = 4;
print "Exponent Assignment Operator: ", $a**=$b, "\n";

```

**输出:**

```perl
Addition Assignment Operator: 13
Subtraction Assignment Operator: 4
Multiplication Assignment Operator: 32
Division Assignment Operator: 2
Modulo Assignment Operator: 3
Exponent Assignment Operator: 4096
```

**三元运算符**

它是一个条件运算符，是 if-else 语句的简写版本。它有三个操作数，因此得名三元。它将根据布尔表达式的值返回两个值之一。

**语法:**

```perl
condition ? first_expression : second_expression;
```

**说明:**

```perl
*condition:* It must be evaluated to true or false.
If the condition is true
first_expression is evaluated and becomes the result.
If the condition is false,
second_expression is evaluated and becomes the result.
```

**示例:**

## Perl 语言

```perl
# Perl program to demonstrate the working
# of Ternary Operator

$x = 5;
$y = 10;

# To find which value is greater
# Using Ternary Operator
$result = $x > $y ? $x : $y;

# displaying the output
print "The Larger Number is: $result"      
```

**输出:**

```perl
The Larger Number is: 10
```

**注:**在三元运算符中，条件也可以是使用关系运算符、逻辑运算符等不同运算符所构成的任何表达式。

**示例:**

## Perl 语言

```perl
# Perl program to demonstrate the working
# of Ternary Operator by using expression
# as the condition

# here maximum value can be 100
$MAX_VALUE = 100;

# suppose user provide value
$user_value = 444;

# To find which whether user provided
# value is satisfying the maximum value
# or not by using Ternary Operator
$result = $user_value <= $MAX_VALUE ? $user_value : $MAX_VALUE;

# displaying the output
# Here it will be MAX_VALUE
print "$result"     
```

**输出:**

```perl
100
```