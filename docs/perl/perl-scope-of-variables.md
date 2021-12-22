# Perl |变量范围

> 原文:[https://www.geeksforgeeks.org/perl-scope-of-variables/](https://www.geeksforgeeks.org/perl-scope-of-variables/)

变量的作用域是程序中可访问变量的部分。范围也称为程序中变量的可见性。在 Perl 中，我们可以声明**全局变量**或者**私有变量**。私有变量也被称为*词汇变量*。

#### 全局变量的范围

全局变量可以在程序中创建的任何函数或块中使用。它在整个程序中是可见的。全局变量可以直接使用，并且可以从程序的每个部分访问。

**示例 1:** 变量 *$name* 在代码的开头声明。它在文件的末尾随处可见。即使在街区内。即使那些在函数声明中。如果我们改变块内的变量，将会改变代码其余部分的值。即使在街区外。

```
# Perl program to illustrate the 
# Scope of Global variables

# declaration of global variable 
$name = "GFG";

# printing global variable 
print "$name\n";    

# global variable can be used 
# inside a block, hence the we 
# are taking a block in which
# we will print the value of 
# $name i.e. global variable
{

    # here GFG will print
    print "$name\n"; 

    # values in global variable can be
    # changed even within a block, 
    # hence the value of $name is 
    # now changed to "GeeksforGeeks"
    $name = "GeeksforGeeks"; 

    # print function prints
    # "GeeksforGeeks"
    print "$name\n"; 
}

# changes made inside the above block'
# are reflected in the whole program 
# so here GeeksforGeeks will print
print "$name\n"; 
```

**Output:**

```
GFG
GFG
GeeksforGeeks
GeeksforGeeks

```

**例 2:**

```
# Perl program to illustrate the 
# Scope of Global variables

# declaration of global variables
$name = "GFG"; 
$count = 1;

# printing global variables
print $count." ".$name."\n";
$count++;

# Block starting
{

    # global variable can be used inside
    # a block, so below statement will 
    # print GFG and 1
    print $count." ".$name."\n";

    # incrementing the value of 
    # count inside the block
    $count++;
}

# taking a function
sub func {

    # Global variable, $count and $name,
    # are accessible within function
    print $count." ".$name."\n";
}

# calling the function
func();
```

**Output:**

```
1 GFG
2 GFG
3 GFG

```

#### 词汇变量的范围(私有变量)

Perl 中的私有变量是在变量前使用 **my** 关键字定义的。**我的**关键字将变量限制在声明它的函数或块中。块可以是 for 循环、while 循环，也可以是一个带有大括号的代码块。局部变量的作用域是局部的，它存在于两个大括号(代码块)之间，在代码块之外，这个变量不存在。这些变量也被称为词汇变量。

**注意:**当在函数或块中使用私有变量时，它们会隐藏以相同名称创建的全局变量。当我们调用带有私有变量的子例程时，它可以在该函数中使用。子程序一退出，私有变量就不能再使用了。

**示例:**

```
# Perl program to illustrate the 
# scope of private variables

# declaration of global variable 
$name = "Global"; 
$count = 1;

# printing global variables
print $count." ".$name."\n";

# incrementing the value of count
# i.e it become 2
$count++;

# block starting
{

    # declaring private variable by using my 
    # keyword which can only be used
    # within this block
    my $new_name = "Private"; 

    # global variables are 
    # accessible inside block
    print $count." ".$name."\n";

    # incrementing the value
    # of global variable
    # here it become 3
    $count++;

    print $name." and ".$new_name."\n";
}

# $new_name variable cannot 
# be used outside, hence nothing 
# is going to print 
print "Variable defined in above block: ".$new_name."\n"; 

# declaring function
sub func {

    # this private variable declaration
    # hides the global variable which define
    # in the beginning of program
    my $name = "Hide"; 
    print $count." ".$name."\n";

}

# calling the function
func();
```

**Output:**

```
1 Global
2 Global
Global and Private
Variable defined in above block: 
3 Hide

```

#### 包变量

在 Perl 中，我们还有一种类型的作用域，叫做包作用域。当我们需要创建可以在不同名称空间中独占使用的变量时，就会用到它。“ **main** ”是每个 Perl 程序中的默认命名空间。Perl 中的名称空间是使用**包**关键字定义的。

**示例:**

```
# Perl program to illustrate 
# the Package Variables

# variable declared in 
# main namespace
$var1 = "Main Namespace";

print "Value of Var1: ".$var1."\n";

# package declaration
# Pack1 is the package 
package Pack1;

    # since $var1 belongs to main namespace, 
    # so nothing will print inside Pack1
    # namespace
    print "Value of var1: ".$var1."\n"; 

    # variable declared in Pack1 namespace
    # having same name as main namespace
    $var1 = "Pack1 Namespace";

    # here $var1 belongs to Pack1 namespace
    print "Value of var1: ".$var1."\n";

    # in-order to print variables 
    # from both namespace, use 
    # following method
    print "Value of var1: ".$main::var1."\n";
    print "Value of var1: ".$Pack1::var1."\n";
```

**Output:**

```
Value of Var1: Main Namespace
Value of var1: 
Value of var1: Pack1 Namespace
Value of var1: Main Namespace
Value of var1: Pack1 Namespace

```

**Perl 中的 Our 关键字:**“Our”关键字只创建同名的现有包变量的别名。**我们的**关键字允许使用包变量，而不用用包名限定它，但是只能在“*我们的*声明的词法范围内。用**声明的变量我们的**关键字声明了一个包变量的别名，该变量将在其整个词法范围内可见，**甚至跨越包边界**。

```
# Perl program to illustrate the use 
# of our keyword

# Pack1 namespace declared
# by using the package keyword
package Pack1;

    # declaring $Pack1::first_name 
    # for rest of lexical scope
    our $first_name;    
    $first_name = "Shashank";

    # declaring $Pack1::second_name for
    # only this namespace
    $second_name;    
    $second_name = "Sharma";

# Pack2 namespace declared
package Pack2;

    # prints value of $first_name, as it 
    # refers to $Pack1::first_name
    print "first_name = ".$first_name."\n";

    # It will print nothing as $second_name
    # does not exist in Pack2 package scope
    print "second_name = ".$second_name."\n";  
```

**Output:**

```
first_name = Shashank
second_name =

```