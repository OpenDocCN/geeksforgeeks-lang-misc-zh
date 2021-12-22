# Perl–从数组创建散列

> 原文:[https://www . geesforgeks . org/perl-从数组创建哈希/](https://www.geeksforgeeks.org/perl-creating-a-hash-from-an-array/)

**散列**是将给定的密钥转换成另一个值的过程。一个**散列函数**用于根据数学算法生成新值(称为散列)。

一个 **[Perl 散列](https://www.geeksforgeeks.org/perl-hash/)** 是由键值对定义的。 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 以一种优化的方式存储散列的元素，这样你就可以非常快速地基于关键字查找它的值。像标量或数组变量一样，散列变量有自己的前缀。散列变量必须以**百分号(%)** 开头。哈希键必须是唯一的。如果试图用已经存在的密钥添加新的密钥-值对，现有密钥的值将被重写。

**示例:**

```
#!/usr/bin/perl

# defines a hash named subjects
# the first scalar inside the 
# brackets are hashes and the 
# second one beside them are values
my %subjects = qw(Physics Laws 
                  Chemistry Exceptions
                  Mathematics Formulas
                  Programming Fun);

# getting the value of Programming
print($subjects{'Programming'});
```

**Output:**

```
Fun
```

为了使代码更加优雅和易于阅读，Perl 提供了= >运算符。它有助于区分键和值。键总是用= >运算符指向它们相应的值。然而，这里 Perl 要求散列的键是字符串，同时，值可以是任何标量。如果使用非字符串值作为键，可能会得到意外的结果。可以使用= >运算符重写$subjects 哈希，如下所示:

```
#!/usr/bin/perl

# declaring hash using the => operator
my %subjects = ( Physics => 'Laws',
                 Chemistry => 'Exceptions',
                 Mathematics => 'Formulas',
                 Programming => 'Fun' );

# getting the value of Mathematics
print($subjects{'Mathematics'});
```

**Output:**

```
Formulas
```

#### 哈希赋值中的奇数个元素

当哈希赋值中的元素数量是奇数时，Perl 会给我们一个警告，因为它注意到分配给哈希的元素数量不能除以 2。元素的数量是奇数。

由于这只是一个警告(只有在“使用警告”有效时才会显示)，脚本将继续分配。奇数元素(“物理”、“化学”、“数学”和“编程”)将成为键，偶数元素(“定律”、“例外”和“公式”)将成为值。因为元素的数量是奇数，所以最后一个键(“编程”)不会有一对。

```
#!/usr/bin/perl
use warnings;
use strict;

# declaring hash with odd number 
# of assignments
my %subjects = qw( Physics Laws
                   Chemistry Exceptions
                   Mathematics Formulas
                   Programming );

print "Physics = $subjects{'Physics'}\n";
print "Chemistry = $subjects{'Chemistry'}\n";
print "Mathematics = $subjects{'Mathematics'}\n";
print "Programming = $subjects{'Programming'}\n";
```

**输出**

```
Physics = Laws
Chemistry = Exceptions
Mathematics = Formulas
Programming = 

Odd number of elements in hash assignment at line 7.
Use of uninitialized value $subjects{"Programming"} in print at line 12.
```

#### 添加、移除和修改哈希的元素

向哈希中添加新元素并修改它们，彼此非常相似。哈希的名称后面是花括号内的键，并被赋予一个值。我们可以使用 delete 函数删除一个散列。以下示例代码显示了如何从哈希中分配/修改和移除元素:

```
#!/usr/bin/perl

# declaring a hash
my %subjects = ( Physics => 'Laws',
                 Chemistry => 'Exceptions',
                 Mathematics => 'Formulas',
                 Programming => 'Fun' );

# extracting keys of hash in an array
@keys = keys %subjects;

# determining size of keys-array i.e.
# number of elements in hash
$size = @keys;
print "Hash size is $size\n";

# adding an element to the hash;
$subjects{'Biology'} = 'Boring';

# determining size of hash after
# adding an element
@keys = keys %subjects;
$size = @keys;

print "Hash size is $size\n";

# removing an element from hash
delete $subjects{'Chemistry'};

# determining size of hash after
# removing an element
@keys = keys %subjects;
$size = @keys;

print "Hash size is $size\n";

# modifying an element of hash
$subjects{'Mathematics'} = 'Intriguing';

# looping over the hash
for(keys %subjects){
    print("$_ is $subjects{$_}\n");
}
```

**Output:**

```
Hash size is 4
Hash size is 5
Hash size is 4
Mathematics is Intriguing
Physics is Laws
Programming is Fun
Biology is Boring

```