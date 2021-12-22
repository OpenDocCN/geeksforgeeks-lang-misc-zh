# Perl |子例程的范围

> 原文:[https://www.geeksforgeeks.org/perl-scope-of-a-subroutine/](https://www.geeksforgeeks.org/perl-scope-of-a-subroutine/)

**[](https://www.geeksforgeeks.org/perl-subroutines-or-functions/)[Perl](https://www.geeksforgeeks.org/introduction-to-perl/)中的** 子程序是**可重用的**代码单元。这是一个动态的概念。函数和子程序是可以互换使用的两个术语。如果你想严格遵守语义，接受参数和返回值的小块命名代码叫做子程序。Perl 中的内置子程序通常被称为 Perl 的函数，因为它们提供了额外的功能。作为类定义的一部分创建的子程序称为**方法**。
几乎可以从任何地方调用子程序，并在子程序完成执行时将控制返回到调用点。它们可以用**零个或多个参数**调用，并可能返回**零个或多个结果**。

像变量一样，子程序既可以直接声明(不定义它们所做的工作)，也可以声明和定义。为了简单地声明一个子程序，我们使用以下形式之一:

> **语法:**
> 子名称
> 子名称原型
> 子名称属性
> 子名称原型属性

其中 **SUB_NAME** 是正在创建的子例程的名称， **PROTOTYPE** 是调用该子例程时应该期望的参数的原型， **ATTRIBUTES** 是该子例程展示的属性列表。**原型**和**属性**参数是可选的。

**注意:**子程序可以命名，也可以匿名。Perl 也允许创建匿名子程序，即没有名字的子程序。这可以通过省略**名称**组件来实现。但是，如果没有定义，就不能创建匿名子例程(如果不知道子例程的名称，Perl 以后就无法附加定义)。您还需要将子例程分配给标量变量，以便以后调用它。

**示例:**

```
# Perl program to demonstrate
# simple subroutine

sub message    # Declared subroutine 
{ 
    print "Hello!\n";   # Body of subroutine
}

$message = message;    # Calling subroutine
```

**Output:**

```
Hello!

```

### 子程序范围

**作用域**的思想处理定义变量或子程序的区域，并且可以被程序的其他部分使用和访问。Perl 子程序主要支持两种范围- **词法**和**全局**。

就像变量一样，子程序也生活在一个特定的范围内，无论是**词法**还是**全局**范围。

**全局作用域**

如果子程序和变量可以在整个程序中的任何地方使用，那么它们就是**全局作用域**，除非分别被同名的词汇作用域子程序和变量覆盖。全局变量对程序的所有不同函数和库都是可用的，尽管它们需要在单独用于每个函数之前被加载。

> **语法:**
> 子假人($param1，$param2) {。。。}

这些子程序只能访问全局范围的变量。Perl 中的大多数内置都是全局范围的。

**例**

```
#!/usr/bin/perl

# Subroutine definition
sub Max 
{

    # get total number of arguments passed.
    $n = scalar(@_);     # local scoped 
    $max = 0;             # local scoped

    foreach $item (@_) 
    {
        if ($item > $max)
        {
            $max = $item;
        }
    }
    print "Max from the given numbers : $max\n";
}

# Subroutine call
Max(10, 20, 30, 40, 50, 100); # called globally

$user_input = "GeeksforGeeks";
if (length($user_input) >= 7)
{
    Max(45, 56, 78, 76, 26, 90);     # called locally
}
```

**Output:**

```
Max from the given numbers : 100
Max from the given numbers : 90

```

**词法范围**

子程序也可以**词法**作为变量。词法子程序是在**函数**或 If-Else 条件中声明和定义的子程序，只能在该范围内运行。在范围之外，它们不被程序的其他部分识别。词法子程序可以访问全局变量和局部变量(在其范围内定义)。词法子程序的调用就像普通子程序一样:

> **语法:**
> if $ condition 1
> {
> my sub 1($ param 1，$param2)
> {
> 。。。
> }
> 
> sub1($arg1，$ arg 2)；#范围内呼叫
> 
> # sub1($arg3，$ arg 4)；#错误–在范围外调用

对 sub1 的第一次调用没问题，但第二次调用可能是编译时错误，因为 sub1 已在其定义范围之外被调用。

**示例:**

```
#!/usr/bin/perl

$user_input = "Geeks";

if (length($user_input) >= 7) 
{
    # Subroutine definition local to IF block
    sub Max 
    {

        # get total number of arguments passed.
        $n = scalar(@_);     # local scoped 
        $max = 0;             # local scoped

        foreach $item (@_) 
        {
            if ($item > $max) 
            {
                $max = $item;
            }
        }
        print "Max from the given numbers : $max\n";
    }

    Max(45, 56, 78, 76, 26, 90);     #called locally
}
else 
{

    # Subroutine definition local to ELSE block
    sub Max 
    {

        # get total number of arguments passed.
        $n = scalar(@_);     # local scoped 
        $max = 0;             # local scoped

        foreach $item (@_) 
        {
            if ($item > $max) 
            {
                $max = $item;
            }
        }
        print "Max from the given numbers : $max\n";
    }

    Max(4, 6, 17, 37, 6, 9);     #called locally
}
```

**Output:**

```
Max from the given numbers : 37

```

### 使用`my`和`local`

Perl 子程序中的 **`my`** 和 **`local`** 用于限制程序中一个变量或一个子程序的范围。限制范围意味着限制可以访问相应变量的区域。

**`my`**

Perl 中的所有变量默认都是**全局**变量，这意味着编译器可以从程序中的任何地方访问它们。但是名为**词法**变量的私有变量也可以使用 **`my`** 运算符创建。
**`my`**关键字声明了一个要在当前块中限定范围的变量。在块的持续时间内，新的变量将优先于任何以前限定范围的变量。当块结束时，变量超出范围。

**例**

```
#!/usr/bin/perl

my $string = "GeeksforGeeks";
print "$string\n";
myfunction();   # function call
print "$string\n";

# Subroutine 1 definition
sub myfunction 
{

    # Private variable for function
    my $string = "GFG";
    print "Inside myfunction $string\n";
    mysub();
}

# Subroutine 2 definition
sub mysub
{
    print "Inside mysub $string\n";
}
```

**Output:**

```
GeeksforGeeks
Inside myfunction GFG
Inside mysub GeeksforGeeks
GeeksforGeeks

```

块终止的那一刻，变量就从视图中消失了。我们不能从定义变量的块外部访问用 **`my`** 声明的变量。
也意味着模块内用 **`my`** 声明的变量在该模块之外是不可访问的(因为该模块是单个块)，即使使用 **`$MyModule::string`** 显式调用。

 **的效果 **`local`** 变量实际上是一个动态范围的变量。它有效地在当前范围内创建了全局变量的**副本。它的操作就像一个词汇范围的变量；当变量超出当前范围时，它的效果会消失，而**变量会返回其原始值**，而不是简单地消失。****

****示例:****

```
#!/usr/bin/perl

$string = "GeeksforGeeks";
print "$string\n";
myfunction();
print "$string\n";

# Subroutine 1 definition
sub myfunction 
{

    # Private variable for function
    local $string = "GFG";
    print "Inside myfunction $string\n";
    mysub();
}

# Subroutine 2 definition
sub mysub
{
    print "Inside mysub $string\n";
}
```

****Output:**

```
GeeksforGeeks
Inside myfunction GFG
Inside mysub GFG
GeeksforGeeks

```** 

****注意:**使用 **`local`** 修改的变量的值对于从变量已经本地化的块调用的所有函数都是一致的。**

**所以， **`local`** 只是挂起全局变量，**为全局变量创建了一个临时范围**，而 **`my`** 在它定义的范围内定义了一个**新的词法变量**，一旦我们超出了它的定义范围，这个变量就会被销毁。

**`our`**

的效果 Perl 支持另一个作用域声明，使我们能够使用关键字 **`our`** 创建一个选择性全局变量。 **`our`** 声明是一个相对较新的发明，它允许您声明一个变量是全局的，并且可能被脚本中定义的任何其他子例程使用。
**`my`**和 **`our`** 都是词汇范围变量的例子。唯一的区别在于词汇范围的应用水平。**

****示例:****

```
#!/usr/bin/perl

our $string = "GeeksforGeeks";
print "$string\n";
myfunction();
print "$string\n";

# Subroutine definition
sub myfunction 
{

    # Private variable for function
    our $string = "GFG";
    print "Inside myfunction $string\n";
}
```

****Output:**

```
GeeksforGeeks
Inside myfunction GFG
GFG

```** 

**在一个函数内使用 **`our`** ，或者在任何块内使用任何形式的嵌套，对同一个变量没有影响。它总是引用同一个全局变量。在用 **`my`** 声明的变量上使用 **`our`** 将没有效果。**