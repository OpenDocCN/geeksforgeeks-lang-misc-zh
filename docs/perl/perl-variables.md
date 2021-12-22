# Perl |变量

> 原文:[https://www.geeksforgeeks.org/perl-variables/](https://www.geeksforgeeks.org/perl-variables/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的变量用于在整个程序中存储和操作数据。创建变量时，它会占用内存空间。变量的数据类型有助于解释器分配内存，并决定在保留内存中存储什么。因此，变量可以存储整数、小数或字符串，并为变量分配不同的数据类型。

**Naming of a Variable**

Perl 中的变量可以用特定的数据类型来命名。命名变量时要遵循一些规则:

*   Perl 中的变量区分大小写。

**示例:**

```
$John and $john are two different variables
```

*   根据所需的数据类型，它以$、@或%开头，后跟零个或多个字母、下划线和数字
*   Perl 中的变量不能包含空格或除下划线以外的任何其他特殊字符。

**示例:**

```
$my-name = "John"; // Invalid 
$my name = "John"; // Invalid
$my_name = "John"; // Valid
```

**Declaration of a Variable**

变量声明是基于用于定义变量的数据类型完成的。这些变量可以是三种不同的数据类型:

*   **标量变量:**包含单个字符串或数值。它以$符号开始。

> **语法:**$ var _ name = value；

**示例:**

```
$item = "Hello" 
$item_one = 2
```

*   **数组变量:**它包含一组随机排序的值。它以@符号开头。

> **语法:** @var_name = (val1、val2、val3、……)-好吧)；或

**示例:**

```
@price_list = (70, 30, 40);
@name_list = ("Apple", "Banana", "Guava");
```

*   **散列变量:**它包含每个键有效访问的(键，值)对。它以%符号开始。

> **语法:** %var_name = ( key1= > val1，key2= > val2，key3= > val3，…..);

**示例:**

```
%item_pairs = ("Apple" =>2, "Banana'=>3);
%pair_random = ("Hi" =>8, "Bye"=>9);

```

**Modification of a Variable**

Perl 允许在变量声明完成后随时修改其变量值。变量的修改有多种方式:

*   标量变量可以简单地通过重新定义它的值来修改。

**示例:**

```
$name = "John";

# This can be modified by simply
# redeclaring the variable $name.
$name = "Rahul";
```

*   可以通过将数组元素的索引传递给数组并为其定义新值来修改该元素。

**示例:**

```
@array = ("A", "B", "C", "D", "E");

# If value of second variable is to
# be modified then it can be done by
@array[2] = "4";
# $array[2]  = "4"; is an alternate way of updating value in an array.

# This will change the array to,
# @array = ("A", "B", "4", "D", "E");
```

*   哈希中的值可以通过使用其键来修改。

**示例:**

```
%Hash = ("A", 10, "B", 20, "C", 30)

# This will modify the value 
# assigned to Key 'B'
$Hash{"B"} = 46;
```

**Variable Interpolation**

Perl 提供了各种方法来定义变量的字符串。这可以通过使用单引号、双引号、使用 q 运算符和双 q 运算符等来实现。
使用单引号和双引号编写字符串是一样的，但是它们的工作方式略有不同。使用单引号编写的字符串显示了其中的内容。

**示例:**

```
$name = "John"
print 'Hi $name\nHow are you?' 
```

上面的代码将打印出来:

```
Hi $name\nHow are you?
```

而用双引号括起来的字符串用它们的值替换变量，然后显示字符串。它甚至用它们的实际用途代替了转义序列。
**例:**

```
$name = "John"
print "Hi $name\nHow are you?" 
```

上面的代码将打印出来:

```
Hi John
How are you?
```

**示例代码:**

## Perl 语言

```
#!/usr/bin/perl
use Data::Dumper;

# Scalar Variable
$name = "GeeksForGeeks";

# Array Variable
@array = ("G", "E", "E", "K", "S");

# Hash Variable
%Hash = ('Welcome', 10, 'to', 20, 'Geeks', 40);

# Variable Modification
@array[2] = "F";

print "Modified Array is @array\n";

# Interpolation of a Variable

# Using Single Quote
print 'Name is $name\n';

# Using Double Quotes
print "\nName is $name";

# Printing hash contents
print Dumper(\%Hash);
```

**Output:** 

```
Modified Array is G E F K S
Name is $name\n
Name is GeeksForGeeks$VAR1 = {
          'to' => 20,
          'Welcome' => 10,
          'Geeks' => 40
        };
```