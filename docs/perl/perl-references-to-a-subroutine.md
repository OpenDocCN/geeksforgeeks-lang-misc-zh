# Perl |对子程序的引用

> 原文:[https://www . geesforgeks . org/perl-references-to-a-sublog/](https://www.geeksforgeeks.org/perl-references-to-a-subroutine/)

**先决条件:** [Perl 引用](https://www.geeksforgeeks.org/perl-references/)

### 声明对子程序的引用

在 Perl 中，**引用**顾名思义就是指向另一个对象的引用或指针。参考资料实际上提供了各种能力和设施，否则这些能力和设施是不可用的，可以用来创建复杂的结构，如**调度表**、**高阶程序**、**闭包**等。对于第一次使用 Perl 的 C 程序员来说，引用完全像一个指针，只是在 Perl 中更容易使用，更切题，更实用。有两种类型的引用:**符号化的**和**硬的**。
**符号**引用使您能够使用另一个变量的值作为对变量名称的引用。例如，如果变量$val 包含字符串“文本”，那么对$val 的符号引用就是指变量$Text。
A **硬**引用是数据结构中包含的实际数据的术语。然而，它所指向的数据结构的形式在很大程度上是不相关的。虽然硬引用可以引用单个标量，但它也可以引用标量数组、散列或子例程。

```
$val = "Text";
$val_ref = \$val;

# For other variables
$array = \@ARGV;
$hash = \%ENV;

# For reference to subroutine
sub val { print "val" };
$valsub = \&val;
```

### 调用子程序引用

调用子程序引用也称为**解引用**。它是从结构中提取信息的行为。当您取消引用标量引用时，您实际上是在引用原始数据结构。取消引用的最直接的方法是在包含引用的标量变量之前添加相关的数据类型字符( **$** 用于标量， **@** 用于数组， **%** 用于散列，以及 **&** 用于子程序)。

```
$val_ref = \$val;       # Create reference to scalar
$array = \@ARGV;        # Create reference to array
$hash = \%ENV;          # Create reference to hash
$valsub = \&            # Create reference to subroutine

# Dereferencing
$val_ref;
$array[0, 1, ....];
$hash{'...'};
&$valsub;
```

> **注意:**取消引用信息的行为必须是明确的。在 Perl 中，任何结构都不支持隐式取消引用。

子程序既可以是**命名的**，也可以是**匿名的**。Perl 提供了声明对两种类型的子例程的引用以及取消引用它们的功能。
**例 1:**

## 实际抽取与汇报语言

```
#!/usr/bin/perl

# Perl program to demonstrate
# reference to subroutines

# Creating a named subroutine
sub name
{
    return "GeeksforGeeks";
}

# Create callable reference
# to named subroutine
$rs1 = \&name;    
print("Reference to named subroutine: ", $rs1);
print("\nAfter dereferencing, value : ", &$rs1);

# Create a reference to an
# anonymous subroutine
$rs2 = sub{
               return "GFG";
          };
print("\n");
print("\nReference to anonymous subroutine: ", $rs2);
print("\nAfter dereferencing, value : ", &$rs2);
```

**Output**

```
Reference to named subroutine: CODE(0x981750)
After dereferencing, value : GeeksforGeeks

Reference to anonymous subroutine: CODE(0x981870)
After dereferencing, value : GFG
```

**中缀**操作的使用如下例所示。中缀操作提供了一种从复杂或嵌套结构中提取信息的更好、更简单的方法。
T3】例 2:

## 实际抽取与汇报语言

```
#!/usr/bin/perl

# Perl program to demonstrate
# reference to subroutines

$rs = \&func1;

# Prints "GeeksforGeeks"
$rs->("Geeks")->("for")->("Geeks");    

sub func1
{
    my $val = shift;
    print "$val";
    return \&func2;
}

sub func2
{
    my $val = shift;
    print "$val";
    return \&func3;
}

sub func3
{
    my $val = shift;
    print "$val\n";
}
```

**Output:** 

```
GeeksforGeeks
```

### 回收

**回调**是开发 Perl **Tk 接口**时应该记住的重要元素之一。当我们达到某个条件点或执行某个动作时，它会从脚本的另一部分回调一段代码。
回调有点像代码的延迟执行，它是由事件触发的，而不是以线性方式执行事情。对于这种事件驱动的代码功能，我们经常在需要时使用子例程引用来调用这种代码片段。
**例:**

## Perl 语言

```
# Perl program to demonstrate
# the use of callbacks
sub alt {
            print "$a $b\n";
            $arr{$a} cmp $arr{$b};
        }

%arr = ("Marcelo", "Lewis",
        "Rodrygo", "Peter",
        "Sandro", "James");

# @names = sort alt (keys(%arr));
@names = calc ("Alternate", keys(%arr));
foreach $person (@names)
{
    print "$person teams up with $arr{$person}\n";
}

# Example code to show
# what really goes on inside sort.
sub calc
{
    my ($subn, @final) = @_;
    for ($k = 0; $k < $final; $k++)
    {
        $count = 0;
        for ($j = 0; $j < $final - $k; $j++)
        {
            $a = $final[$j];
            $b = $final[$j + 1];
            if (&{$subn}() > 0 )
            {
                $final[$j] = $b;
                $final[$j + 1] = $a;
                $count++;
            }
        }
        last unless ($count);
    }
    return @final
}
```

**Output:** 

```
Sandro teams up with James
Rodrygo teams up with Peter
Marcelo teams up with Lewis
```

上面的例子描述了使用回调函数 **calc** 基于散列中保存的值的字符数(长度)对散列关键字列表进行排序。

### 引用的数组和散列

除了数组和散列的常规约束之外，您还可以创建由两者的组合组成的复杂结构。这些是嵌套的或复杂的结构，它们可以用来以易于使用的格式建模复杂的数据。嵌套结构的实际情况是，Perl 将嵌套数据类型存储为对匿名变量的引用。例如，在二维数组中，主数组是引用列表，子数组是这些引用指向的匿名数组。这意味着“数组的数组”实际上意味着数组引用的数组。所有嵌套结构也是如此；而且，尽管看起来很复杂，但它确实为创建复杂的嵌套结构提供了一种合适的强大方法。
**例 1:**

## 实际抽取与汇报语言

```
w
# Perl program to demonstrate
# array of references

# Declaring a reference to a nested array
$array = [[1, 2, 3, 4, 5],
          ['Geeks', 'for', 'Geeks'],
          [6, 7, 8, 9]];

# Access element using index
# Dereferencing performed
print("$array[1][2]");    

# Access element using infix method
print("\n$array->[1][1]");
print("\n$array->[1]->[0]");

# Printing complete nested array
print("\nElements in the array are :");
print("\n");
for(my $i = 0; $i < scalar(@{$array}); $i++)
{
    for(my $j = 0; 
           $j < scalar(@{$array->[$i]}); $j++)
    {
        print($array[$i][$j]);
        print(" ");
    }
    print("\n");
}
```

**Output:** 

```
Geeks
for
Geeks
Elements in the array are :
1 2 3 4 5 
Geeks for Geeks 
6 7 8 9
```

**例 2:**

## 实际抽取与汇报语言

```
#!/usr/bin/perl

# Perl program to demonstrate
# array of references
use strict;
use warnings;

my %friends = ( 1 => 'John',     4 => 'Sandro',
                2 => 'Rodrygo', 5 => 'Peter',
                3 => 'Marcelo', 6 => 'Luis' );

# Declaring a Reference to the hash
my $hash_ref = \%friends;

# Access element from hash using key value
print("$hash_ref{1}\n");     # prints John

# Acces element using infix operation
print("$hash_ref->{3}\n");

# Print all elements of the hash
# with their keys
print ("The hash stored is :\n");

for (keys %$hash_ref)
{
    print("$_ = $hash_ref->{$_}\n");
}
```

**Output:** 

```
John
Marcelo
The hash stored is :
4 = Sandro
1 = John
2 = Rodrygo
5 = Peter
3 = Marcelo
6 = Luis
```