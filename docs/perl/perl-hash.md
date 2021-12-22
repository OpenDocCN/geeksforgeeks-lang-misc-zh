# perl 散列

> 原文:[https://www.geeksforgeeks.org/perl-hash/](https://www.geeksforgeeks.org/perl-hash/)

一个[散列](https://www.geeksforgeeks.org/perl-hashes/)是一组键值对。Perl 存储散列的元素，这样它就可以根据关键字搜索值。哈希变量以“%”符号开头。

Perl 要求散列的键是字符串，而值可以是任何[标量](https://www.geeksforgeeks.org/perl-scalars/)。这些值可以是数字、字符串或引用。如果使用非字符串值作为键，会产生意外的结果。

哈希键必须是唯一的。如果一个新的键值对被添加到一个散列中，并且该键是存在的，那么它的相应值将被覆盖。

**Creating Hashes**

有许多方法可以初始化散列变量，如下所示:

*   该值直接赋值，如下所示，并将数据添加到现有的哈希中。

```
$stud{'Comp'} = 45;
$stud{'Inft'} = 42;
$stud{'Extc'} = 35;
```

*   另一种方法是使用列表，通过获取单个对将列表转换为散列。该对的第一个元素用作键，第二个元素用作值。

```
%stud = ('Comp', 45, 'Inft', 42, 'Extc', 35);
```

*   一种方法是使用 **= >** 来表示键/值对，如下所示:

```
%stud = ('Comp' => 45, 'Inft' => 42, 'Extc' => 35);
```

*   做同样事情的另一种方法如下所示。这里所有的键前面都有连字符(-)所以不需要引号。只有当单词中没有空格时，才能使用此方法构建哈希。

```
%stud = (-Comp => 45, -Inft => 42, -Extc => 35);
```

**Accessing Hash Elements**

为了从散列中访问单个元素，变量以美元符号($)作为前缀，然后在变量名称后的大括号内追加元素键。

以下示例说明了如上所述的所有哈希创建方法:

**示例:**

## Perl 语言

```
#!/usr/bin/perl

# Initializing Hash1 by
# directly assigning values
$stud1{'Comp'} = 10;
$stud1{'Inft'} = 20;
$stud1{'Extc'} = 30;

# printing elements of stud
print "Printing values of Hash1\n";
print "$stud1{'Comp'}\n";
print "$stud1{'Inft'}\n";
print "$stud1{'Extc'}\n";

# Initializing Hash2 by taking
# individual pairs
%stud2 = ('Comp', 15, 'Inft', 18, 'Extc', 22);

# Extracting values using keys
print "\nPrinting values of Hash2\n";
print "computer = $stud2{'Comp'}";
print "\ninft = $stud2{Inft}";
print "\nextc = $stud2{'Extc'}\n";

# Initializing Hash3 using '=>'
%stud3 = ('Comp' => 45, 'Inft' => 42, 'Extc' => 35);

# printing elements of stud3
print "\nPrinting values of Hash3\n";
print "$stud3{'Comp'}\n";
print "$stud3{'Inft'}\n";
print "$stud3{'Extc'}\n";

# Initializing Hash4 using hyphen(-)
%stud4 = (-Comp => 5, -Inft => 15, -Extc => 25);

# Printing elements of stud4
print "\nPrinting values of Hash4\n";
print "$stud4{'-Comp'}\n";
print "$stud4{'-Inft'}\n";
print "$stud4{'-Extc'}";
```

**Output:** 

```
Printing values of Hash1
10
20
30

Printing values of Hash2
computer = 15
inft = 18
extc = 22

Printing values of Hash3
45
42
35

Printing values of Hash4
5
15
25
```

**Extracting Keys and Values**

有时需要提取散列的键和值来对其执行各种操作。元素修改、删除、添加等操作。Hash 允许使用内置函数提取这些键和值。
使用 [**键**](https://www.geeksforgeeks.org/perl-keys-function/) 功能可以从散列中获得所有键的列表。

> **语法:**键%HASH
> 返回 HASH 中存在的所有键的数组

**示例:**

## Perl 语言

```
# Initializing Hash with Key-Value pairs
%stud = ('Comp' => 45, 'Inft' => 42, 'Extc' => 35);

# Extracting keys from hash
@Key_array = keys %stud;

# Printing the extracted keys
print "Keys are :\n";
print "$Key_array[0]\n";
print "$Key_array[1]\n";
print "$Key_array[2]\n";
```

**输出:**

```
Keys are :
Comp
Extc
Inft
```

同样的， [**值**](https://www.geeksforgeeks.org/perl-values-function/) 函数用来获取所有值的列表。

> **语法:**值%HASH
> 返回一个包含所有 HASH 值的数组

**示例:**

## Perl 语言

```
# Initializing Hash with Key-Value pairs
%stud = ('Comp' => 45, 'Inft' => 42, 'Extc' => 35);

# Extracting values from hash
@value_array = values %stud;

# Printing the extracted values
print "Values are :\n";
print "$value_array[0]\n";
print "$value_array[1]\n";
print "$value_array[2]\n";
```

**Output:** 

```
Values are :
45
35
42
```