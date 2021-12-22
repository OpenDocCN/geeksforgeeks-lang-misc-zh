# Perl |可变和不可变参数

> 原文:[https://www . geesforgeks . org/perl-可变和不可变参数/](https://www.geeksforgeeks.org/perl-mutable-and-immutable-parameters/)

一个 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 函数或子例程是一组共同执行特定任务的语句。在每种编程语言中，用户都希望重用代码。因此，用户将这段代码放在函数或子例程中，这样就不需要反复编写代码。这些子程序包含定义参数类型和数量的参数，这些参数可以在函数调用时传递给函数。这些参数或参数用于根据函数中指定的表达式计算传递给函数的值。然后，这些值被返回给指定的参数，并被传递给调用函数。

**示例:**

```perl
sub Function1(parameter1, parameter2){ statement; }
```

### 可变参数:

这些类型的参数是那些其值可以在函数中修改的参数，这些参数作为参数传递给函数。这意味着当使用**调用者函数**将参数传递给函数时，其值将绑定到**调用函数**中的参数，这意味着对该函数中的值所做的任何更改也将反映在调用者函数的参数中。

### 不可变参数:

这些参数属于那些不能在作为参数传递给它们的函数中修改其值的类型。这意味着当使用**调用函数**将参数传递给函数时，子程序接收的是一个值而不是一个变量。因此，对函数参数所做的任何更改都不会反映出来。

默认情况下，Perl 中的*子例程*参数是不可变的，这意味着它们不能在函数内更改，也不能意外修改调用者函数的参数。
在某些语言中，这个过程被称为**“按值调用”**，这意味着被调用的子例程接收一个值而不是变量，因此调用者函数的参数不会被修改。

**示例:**

```perl
#!/usr/bin/perl

# Function Definition
sub Func(Int $variable)
{
    # Operation to be performed
    $variable /= 2; 
}

# Defining a local variable
my $value = 20;

# Function Call with local variable
print Func($value);
```

**输出:**

> **错误:**不能赋值给不可变的值

要更改这些参数的属性，可使用*特性。在特性的帮助下，参数的值可以在子程序中改变。*

### *特点:*

*这些是预定义的内置子例程，当在方法中使用时，它们在编译时运行时修改方法的行为。特征甚至可以用来改变方法的主体，或者简单地用元数据标记方法。
性状可以有多种类型，取决于它们的用途，例如:*

*   *`**is cached**` trait 根据传递给它的参数自动缓存函数的返回值。*
*   *`**is rw**`特性允许子程序参数的可写访问器。*
*   *`**is copy**` trait 允许在子例程中更改参数值，但不更改调用者函数中的参数。*

***例:**使用 **`is copy`** 性状*

```perl
*#!/usr/bin/perl

# Function Definition using
# 'is copy' trait
sub Func(Int $variable is copy)
{
    # Operation to be performed
    $variable += 5; 
}

# Defining a local variable
my $value = 10;

# Function Call with local variable
print Func($value), "\n";

# Checking if 
# $value gets updated or not
print $value;*
```

***输出:***

```perl
*15
10*
```

*在上面的代码中， **`is copy`** trait 被使用是因为默认情况下，Perl 不允许修改子例程内的参数。这个特性允许程序将调用者函数的参数值分配给被调用的子程序的参数。但是，这种特性只会改变被调用函数中参数的值。*

***例:**使用 **`is rw`** 性状*

```perl
*#!/usr/bin/perl

# Function Definition using
# 'is rw' trait
sub Func(Int $variable is rw)
{
    # Operation to be performed
    $variable += 5; 
}

# Defining a local variable
my $value = 10;

# Function Call with local variable
print Func($value), "\n";

# Checking if 
# $value gets updated or not
print $value;*
```

***输出:***

```perl
*15
15*
```

*在上面的代码中，当使用`**is rw**`而不是`**is copy**` trait 时，调用者函数中传递的参数的值也会得到更新。*

*当使用`**is rw**`特性时，被调用函数的参数与调用者函数的参数绑定在一起，所以如果前者的值有任何变化，后者会立即更新。这是因为这个过程被称为**“引用调用”**。因为，两个参数都指向同一个内存位置(因为`**is rw**`特性)。这使得参数完全可变。*