# Perl |多维哈希

> 原文:[https://www.geeksforgeeks.org/perl-multidimensional-hashes/](https://www.geeksforgeeks.org/perl-multidimensional-hashes/)

**Prerequisite:**

[Hashes-Basics](https://www.geeksforgeeks.org/perl-hash/)

### 介绍

除了哈希的常规约束，我们还可以创建由两者组合而成的复杂结构。这些是**嵌套的**或**复杂的**结构，它们可以用来以易于使用的
格式建模复杂的数据。

在所有 Perl 的嵌套结构中，多维散列或散列的 T2 散列是最灵活的。这就像建立一个本身包含一组其他记录的记录。

创建散列的格式类似于数组的数组。简单地说，不是将值分配给普通散列中的主键，而是将包含辅助键及其各自值的整个散列分配给外部散列的主键。

> **语法:**
> 
> my % hash =(primary _ key = > { secondary _ key = > { sub _ sec _ key = > {…} })；

**示例:**

以下示例显示了描述公司组织的哈希散列。主键是部门，嵌套键是员工姓名。这些值包含相应员工的职称。

```
# !/usr/bin/perl 
# Perl program to demonstrate 
# Multidimensional hash

use strict; 
use warnings;
use Data::Dumper qw(Dumper); 

# Creating a 2D hash
my %company = ('Sales' =>    {
                                'Brown' => 'Manager',
                                'Smith' => 'Salesman',
                                'Albert' => 'Salesman', 
                            }, 
            'Marketing' =>  {
                                'Penfold' => 'Designer',
                                'Evans' => 'Tea-person',
                                'Jurgens' => 'Manager', 
                            },
            'Production' => {
                                'Cotton' => 'Paste-up',
                                'Ridgeway' => 'Manager',
                                'Web' => 'Developer', 
                            },
            ); 

# Print the List 
print Dumper(\%company);
```

**Output:**

```
$VAR1 = {
          'Marketing' => {
                           'Evans' => 'Tea-person',
                           'Jurgens' => 'Manager',
                           'Penfold' => 'Designer'
                         },
          'Sales' => {
                       'Smith' => 'Salesman',
                       'Albert' => 'Salesman',
                       'Brown' => 'Manager'
                     },
          'Production' => {
                            'Ridgeway' => 'Manager',
                            'Web' => 'Developer',
                            'Cotton' => 'Paste-up'
                          }
        };

```

在上例中， **Dumper** 函数的输入是对数据结构的引用，因此我们在%company 前面放了一个反斜杠 **(\)** 。
**注意:**密钥的顺序是随机的，因为散列不会将它们保持在任何特定的顺序中。

**其他一些操作:**

*   **向现有哈希添加另一个匿名成员:**

    > **语法:**
    > $ company { ' new _ key ' } = { ' sub _ key 1 ' =>值 1、
    > 'sub_key2' = >值 2、
    > ' sub _ key 3 ' = >值 3
    > }；

*   **Access specific value:**

    > **Syntax:**
    > Print $ company {"production"} {"web"}; # Developer

    will be output.
*   **set value of a specific key:**

    > **Syntax:**
    > $ Company {$ Production}-> {"Web"} = Senior developer; # Change the website to senior developer

### 遍历多维哈希

要遍历多维散列或散列中的每个值，只需遍历外部散列的键，然后遍历内部散列的键。

对于 N 维散列，需要 N 个嵌套或嵌入的循环来遍历整个散列。和**的**和**循环都可以用于循环到哈希。**

**语法:**

```
for $key (keys %hash) 
{
    print "$key: \n";
    for $ele (keys %{$hash{$key}})
    {
        print "  $ele: " . $hash{$key}->{$ele} . "\n";
    }
}
```

对于大规模多维散列，使用每个**关键字同时检索键和值可能会稍微快一些。**

**语法:**

```
while (($key, $ele) = each %hash) 
{
    print "$key: \n";
    while (($ele, $sub_ele) = each %$ele) 
    {
        print " $ele = $sub_ele ";
    }
    print "\n";
}
```

以下示例说明了使用`**For**`和`**while**`循环遍历多维散列:
**示例:**

```
# !/usr/bin/perl 
# Perl program to demonstrate
# Traversing of 
# Multidimensional hash
use strict; 
use warnings;
use Data::Dumper qw(Dumper); 

my %company = ('Sales' =>    {
                                'Brown' => 'Manager',
                                'Smith' => 'Salesman',
                                'Albert' => 'Salesman', 
                            }, 
            'Marketing' =>  {
                                'Penfold' => 'Designer',
                                'Evans' => 'Tea-person',
                                'Jurgens' => 'Manager', 
                            },
            'Production' => {
                                'Cotton' => 'Paste-up',
                                'Ridgeway' => 'Manager',
                                'Web' => 'Developer', 
                            },
            ); 

print "Traversing hash using For loop: "."\n";
print "\n";

# traversing hash using for loop
for my $key (keys %company) 
{
    print "$key: \n";
    for my $ele (keys %{$company{$key}}) 
    {
        print " $ele: " . $company{$key}->{$ele} . "\n";
    }
}

print "\nTraversing hash using while" . 
      "loop using each keyword: " . "\n";
print "\n";

# traversing hash using each keyword
# and while loop
while ((my $key, my $ele) = each %company)
{
    print "$key: \n";
    while ((my $ele, my $sub_ele) = each %$ele)
    {
        print " $ele = $sub_ele ";
    }
    print "\n";
}
```

**Output:**

```
Traversing hash by For loop.

Marketing: 
 Evans: Tea-person
 Jurgens: Manager
 Penfold: Designer
Sales: 
 Brown: Manager
 Albert: Salesman
 Smith: Salesman
Production: 
 Cotton: Paste-up
 Web: Developer
 Ridgeway: Manager

Traversing hash using while loop with each keyword.

Marketing: 
 Evans=Tea-person  Jurgens=Manager  Penfold=Designer 
Sales: 
 Brown=Manager  Albert=Salesman  Smith=Salesman 
Production: 
 Cotton=Paste-up  Web=Developer  Ridgeway=Manager 

```

### 检查多维哈希中的键是否存在

很多时候，当使用 Perl 散列时，我们需要知道散列中是否已经存在某个密钥。给定一个散列，可以通过使用 **`[exists](https://www.geeksforgeeks.org/perl-exists-function/)`** 关键字来检查特定密钥的存在。
在像上面例子中使用的**% company】**这样的多维散列中，必须使用关键字 **`exists`** 直到被检查是否存在的密钥的深度级别已经达到。

> **语法:**
> if(exists($ hash { key }){
> if(exists($ hash { key } { sub _ key }){
> …。
> }

使用第 n 级构造时也应该小心，不要先尝试第(n-1)级，因为这可能会触发不需要的**自动活体化**

**示例:**

这里有一个简单的例子，演示了 Perl `**exists**`散列函数。在这个 Perl 脚本中，我们将首先创建一个简单的 Perl 散列，然后我们将使用`**exists**`函数来查看散列中是否存在名为‘Albert’的散列关键字。

```
# !/usr/bin/perl 
# Perl program to check for
# existence of a key in a
# Multidimensional hash
use strict; 
use warnings;

my %company = ('Sales' =>    {
                                'Brown' => 'Manager',
                                'Smith' => 'Salesman',
                                'Albert' => 'Salesman', 
                            }, 
            'Marketing' =>  {
                                'Penfold' => 'Designer',
                                'Evans' => 'Tea-person',
                                'Jurgens' => 'Manager', 
                            },
            'Production' => {
                                'Cotton' => 'Paste-up',
                                'Ridgeway' => 'Manager',
                                'Web' => 'Developer', 
                            },
            ); 

# Check for key existence
if (exists $company{"Sales"}) 
{
    print "Sales department exists.\n";
    if (exists $company{"Sales"}{"Albert"}) 
    {
        print "Albert is " . $company{"Sales"}{"Albert"} . 
              " of Sales department . \n";
    }
    else 
    {
        print "Albert is not a member of Sales department.\n";
    }
}
else 
{
    print "Sales department do not exists.\n";
}
```

**Output:**

```
Sales department exists.
Albert is Salesman of Sales department.

```