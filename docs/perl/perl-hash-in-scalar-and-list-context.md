# 标量和列表上下文中的 Perl | Hash

> 原文:[https://www . geesforgeks . org/perl-标量和列表中的哈希上下文/](https://www.geeksforgeeks.org/perl-hash-in-scalar-and-list-context/)

**Prerequisite:**

[Perl Hash](https://www.geeksforgeeks.org/perl-hash-operations/)

Perl 中的 **Hash** 是一组键/值对。Perl 为我们提供了将散列分配给一个类型和一个类型的灵活性，这两种类型分别称为列表上下文和标量上下文。

**列表上下文中的哈希**

在 Perl 中将散列分配给列表类型是通过创建一个以键和值为元素的列表来实现的。当散列在 LIST 上下文中时，Perl 将散列转换成交替值的列表。原始散列中的每个键值对将成为新创建的列表中的两个值。

> **语法:**
> 我的@ list = % hash

关于这个结果列表的一个有趣的事实是，对于每一对**，密钥将首先出现，值将在**之后出现。

**示例**

```
# !/usr/bin/perl
# Perl program to demonstrate
# List Context of hash

use strict; 
use warnings;
use 5.010;
use Data::Dumper qw(Dumper);

# Creating a Hash
my %hash = ('MyVehicle' => 'Car', 
        'Model' => 1234, 
        'Speed' => 60.7,     
        'Red' => 'Stop',         
        'Yellow' => 'Look and move', 
        'Green' => 'Go'
       ); 

# Assign hash to a list context
my @list = %hash;

# Print the List
say Dumper \@list;
```

**Output:**

```
$VAR1 = [
          'Yellow',
          'Look and move',
          'Green',
          'Go',
          'Speed',
          '60.7',
          'MyVehicle',
          'Car',
          'Red',
          'Stop',
          'Model',
          1234
        ];

```

在这里，我们可以看到散列的每个值都放在列表中它对应的键之后。但是没有定义这些对在列表中的放置顺序。

**Data::Dumper** 用于序列化哈希和列表。本模块提供了将数据结构(包括对象)解析为字符串格式的方法，该格式既可用于“转储”数据进行打印，也可用于进行评估，以便转储的结构可以通过**评估**重建为有效的内部结构。

主要功能**转储程序**接受数据结构或对象的标量引用列表。返回值是结构的字符串表示形式，以正常的字符串语法格式生成。

**例**

```
# !/usr/bin/perl
# Perl program to demonstrate
# Use of Data::Dumper

use Data::Dumper;

my $ref = { 'MyVehicle' => 'Car', 
        'Model' => 1234, 
        'Speed' => 60.7,     
        'Red' => 'Stop',         
        'Yellow' => 'Look and move', 
        'Green' => 'Go'
      }; 

print Dumper($ref);
```

**Output:**

```
$VAR1 = {
          'Yellow' => 'Look and move',
          'Red' => 'Stop',
          'MyVehicle' => 'Car',
          'Green' => 'Go',
          'Speed' => '60.7',
          'Model' => 1234
        };

```

**哈希中列表上下文的使用:**

*   In the List context in Perl, the operator can be used to obtain multiple values between the supplied range.
    **Example:**

    ```
    @hundred = (0..100);

    ```

    上面的例子如果放入一个 print 语句将导致打印一个从 0 到 100 的数字范围。

    *   通过使用列表上下文，可以很容易地按关键字或值对散列进行排序。将哈希转换为其键或值的列表后，对该列表进行排序，然后按排序顺序存储相应的键或值。*   我们也可以使用哈希的列表上下文，当哈希非空时，即哈希的大小不是 0 时，我们才希望执行一段代码。
    **语法**

    > @ keys = keys % hash
    > if(@ keys)
    > {
    > …。代码…
    > }

**标量上下文中的哈希**

在 Perl 中将一个散列分配给一个标量类型实际上会给出一些表示散列内部布局的内部数字。返回类型是描述哈希当前存储统计信息的字符串。这是
报告为**“已用/总计”**桶。桶是存储哈希信息的容器。

获得的字符串看起来像一个分数，可以计算为:

```
The denominator of the fraction is the total number of buckets.
The numerator of the fraction is the number of buckets which has one or more elements.
```

> **语法:**
> 我的$ list = % hash

**示例**

```
# !/usr/bin/perl
# Perl program to demonstrate
# Scalar Context of hash

# Creating a Hash
my %hash = (
        'MyVehicle' => 'Car', 
        'Model' => 1234, 
        'Speed' => 60.7,     
        'Red' => 'Stop',         
        'Yellow' => 'Look and move', 
        'Green' => 'Go'
        ); 

# Assign hash to a Scalar Context
my $list = %hash;

# Print the List
print $list;
```

**Output:**

```
5/8

```

在上面的输出中，哈希中总共有 6 个桶(所有键/值对)，因此分配的总桶数
将是 2 的最低次幂**>总键数**，用于所有桶的完全容纳，因此分母为 8。
而分子完全取决于内部算法，因为它根据散列存储属性不断改变其值。
然而，一旦散列分配了它的桶，即使我们收缩散列，它们也将保持被分配。

**注意:**对于元素个数相同的哈希，个数越高越好。返回 6/8 的冲突比返回 4/8 的冲突少。

**散列中标量上下文的使用:**

*   The Scalar context of a hash helps to determine whether the hash is empty or not. It returns 0 if the hash
    is empty.

    > 我的$ list = % hash
    > if ($list)
    > {
    > …。代码…
    > }

    如果哈希非空，将执行 **if** 条件。

    *   It helps in finding out whether Perl’s internal hashing algorithm is performing poorly on our data set.

    **例如**、
    我们将 10 个东西放在一个 hash 中，但是在标量上下文中评估%HASH 会显示“1/16”，这意味着十六个桶中只有一个被触及，并且大概包含了你所有的 10 个项目。这是不应该发生的。

    *   Also we can get the size – that is, the number of elements from a hash by using the scalar context on
    either keys or values.

    **语法**

    > @ keys = keys % hash
    > $ size = @ keys；

    这里， **$size** 将返回散列的大小。