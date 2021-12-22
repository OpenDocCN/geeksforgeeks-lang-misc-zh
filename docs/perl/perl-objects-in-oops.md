# Perl | OOPs 中的对象

> 原文:[https://www.geeksforgeeks.org/perl-objects-in-oops/](https://www.geeksforgeeks.org/perl-objects-in-oops/)

Perl 是一种基于面向对象、动态和 T2 解释器的编程语言。在面向对象编程中，我们有三个主要方面，即对象、类和方法。一个对象是一个数据类型，它可以作为它所属的类的一个**实例**被专门调用。它可以是不同数据类型的数据变量的集合，也可以是不同数据结构的集合。方法是作用于类的这些对象的函数。

下面是一个基本示例，可以更好地理解如何在 Perl 中使用对象:

**首先**，我们需要定义类。在 Perl 中，这是通过构建类的包来完成的。[包](https://www.geeksforgeeks.org/packages-in-perl/)是一个封装的实体，包含相关类的所有数据成员和方法。

```perl
package Employee;

```

这里，雇员是类名。

**第二个**任务，是创建包的一个实例(即对象)。为此，我们需要一个构造函数。一个[构造器](https://www.geeksforgeeks.org/perl-constructors-and-destructors/)是 Perl 中的一个子程序，通常被命名为**“新的”**。但是，该名称是用户定义的，因此不限于“新”。

```perl
package Employee;

# Constructor with name new
sub new 
{
    my $class = shift;
    my $self = {
                  _serialNum => shift,
                  _firstName => shift,
                  _lastName  => shift,
              };

    bless $self, $class;
    return $self;
}
```

在构造函数中，我们定义了一个简单的**散列引用** $self 来设计我们的对象。在这里，对象将有三个值 serialNum、firstName 和 lastName，这意味着与此相关的每个员工都将有自己的一组序列号、firstname 和 lastname。`**[my](https://www.geeksforgeeks.org/perl-my-keyword/)**`关键字是一个访问说明符，它将$class 和$self 本地化到封闭块中。`**[shift](https://www.geeksforgeeks.org/perl-shift-function/)**`关键字从默认数组**“@ _”**中取包名，传递给祝福功能。
**`bless`** 函数用于返回最终成为对象的引用。
最后，构造函数将最终返回 Employee 类的实例(这里)。

**最后**，主要部分是如何初始化一个对象。可以通过以下方式完成:

```perl
$object = new Employee(1, "Geeks", "forGeeks");

```

这里， **$object** 是一个标量变量，它是对构造函数中定义的散列的引用。

下面是在 OOPs 中创建和实现对象的示例程序:

```perl
use strict;
use warnings;

# class with the name Employee
package Employee;

# constructor with the name new
sub new 
{            
    # shift will take package name 
    # and assign it to variable 'class'
    my $class = shift;    

    # defining the hash reference
    my $self = {                         
                _serialNum => shift,
                _firstName => shift,
                _lastName => shift,
               };

    # Attaching object with class
    bless $self, $class;

    # returning the instance of class Employee
    return $self;                         
}

# Object creation of the class
my $object = new Employee(1, "Geeks", "forGeeks");

# object here is a hash to a reference
print("$object->{_firstName} \n");             
print("$object->{_serialNum} \n");    
```

**Output:**

```perl
Geeks 
1

```

Perl 中的对象的工作方式与 C++、Java 等其他语言相同。上面的程序展示了一个对象在 Perl 中的工作，它的创建和它在类中的使用。