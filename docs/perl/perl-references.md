# Perl |参考文献

> 原文:[https://www.geeksforgeeks.org/perl-references/](https://www.geeksforgeeks.org/perl-references/)

在 Perl 中，我们使用变量来访问存储在内存位置的数据(所有数据和函数都存储在内存中)。变量被赋予在各种操作中使用的数据值。 **Perl Reference** 是一种访问相同数据但使用不同变量的方式。Perl 中的引用是保存另一个变量位置的[标量](https://www.geeksforgeeks.org/perl-scalars/)数据类型。另一个变量可以是标量、散列、数组、函数名等。嵌套数据结构可以很容易地创建，因为用户可以创建一个包含对另一个列表的引用的列表，该列表可以进一步包含对数组、[标量](https://www.geeksforgeeks.org/perl-scalars/)或散列等的引用。

#### 参考创建

您可以为[标量](https://www.geeksforgeeks.org/perl-scalars/)值、散列、数组、函数等创建引用。为了创建一个引用，定义一个新的标量变量，并通过在它前面加一个反斜杠来为它指定变量的名称(您想要创建它的引用)。

**示例:**引用不同的数据类型:

```
# Array Reference

# defining array 
@array = ('1', '2', '3');

# making reference of array variable  
$reference_array = \@array;  

```

```
# Hash Reference

# defining hash
%hash = ('1'=>'a', '2'=>'b', '3'=>'c'); 

# make reference of the hash variable
$reference_hash = \%hash;   

```

```
# Scalar Value Reference

# defining scalar
$scalar_val = 1234;

# making reference of scalar variable
$reference_scalar = \$scalar_val; 

```

**注:**

*   A *reference to an anonymous* [**hash**](https://www.geeksforgeeks.org/perl-hashes/) can be created using the *curly brackets {}* around the key and value pairs.

    **示例:**

    ```
    # creating reference to anonymous hash
    $ref_to_anonymous_hash = {'GFG' => '1', 'Geeks' => '2'};

    ```

*   A *reference to an anonymous array* can be created using the *square brackets []*.

    **示例:**

    ```
    # creating reference to an anonymous array
    $ref_to_anonymous_array = [20, 30, ['G', 'F', 'G']];

    ```

*   A *reference to an anonymous subroutine* can also be created with the help of **sub**. Here there will be no name for the **sub**.

    **示例:**

    ```
    # creating reference to an anonymous subroutine
    $ref_to_anonymous_subroutine = sub { print "GeeksforGeeks\n"};

    ```

*   无法创建对输入/输出句柄的引用，即目录句柄和文件句柄*。*

#### *取消引用*

*现在，在我们进行了引用之后，我们需要使用它来访问值。**取消引用**是访问引用所指向的内存中的值的方式。为了取消引用，我们根据变量的类型使用前缀 **$、@、%或&** (引用可以指向数组、标量或散列等)。*

***例 1:***

```
*# Perl program to illustrate the 
# Dereferencing of an Array

# defining an array
@array = ('1', '2', '3');  

# making an reference to an array variable
$reference_array = \@array;  

# Dereferencing
# printing the value stored 
# at $reference_array by prefixing 
# @ as it is a array reference
print @$reference_array;    *
```

***Output:**

```
123

```* 

***例 2:***

```
*# Perl program to illustrate the 
# Dereferencing of a Hash

# defining hash
%hash = ('1'=>'a', '2'=>'b', '3'=>'c');

# creating an reference to hash variable
$reference_hash = \%hash;   

# Dereferencing
# printing the value stored 
# at $reference_hash by prefixing 
# % as it is a hash reference
print %$reference_hash;  *
```

***Output:**

```
3c2b1a

```* 

***例 3:***

```
*# Perl program to illustrate the 
# Dereferencing of a Scalar

# defining a scalar
$scalar = 1234;

# creating an reference to scalar variable 
$reference_scalar = \$scalar; 

# Dereferencing
# printing the value stored 
# at $reference_scalar by prefixing 
# $ as it is a Scalar reference
print $reference_scalar;  *
```

***Output:**

```
1234

```*