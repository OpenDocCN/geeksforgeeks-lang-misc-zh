# Perl 编程中的通用包

> 原文:[https://www . geesforgeks . org/universal-package-in-perl-programming/](https://www.geeksforgeeks.org/universal-package-in-perl-programming/)

**UNIVERSAL** 是 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 5 中的内置包。它也可以被认为是一个基类，派生类可以在其中隐式继承或重写。它提供了几种默认方法，如`isa()`、`can()`、`VERSION()`和`DOES()`。通用类不能显示在包的 **@ISA** 变量中。其他方法也可以通过 Perl 或 XS 代码添加到 UNIVERSAL 类中。在程序中使用上述方法，不需要在代码中包含“**使用 UNIVERSAL** ”语句。

#### 版本()方法

它返回合适的类或包的$VERSION 变量的值。此方法可以将版本号作为可选参数。如果查询的$VERSION 不大于或等于参数，此方法将引发异常。

**示例:**
我们来考虑一下 2.0 版本的模块 Dog

```
use 5.010;
package Dog 2.0;
use strict;
use warnings;

# constructor
sub new
{
    # the package name 'Dog' is in the default array @_
    # shift will take package name 'Dog' 
    # and assign it to variable 'class'
    my $class = shift;

    # object
    my $self = {
        'name' => shift,
        'breed' => shift
    };

    # blessing self to be object in class
    bless $self, $class;

    # returning object from constructor
    return $self;
}

my $d = new Dog('Sammy','Pug');

say Dog->VERSION();
say $d->VERSION();
say $d->VERSION(0.0);
say $d->VERSION(1.5);
say $d->VERSION(3.0);    # EXCEPTION
```

**输出:**

```
2.0
2.0
2.0
2.0
Dog version 3 required--this is only version 2.0 at /home/4c09f6973dc56e8a558b8be499a040bb.pl line 32.

```

#### dos()方法

`DOES()`方法检查类或对象是否执行特定的角色。当角色的名称传递给此方法时，如果它执行指定的角色，则返回 true(1)，否则返回 false(0)。角色可以被认为是一个类所表现的行为的集合。

**示例:**
让我们考虑模块/类狗和动物

```
use 5.010;
package Animal;  

sub new
{
    my $type = shift;           
    my $self = {};               
    return bless $self, $type;    
}

sub MyMethod 
{
   print "Animal::MyMethod called!\n";
}

# class Dog    
package Dog;   

# class Dog inherits from class Animal
@ISA = qw(Animal);    

sub new
{
    my $type = shift;            
    my $self = Animal->new;     
    return bless $self, $type;  
}
sub MyMethod
{
    my $self = shift;

    $self->SUPER::MyMethod();
}

# Driver Code
package main;      
$myObject = Animal->new();
$myObject2 = Dog->new();

# Basic DOES() usage
say Dog->DOES('Animal');
say $myObject->DOES('Animal');
say $myObject2->DOES('Dog');
```

**输出:**

```
1
1
1

```

#### can()方法

`can()`方法接受方法名为字符串。它返回对实现此方法的现有函数的引用，否则它将返回一个 false 值。此方法可以在类、对象或包上调用。如果 can($classname)返回 true，则表示存在名为$classname 的类。这个方法只检查一个类的存在，不评论它的可用性。

**例:**
我们来考虑一个类 Dog，它有一个叫 bark 的方法，这个方法可以参考如下:

```
use 5.010;
use strict;
use warnings;

{ 
    package Animal; 
    sub new 
    { 
        bless({}, 
        $_[0]) 

    }
}

{ 
    package Dog; 
    our @ISA = qw(Animal); 
    sub dog { 1 } 
}

# objects
my $dog = Dog->new;
my $animal = Animal->new;

# Basic can() usage
say $animal->can('dog');  # false
say $dog->can('dog');  # true
```

**输出:**

```
Use of uninitialized value in say at /home/fdfdd52de0b7348de191b3d9be3cb44f.pl line 11.
CODE(0x1fc3168)

```

`can()`也可以用来检查一个包是否成功实现了特定的功能或方法。

#### isa()方法

`isa()`方法接受类的名称或内置类型的名称作为字符串。它可以在类方法、实例方法或对象上调用。如果指定的类或对象是从包派生的，或者是对给定类型的受保护引用，则返回 true。

**示例:**
假设$doggy 是一个对象(一个散列引用，被祝福到 Dog 类中，从 Animal 类继承而来):

```
use 5.010;
use strict;
use warnings;

{ 
    package Animal; 
    sub new
    { 
        bless({},
        $_[0]) 
    } 
}

{ 
    package Dog; 
    our @ISA = qw(Animal); 
    sub dog { 1 } 
}

# objects
my $animal = Animal->new;
my $dog = Dog->new;

# basic isa() usage 
say $animal->isa('Animal');  # true
say $dog->isa('Animal');  # true
```

**输出:**

```
1
1

```