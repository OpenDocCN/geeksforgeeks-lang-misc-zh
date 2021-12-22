# Perl | Hashes

> 原文:[https://www.geeksforgeeks.org/perl-hashes/](https://www.geeksforgeeks.org/perl-hashes/)

一组**键/值**对被称为哈希。哈希结构中的每个键都是唯一的，并且是类型字符串。与这些键相关联的值是 [**标量**](https://www.geeksforgeeks.org/perl-scalars/) 。这些值可以是数字、字符串或引用。哈希是使用 **my** 关键字声明的。变量名前面是美元**符号($)** ，后面是花括号下的键和与该键关联的值。每个键都与一个值相关联。
**例:**

```
my%rateof{mango} = 45;
```

**问题出现了什么时候用 Array，什么时候用 Hashes？**

*   如果事情是有序的，那么去数组。例如:

```
1\. A list of people in a bank queue.
2\. A list of people in railway reservation line.
3\. A list of files to read.
```

*   如果我们拥有的东西不合适，那就去找哈希吧。例如:

```
1\. An index of surname looked up by the first name.
2\. An index showing the size of files looked up by name.
```

**空散列:**没有任何键的散列变量称为**空散列**。

*   **例:**

```
my %rateof;
```

*   这里的*速率是散列变量。*

**将键/值对插入哈希:**键总是字符串类型，值总是标量类型。

*   **例:**

```
$rateof{'mango'} = 45; 
```

*   这里的关键是芒果，数值是 45。

**哈希的初始化&获取哈希的元素:**哈希变量可以在其声明期间用键/值对进行初始化。有两种方法可以初始化散列变量。一种是使用 **= >** ，称为*胖箭*或*胖逗号*。第二种是将键/值对放入由逗号(，)分隔的*双引号("")中。使用粗逗号提供了另一种选择，因为您可以在键周围留下双引号。
要从散列中访问单个元素，可以使用美元符号($)后跟散列变量，再跟花括号下的键。在访问键/值对时，如果您传递了不存在的键，那么它将返回一个未定义的值，或者如果您打开了警告，它将显示警告。* 

*   **例:**

## Perl 语言

```
# Perl program to demonstrate the
# Fetching an element of a Hash

# creating hash
%rateof = ('Mango' => 45, 'Orange' => 30, 'Grapes' => 40);

# Fetching an element of Hash
print "$rateof{'Mango'}\n";
print "$rateof{'Orange'}\n";
print "$rateof{'Grapes'}\n";
```

*   **输出:**

```
45
30
40
```

*   **解释:**要访问芒果、橙子、葡萄三个键，并打印与之相关的值，只需使用美元符号后跟键。print 语句将打印与该键关联的值。

**散列中的空值:**通常，不能将空值分配给散列的键。但是在 Perl 中，有一种方法可以为 Hashes 提供空值。通过使用 [**取消**](https://www.geeksforgeeks.org/perl-undef-and-the-defined-function/) 功能。“undef”可以根据用户的需要分配给新的或现有的密钥。将 undef 放在双引号中会使其成为字符串而不是空值。

## Perl 语言

```
# Perl program to demonstrate the
# empty values of a Hash

#use warnings;

# creating hash
%rateof = ('Mango' => 45, 'Orange' => undef, 'Grapes' => 40);

# Fetching an element of Hash
print "$rateof{'Mango'}\n";
print "$rateof{'Orange'}\n";
print "$rateof{'Grapes'}\n";
```

**输出:**

```
45

40
```

**迭代散列:**要访问散列中的值，用户必须知道与该值相关联的密钥。如果一个散列的关键字事先不知道，那么在关键字函数的帮助下，用户可以获得关键字列表，并可以迭代这些关键字。
**例:**

```
my @fruits = keys %rateof;
for my $fruit (@fruits) {
    print "The color of '$fruit' is $rateofof{$fruit}\n";
}
```

**散列的大小:**键/值对的数量被称为散列的大小。要获得大小，第一个用户必须创建一个键或值的数组，然后他可以获得数组的大小。

*   **语法:**

```
print scalar keys % hash_variable_name;
```

*   **例:**

## Perl 语言

```
# Perl program to find the size of a Hash

#use warnings;

# creating hash
%rateof = ('Mango' => 64, 'Apple' => 54, 'Grapes' => 44, 'Strawberry'=>23);

# creating array of keys
@keys = keys %rateof;
$size = @keys;
print "Hash size using Keys is: $size\n";

# creating hash of values
@values = values %rateof;
$size = @values;
print "Hash size using Values is: $size\n";
```

*   **输出:**

```
Hash size using Keys is: 4
Hash size using Values is: 4
```

**在哈希中添加和移除元素:**用户可以使用简单的赋值运算符轻松地将新的一对键/值添加到哈希中。

*   **示例 1:** 在哈希中添加元素

## Perl 语言

```
# Perl program to add an element in a hash

#use warnings;

# creating hash
%rateof = ('Mango' => 64, 'Apple' => 54, 'Grapes' => 44, 'Strawberry'=>23);

# array of keys
@keys = keys %rateof;

$size = @keys;
print "SIZE OF HASH BEFORE ADDING:  is $size\n";

# Adding new key/value pair into hash
$rateof{'Potato'} = 20;

# array of keys
@keys= keys %rateof;

$size = @keys;
print "SIZE OF HASH AFTER ADDING:  is $size\n";
```

*   **输出:**

```
SIZE OF HASH BEFORE ADDING:  is 4
SIZE OF HASH AFTER ADDING:  is 5
```

*   **示例 2:** 使用**删除**功能
    从哈希中删除元素

## Perl 语言

```
# Perl program to element from hash

#use warnings;

# creating hash
%rateof = ('Mango' => 64, 'Apple' => 54, 'Grapes' => 44, 'Strawberry'=>23);

# creating array of keys
@keys= keys %rateof;

# finding size of hash
$size = @keys;
print "SIZE OF HASH BEFORE DELETING: $size\n";

# using delete function
delete $rateof{'Mango'};

# creating array of keys
@keys= keys %rateof;

# finding size of hash
$size = @keys;
print "SIZE OF HASH AFTER DELETING: $size\n";
```

*   **输出:**

```
SIZE OF HASH BEFORE DELETING: 4
SIZE OF HASH AFTER DELETING: 3
```