# Perl | OOPs 中的封装

> 原文:[https://www.geeksforgeeks.org/perl-encapsulation-in-oops/](https://www.geeksforgeeks.org/perl-encapsulation-in-oops/)

**封装 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的**是封装数据的过程，以保护数据免受不需要访问这部分代码的外部来源的影响。封装是[面向对象编程](https://www.geeksforgeeks.org/object-oriented-programming-oops-in-perl/)的一部分，它用于绑定数据和用于操作该数据的子程序。
另一方面，封装是一个保护屏障，防止数据被这个屏障之外的代码访问。

*   从技术上讲，在封装中，一个类的变量或数据对任何其他类都是隐藏的，只能通过声明它们的自己类的任何成员函数来访问。
*   与封装一样，一个类中的数据对其他类是隐藏的，因此也被称为**数据隐藏**。
*   **封装可以通过:**将类中的所有变量声明为局部变量，并通过导入包来获取类的方法来设置和获取变量的值。

![](img/0ed36914350b3bbc86ee3244011a599f.png)

考虑一个真实的封装示例，在一个公司中，有不同的部分，如帐户部分、财务部分、销售部分等。财务科处理所有财务交易，并记录所有与财务有关的数据。同样，销售部门处理所有与销售相关的活动，并保存所有销售记录。现在可能会出现这样一种情况:出于某种原因，财务部的一名官员需要某个特定月份的所有销售数据。在这种情况下，不允许他直接访问销售部门的数据。他首先必须联系销售部门的其他官员，然后要求他提供具体数据。这就是封装。这里，销售部门的数据和能够操纵这些数据的员工被包装在一个名称“销售部门”下。

**示例:**

```perl
# Declaration and definition of Base class 
use strict; 
use warnings; 

package Student;
sub new 
{ 

    # shift will take package name 'Student'  
    # and assign it to variable 'class' 
    my $class = shift; 

    my $self = { 
                'name'=> shift, 
                'age'=> shift,
                'roll_no' => shift
               }; 

    # Bless function to bind object to class 
    bless $self, $class; 

    # returning object from constructor 
    return $self; 
} 

# Method for displaying the details
sub get_details 
{ 
    my $self = shift; 

    print "Name is: $self->{'name'}\n"; 
    print "Age is: $self->{'age'}\n"; 
    print "Roll_no is: $self->{'roll_no'}"; 
} 

# Object creation and calling
my $obj1 = Student->new("Rahul", 25, 12);
$obj1->get_details();
```

**Output:**

```perl
Name is: Rahul
Age is: 25
Roll_no is: 12

```

在上面的代码中，如果需要访问类的数据进行任何修改或者只是打印类的数据，那么就不能直接完成。需要创建该类的对象，然后使用 get_details()方法访问数据。这个过程被称为**数据封装**。

**封装优势:**

*   **数据隐藏:**用户将不知道类的内部实现。用户看不到该类如何在变量中存储值。他只知道我们正在将值传递给访问器，并且变量正在被初始化为该值。
*   **增加灵活性:**我们可以根据自己的需求，将类的变量设为只读或只写。如果我们希望将变量设为只读，那么我们只需要在代码中使用 Get Accessor。如果我们希望将变量设置为只写，那么我们只能使用 Set Accessor。
*   **可重用性:**封装还提高了可重用性，容易随着新的需求而改变。
*   **测试代码很容易:**封装的代码对于单元测试来说很容易测试。