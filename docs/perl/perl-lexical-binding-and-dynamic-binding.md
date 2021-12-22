# Perl |词法绑定和动态绑定

> 原文:[https://www . geesforgeks . org/perl-词法绑定和动态绑定/](https://www.geeksforgeeks.org/perl-lexical-binding-and-dynamic-binding/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的词法绑定和动态绑定是一个定义变量的值和范围的系统，它使变量很容易通过其各自的名称找到。Perl5 支持词法绑定和动态绑定

<font size="3">**词汇绑定:**</font> 又称**静态绑定**。绑定范围类似于语法、函数等，它们构成了全新的表值，变量的名称按照排名顺序进行分类，这被称为环境。这种绑定在 **Emacs** 中引入。这为最大化利用创造了许多机会，因此使用它的程序在未来版本的 Emacs 中具有运行更快的优势。它们与后来添加到 Emacs 26.1 版本中的并发性更加协调。词法范围意味着对在词汇上绑定的变量的引用应该位于绑定的构造中。

**词法绑定的工作方式:**词法环境最好由绑定构造来定义，这指定了构造中有界变量的局部值。词法环境是 Lisp 评估器查看变量具体值的第一个地方。词汇绑定的范围是不确定的。这意味着即使在词法环境的执行结束后，它也不会被丢弃，并且每当它被调用时都可以再次使用。
T3】例:

```
#!/usr/bin/perl

# Perl program to demonstrate 
# lexical binding

{
    # begin lexical scope
    my $var = "GeeksforGeeks";
    print "\$var is: ", (defined $var ? 
                                 $var : "Geeks"), $/;

} # end lexical scope

# Executing outside lexical scope
print "\$var is: ", (defined $var ? 
                             $var : "Geeks"), $/;
```

**Output:**

```
$var is: GeeksforGeeks
$var is: Geeks

```

在上面的示例代码中，变量 **$var** 的范围是为特定的代码体定义的，并且在外部调用时会发生变化。这表明一旦词法范围已经退出，那么在这个词法范围中创建的任何内容都将被删除。

<font size="3">**动态绑定:**</font> 这也被称为**后期绑定**词汇或静态绑定的替代选项。这个绑定是一个系统，通过这个系统，程序等待运行时完成，然后通过被称为实际子例程的名称来绑定方法。这种绑定成本更高，但同时，它也有自己的好处，比如避免版本之间的冲突。Java 和 C++是可以执行动态绑定的常见语言。动态绑定中常用的概念是[方法覆盖](https://www.geeksforgeeks.org/perl-method-overriding-in-oops/)。
**为什么要使用动态绑定？**

*   更容易实现。在词汇绑定之前，整个概念是通过大众的方式来理解的。
*   这对其他人来说更明智，也更容易理解。

**示例:**

```
#!/usr/bin/perl

# Perl program to demonstrate 
# Dynamic binding
package Animal;

sub new 
{
    my $class = shift;

    # Bless into the correct class
    bless {}, $class; 
}

sub method1 
{
    my $this = shift;
    print("This is Animal class Method 1");
}

sub method2 
{
    my $this = shift;
    print("\nThis is Animal class Method 2");
}

package cat;

our @ISA = (Animal); # cat is a subclass of Animal

sub method2
{
    my $this = shift;
    print("\nThis is cat class Method 1");
}

package main;

# Calls Animal::new but creates a 'cat' object
my $cat = new cat; 

# Calls Animal::new but creates a 'dog' object
my $dog = new Animal; 

$dog->method1(); # Calls Animal::method1
$cat->method2(); # Calls cat::method2
```

**Output:**

```
This is Animal class Method 1
This is cat class Method 1

```

在上面的示例代码中，Perl 使用[方法覆盖](https://www.geeksforgeeks.org/perl-method-overriding-in-oops/)的概念来执行动态绑定的操作。它展示了动态绑定如何允许访问类范围之外的内容。