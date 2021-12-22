# Perl |运算符| Set–2

> 原文:[https://www.geeksforgeeks.org/perl-operators-set-2/](https://www.geeksforgeeks.org/perl-operators-set-2/)

运算符是任何编程语言的主要构件。运算符允许程序员对操作数执行不同类型的操作。在 Perl 中，运算符符号对于不同类型的操作数是不同的(比如[标量](https://www.geeksforgeeks.org/perl-scalars/)和字符串)。一些运算符已经在 [**Perl 运算符集–1**](https://www.geeksforgeeks.org/perl-operators-set-1/)中讨论过。本文将讨论其余的运算符:

*   [引用类似操作符](#Quote Like Operators)
*   [串操纵操作器](#String Manipulation Operators)
*   [范围操作员](#Range Operator)
*   [自动递增&递减运算符](#Auto Increment & Decrement Operator)
*   [箭头操作器](#Arrow Operator)

#### 类似引号的运算符

在这些运算符中，{}将代表用户选择的一对分隔符。在此类别中，有以下三种运算符:

*   **q{ }** :它会用单引号将字符串括起来**(”**)并且不能对字符串变量进行插值。*例如:* q{geek}给出‘geek’。
*   **qq{ }** :将一个字符串括在双引号 **("")** 中，可以对字符串变量进行插值。*例如:* qq{geek}给出“geek”。
*   **qx{ }** :它会在反引号**()**中括起一个字符串。*例如:* qq{geek}给出‘geek’。

**示例:**

## Perl 语言

```
# Perl program to demonstrate the Quote
# Like Operators

#!/usr/local/bin/perl

# taking a string variable
$g = "Geek";

# using single quote Operators
# this operator will not
# interpolate the string variable
$r = q{$g};

print "Value of g is = $r\n";

# using double quote Operators
# this operator will interpolate
# the string variable
$r = qq{$g};

print "Value of g is = $r\n";

# Executing unix date command
$d = qx{date};

print "Value of qx{date} = $d";
```

**输出:**

```
Value of g is = $g
Value of g is = Geek
Value of qx{date} = Sun Aug 12 14:19:43 UTC 2018
```

**串操纵操作器**

字符串是标量变量，在 Perl 中以 **($)** 符号开始。字符串由用户在单引号**()**或双引号 **("")** 中定义。Perl 中有不同类型的字符串运算符，如下所示:

*   **串联运算符(。)** : Perl 字符串用一个**点(。)**符号。点(。)符号代替了 Perl 中的(+)符号。
*   **重复运算符(x):**x 运算符的左侧接受一个字符串，右侧接受一个数字。它将返回左侧的字符串，重复次数与右侧的值相同。

**示例:**

## Perl 语言

```
# Perl program to demonstrate the
# string operators

#!/usr/bin/perl

# Input first string
$first_string = "Geeks";

# Input second string
$second_string = "forGeeks";

# Implement Concatenation operator(.)
$concat_string = $first_string.$second_string;

# displaying concatenation string result
print "Result of Concatenation Operator = $concat_string\n";

# Input a string
$string = "GeeksforGeeks ";

# Using Repetition operator(x)
$str_result = $string x 4;

# Display output
# print string 4 times
print "Result of Repetition Operator = $str_result";
```

**输出:**

```
Result of Concatenation Operator = GeeksforGeeks
Result of Repetition Operator = GeeksforGeeks GeeksforGeeks GeeksforGeeks GeeksforGeeks 
```

**注:**想了解更多 Perl 中的字符串运算符，可以参考 [**Perl 字符串运算符**](https://www.geeksforgeeks.org/perl-string-operators/) 一文。

#### 范围运算符(..)

在 Perl 中，range 运算符用于创建指定元素的指定序列范围。所以这个操作符被用来创建一个指定的序列范围，其中开始和结束元素都包含在内。*例如* 7..10 会产生一个类似 7，8，9，10 的序列。
T3】例:

## Perl 语言

```
# Perl program to demonstrate the
# Range operators

#!/usr/bin/perl

# using range operator 
@res = (1..4);

# Display output
print "Result of Range Operator = @res";
```

**输出:**

```
Result of Range Operator = 1 2 3 4
```

#### 自动递增和自动递减运算符

**自动递增(++):** 递增整数值。当放在变量名(也称为预递增运算符)之前时，其值会立即递增。例如，++$x。当它被放在变量名(也称为后递增运算符)之后时，它的值会被暂时保留，直到执行这个语句，并且在执行下一个语句之前会被更新。例如，$x++。
**自动递减运算符(–):**递减整数值。当放在变量名(也称为预递减运算符)之前时，其值会立即递减。例如–$ x。当它被放在变量名(也称为后递减运算符)之后时，它的值会被暂时保留，直到执行该语句，并在执行下一个语句之前被更新。例如，$ x–。
**注意:**递增和递减运算符称为一元运算符，因为它们使用单个操作数。
**示例:**

## Perl 语言

```
# Perl program to demonstrate the Auto
# Increment and Decrement Operator

#!/usr/local/bin/perl

# taking a  variable
$g = 10;

# using pre Increment
$res = ++$g;

print "Value of res is = $res\n";
print "Value of g is = $g\n";

# taking a  variable
$g1 = 15;

# using post Increment
$res1 = $g1++;

print "Value of res1 is = $res1\n";
print "Value of g1 is = $g1\n";

# taking a  variable
$g2 = 20;

# using pre Decrement
$res2 = --$g2;

print "Value of res2 is = $res2\n";
print "Value of g2 is = $g2\n";

# taking a  variable
$g3 = 25;

# using post Decrement
$res3 = $g3--;

print "Value of res3 is = $res3\n";
print "Value of g3 is = $g3\n";
```

**输出:**

```
Value of res is = 11
Value of g is = 11
Value of res1 is = 15
Value of g1 is = 16
Value of res2 is = 19
Value of g2 is = 19
Value of res3 is = 25
Value of g3 is = 24
```

#### 箭头运算符(-->)

此运算符用于从类或对象中取消引用变量或方法。示例:$ob->$x 是从对象$ob 访问变量$x 的示例。这个操作符通常被用作散列或数组的引用，以访问散列或数组的元素。
**例:**

## Perl 语言

```
# Perl program to demonstrate the Arrow Operator

#!/usr/local/bin/perl

use strict;
use warnings;

# reference to array
my $arr1 = [4,5,6];

# array inside array
my $arr2 = [4,5,[6,7]];

# reference to hash
my $has1 = {'a'=>1,'b'=>2};

# hash inside hash
my $has2 = {'a'=>1,'b'=>2,'c'=>[1,2],'d'=>{'x'=>3,'y'=>4}};

# using arrow operator
print "$arr1->[0]\n";
print "$arr2->[1]\n";
print "$arr2->[2][0]\n";
print "$has2->{'a'}\n";
print $has2->{'d'}->{'x'},"\n";
print $has2->{'c'}->[0],"\n";
```

**输出:**

```
4
5
6
1
3
1
```

**需要记住的要点:**

1.  **运算符关联性:**用于决定等式或表达式是从左到右还是从右到左求值。评价的顺序很重要。有时从两边看起来可能都一样，但会产生很大的差异。
2.  **Perl Arity:**Arity 可以定义为运算符操作的操作数的数量。
    *   **空运算符**:这些运算符对零操作数进行运算。
    *   **一元运算符:**这些运算符对一个操作数进行运算。
    *   **二元运算符:**这些运算符对两个操作数进行运算。
    *   **列表运算符:**这些运算符对操作数列表进行运算。
3.  **Perl Fixity:** 可以定义为运算符相对于其操作数的位置。
    *   **中缀运算符:**这些运算符位于其操作数之间。例如，5 + 8，这里，+运算符位于操作数 5 和 8 之间
    *   **前缀运算符:**这些运算符位于其操作数之前。比如，！$g，–7，这里，！and–运算符位于操作数$a 和$ 3 之前。
    *   **后缀运算符:**这些运算符出现在其操作数之后。例如，$y ++，这里，+++运算符出现在操作数$x 之后。
    *   **扬抑符:**这些运算符将其操作数像散列构造函数和引用运算符一样括起来。例如，(qq[..])
    *   **后置运算符:**这些运算符跟在某些操作数后面，包围某些操作数。例如，$hash{$y}

#### 运算符优先级和关联性表

<figure class="table">

| 操作员 | 优先 | 结合性 |
| -> | 箭头运算符 | 从左到右 |
| ++, — | 增量、减量 | 非联想的 |
| ** | 指数 | 从右向左 |
| ！, +, -, ~ | 非，一元正，一元负，补码 | 从右向左 |
| ！=, ~= | 不等于，补足等于 | 从左到右 |
| *, /, % | 乘法、除法、模数 | 从左到右 |
| <> | 移位运算符 | 从左到右 |
| <>，<=, > = | 比较，小于等于，右小于等于 | 非联想的 |
| & | 按位“与” | 从左到右 |
| &#124;, ^ | 按位或、异或 | 从左到右 |
| && | 和 | 从左到右 |
| &#124;&#124; | 运筹学 | 从左到右 |
| .. | 距离操作手 | 非联想的 |
| *=, /=, +=, -= | 乘等于，除等于，加等于 | 从右向左 |

</figure>