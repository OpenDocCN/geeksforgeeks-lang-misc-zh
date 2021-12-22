# Perl | OOPs 中的方法

> 原文:[https://www.geeksforgeeks.org/perl-methods-in-oops/](https://www.geeksforgeeks.org/perl-methods-in-oops/)

方法用于访问和修改对象的数据。这些是使用类或包本身的对象调用的实体。方法基本上是 Perl 中的一个子程序，没有一个方法的特殊身份。方法的语法与子程序的语法相同。就像子程序一样，方法是用 **`sub`** 关键字声明的。

方法将调用它的对象或包作为它的第一个参数。OOPs 使用这些方法来操作对象的数据，而不是直接与对象交互，这样做是为了维护数据的安全性，防止程序员直接更改对象的数据。这可以通过使用各种助手方法来实现，这些方法将对象作为参数，并将其值存储到另一个变量中。此外，对第二变量进行修改。这些修改不会影响对象的数据，因此使其更加安全。

## Perl 中的方法类型:

根据传递的参数，方法可以分为两种类型- `**static**`方法和`**virtual**`方法。

一个 **`static`** 方法是传递给该方法的第一个参数是类名。静态方法的功能适用于整个类，因为它以类名作为参数。这些方法也被称为**类方法**。由于大多数方法都在同一个类中，因此没有必要将类名作为参数传递。
**示例:**一个类的构造函数被认为是静态方法。

`**virtual**`方法是将对对象的引用作为第一个参数传递给函数的方法。在虚函数中，第一个参数被转移到局部变量，然后这个值被用作引用。

**示例:**

```perl
sub Student_data
{ 
    my $self = shift; 

    # Calculating the result 
    my $result = $self->{'Marks_obtained'} / 
                 $self->{'Total_marks'}; 

    print "Marks scored by the student are: $result"; 
} 
```

面向对象编程中的方法需要括号来保存参数，而这些方法是通过使用箭头操作符( **- >** )来调用的。

**`get-set`方法:**
方法用于为对象的数据提供安全性，因此要么与对象的引用一起使用，要么将值存储在其他变量中，然后使用。 **`get-set`** 方法用于 OOPs 中，为对象提供这种数据安全性。 **`get-method`** 有助于获取对象的当前值，而 **`set value`** 方法用于为对象设置新值。

**示例:**

```perl
# Declaration and definition of Base class 
use strict; 
use warnings; 

# Creating parent class 
package vehicle; 

# Setter method
sub set_mileage
{ 

    # shift will take package name 'vehicle'  
    # and assign it to variable 'class' 
    my $class = shift; 

    my $self = { 
                'distance'=> shift, 
                'petrol_consumed'=> shift
               }; 

    # Bless function to bind object to class 
    bless $self, $class; 

    # returning object from constructor 
    return $self; 
} 

# Getter method
sub get_mileage 
{ 
    my $self = shift; 

    # Calculating result 
    my $result = $self->{'distance'} / 
                 $self->{'petrol_consumed'}; 

    print "The mileage by your vehicle is: $result\n"; 

} 

# Object creation and method calling
my $ob1 = vehicle -> set_mileage(2550, 170); 
$ob1->get_mileage(); 
```

**输出:**
![](img/3d945d5b49e67ba0b4bf83609801c4ff.png)