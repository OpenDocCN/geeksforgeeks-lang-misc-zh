# Perl |哈希运算

> 原文:[https://www.geeksforgeeks.org/perl-hash-operations/](https://www.geeksforgeeks.org/perl-hash-operations/)

**Prerequisite:**

[Perl Hashes](https://www.geeksforgeeks.org/Perl-Hashes/)

[Perl Hash](https://www.geeksforgeeks.org/perl-hash/)

大多数读者可能都知道，**哈希**通过一种叫做**哈希**的机制来存储数据。在散列法中，密钥用于确定一个值或数据。这些密钥必须是**唯一的**，然后用作存储与密钥相关的数据的索引。该数据不必是唯一的。它可能是重复的。

Hash 是通过维护键和值或**键/值对**之间的关系来存储数据的数据结构。给定一把钥匙，我们就能找到它的价值。键/值对是可变的对象，因此可以随时更改。哈希中的键可以进一步定义为用于检索值的对象。与数组相比，使用哈希的主要优势在于，哈希允许基本操作的执行时间保持不变，例如，在特定键上获取值或设置值(在数组的情况下是索引)，即使对于大型数据集也是如此。

请注意，Perl 中的散列是**而不是有序的**。这意味着当您迭代散列时，您可能无法按照插入值的相同顺序提取这些值。

存储在散列罐中的值可以是**类型的整数、浮点、字符串、布尔、数组和散列**本身。

**例**

```
#!/usr/bin/perl

# Creating a simple hash containing
# different types of values
my %hash = ( # value type string
            'MyVehicle' => 'Car',

            # value type integer
            'Model' => 1234,

            # value type float
            'Speed' => 60.7,    

            # value type hash
            'Traffic' => {'Red' => 'Stop',         
                        'Yellow' => 'Look and move', 
                        'Green' => 'Go'},
            # value type array
            'AllVehicles' => ['Car', 'Cycle', 
                              'Bus', 'Auto']);

# printing values stored 
# at key 'Traffic' and 'AllVehicles'
print "Traffic : $hash{'Traffic'}\n";
print "AllVehicles : $hash{'AllVehicles'}\n";
```

**Output:**

```
Traffic : HASH(0x242af30)
AllVehicles : ARRAY(0x24471f8)

```

这里，关键流量的数据类型是哈希，关键所有车辆的数据类型是数组。因此，输出分别是散列和数组的第一个元素的地址。

此外，可以对散列执行许多操作或操纵，如下所述:

**散列运算**

Perl 哈希操作包括各种操作，这些操作通过哈希来更有效地存储和检索数据。哈希中最常用的操作是:

1.  访问散列中的键和值。
2.  修改特定键的值。
3.  循环到哈希。

Perl Hash 中的每个操作都将在下面用例子进行解释:

**查找/访问 Perl 哈希值或密钥**

查找或访问意味着能够访问散列的每一个键/值对，以便进一步操作。Perl 中的键以一种最佳方式存储哈希的元素，这样就可以非常快地获取其值。散列中的值可以使用嵌入在 **{}** 括号之间的相应键名来查找。

> **语法:**$ hash _ name { key _ name }；

**例**

```
# Perl program to demonstrate 
# accessing of the hash values
my %hash = ('MyVehicle' => 'Car', 
            'Model' => 1234, 
            'Speed' => 60.7, 

            # value type hash
            'Traffic' => {'Red' => 'Stop',             
                          'Yellow' => 'Look and move', 
                          'Green' => 'Go'},

            # value type array
            'AllVehicles' => ['Car', 'Cycle', 
                              'Bus', 'Auto']);

# Creating array containing 
# keys of the hash
@k = keys %hash;         

# print all keys of the hash
print "Keys are : ";
print join(", ", @k), "\n";

# Creating array containing
# values of the hash
@v = values %hash;             

# print value of all values
print "Values are : ";
print join(", ", @v), "\n";

# accessing individual values of the keys
print "Speed is : $hash{'Speed'}\n";
print "Yellow light indicates : $hash{'Traffic'}{'Yellow'}\n";
print "$hash{'AllVehicles'}[3] is a type of vehicle \n";
```

**Output:**

```
Keys are : AllVehicles, MyVehicle, Speed, Traffic, Model
Values are : ARRAY(0x9361f8), Car, 60.7, HASH(0x919f30), 1234
Speed is : 60.7
Yellow light indicates : Look and move
Auto is a type of vehicle 

```

**修改哈希元素**

散列中的值不是固定的，也就是说，它们容易改变，Perl 提供了这种修改和更新散列中的值的能力。对于给定的键，要修改或更新其相应的值，请使用以下语法:

> **语法:**$ hash { ' Key ' } = modified _ value；

要修改给定的键而不改变其相应的值，只需创建一个额外的键，即修改后的键，并为该键分配值(为此您需要这个新键)，然后使用 **delete** 关键字删除以前的键/值对。

**示例:**

```
# Perl program to demonstrate the 
# Modification of an element of a Hash 

# creating a hash
my %hash = ('MyVehicle' => 'Car', 
            'Model' => 1234, 
            'Speed' => 60.7, 

            # value type hash
            'Traffic' => {'Red' => 'Stop',             
                          'Yellow' => 'Look and move', 
                          'Green' => 'Go'},

            # value type array
            'AllVehicles' => ['Car', 'Cycle', 
                              'Bus', 'Auto']);

# previous value of key 'Model'
print ("Previous Model number is ", 
             $hash{'Model'}, "\n");

# modifying value of key 'Model'
$hash{'Model'} = 7717;

# new value of key 'Model'
print ("New Model number is ", 
        $hash{'Model'}, "\n");

# Changing key from 'MyVehicle' to 'Mine' 
# without changing its corresponding value
@k = keys %hash;

# printing previous keys
print "Previous Keys are : \n";     
print join(", ", @k), "\n"; 

$hash{'Mine'} = 'Car';

# deleting 'MyVehicle' key/value pair
delete $hash{'MyVehicle'};         

@k_n = keys %hash;
print "New Keys are : \n";    

# printing new keys
print join(", ", @k_n), "\n"; 
```

**Output:**

```
Previous Model number is 1234
New Model number is 7717
Previous Keys are : 
MyVehicle, AllVehicles, Model, Traffic, Speed
New Keys are : 
Mine, Speed, Traffic, Model, AllVehicles

```

**遍历 Perl 哈希值**

Perl 允许循环其哈希值。这意味着哈希是迭代类型，可以使用“for”循环和“while”循环迭代其键和值。在 Perl 中，哈希数据结构由 key()函数提供，类似于 Python 编程语言中的函数。这个 keys()函数允许你在标量中获得一个散列的键列表，这个列表可以进一步用于迭代散列的各个键的值。

> **语法**键%哈希

此外，Perl 提供了两种方法来循环散列中的所有元素。

1.  Perl **foreach** 循环
2.  Perl **而**循环使用**的每个**功能

```
# Perl program to demonstrate the 
# looping over a hash using its keys

# creating a hash
my %hash = ('MyVehicle' => 'Car', 
            'Model' => 1234, 
            'Speed' => 60.7, 

            # value type hash
            'Traffic' => {'Red' => 'Stop',             
                          'Yellow' => 'Look and move', 
                          'Green' => 'Go'},

            # value type array
            'AllVehicles' => ['Car', 'Cycle',
                              'Bus', 'Auto']);

# Case 1: When hash is not large 

# for loop to loop over the hash
foreach my $key (keys %hash)
{

    # do stuff
    $value = $hash{$key};
    print "Value of $key is $value\n"; 
}

# Case 2: When hash is very large 

# traversing the hash using "each" function
while(($key, $value) = each (%hash))
{

    # do stuff
    $value = $hash{$key};
    print "Value of $key is $value\n"; 
}
```

**Output:**

```
Value of Model is 1234
Value of MyVehicle is Car
Value of Traffic is HASH(0x1049f30)
Value of AllVehicles is ARRAY(0x10661f8)
Value of Speed is 60.7
Value of Model is 1234
Value of MyVehicle is Car
Value of Traffic is HASH(0x1049f30)
Value of AllVehicles is ARRAY(0x10661f8)
Value of Speed is 60.7

```

在上面的例子中，代码给出了数组第一个元素的地址和分别存储在关键字“所有车辆”和“交通”中的散列。为了克服这一点，我们必须在数组内部循环并散列。

**例**

```
# Perl program to demonstrate the 
# looping over a multidimensional hash

# creating a hash
my %hash = ('MyVehicle' => 'Car', 
            'Model' => 1234, 
            'Speed' => 60.7, 

            # value type hash
            'Traffic' => {'Red' => 'Stop',             
                          'Yellow' => 'Look and move', 
                          'Green' => 'Go'},

            # value type array
            'AllVehicles' => ['Car', 'Cycle',
                              'Bus', 'Auto']);

# Loop over the key storing array 
my @array = @{$hash{'AllVehicles'}};
print "AllVehicles include \n";

# for loop to loop over the array
foreach my $ele (@array)
{
    print "$ele\n";
}

# Loop over the key storing hash
print "\nTraffic includes\n";

# for loop to loop over the hash
foreach my $val(keys %{$hash{'Traffic'}})
{
    print "Key : $val, value : $hash{'Traffic'}{$val}\n";
}
```

**Output:**

```
AllVehicles include 
Car
Cycle
Bus
Auto

Traffic includes
Key : Yellow, value : Look and move
Key : Green, value : Go
Key : Red, value : Stop

```