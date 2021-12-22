# Perl–面向对象编程中的属性

> 原文:[https://www . geesforgeks . org/perl-面向对象编程中的属性/](https://www.geeksforgeeks.org/perl-attributes-in-object-oriented-programming/)

在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中，面向对象的概念非常基于引用和*数组/散列*。相对于 Perl 编程，面向对象编程的几个主要术语是对象、类和方法。

*   In Perl, the *object* is like a reference to a data type that knows which class it belongs to. Object is stored as a reference in a scalar variable. Because scalar only contains references to objects, it can even hold different objects in different classes.
*   In Perl, the package containing the corresponding methods needed to create and manipulate objects is called *class* .
*   In Perl, *method* is a subroutine defined in the package. The package name or object reference is the first parameter of the method, depending on whether the method affects the current class or object.

#### 属性

每个类都可以定义属性。当我们将它们表示为对象时，我们为这些属性赋值。例如，甚至每个“文件”对象都有一个路径。属性也称为属性。

属性通常定义为只读或读写。只读属性只能在创建对象时设置，而读写属性可以随时更改。一个属性值本身可以是另一个对象。并不是每个类都必须有属性和方法。

Perl 没有特殊的属性语法。在后面，属性通常作为键存储在对象的底层散列中。

## Perl

```
sub new{
    my ($class, $args) = @_;
    my $self = bless { serial => $args->{serial},
                       name => $args->{name},
                       price => $args->{price}
                     }, $class;
}
```