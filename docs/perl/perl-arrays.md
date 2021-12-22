# Perl |数组

> 原文:[https://www.geeksforgeeks.org/perl-arrays/](https://www.geeksforgeeks.org/perl-arrays/)

在 Perl 中， ***数组*** 是一种特殊类型的变量。数组用于存储值列表，列表中的每个对象被称为一个元素。元素可以是数字、字符串或任何类型的 **[标量](https://www.geeksforgeeks.org/perl-scalars/)** 数据，包括另一个变量。
![arrays](img/13b7429b646a58c1b6e67867ce0dab9c.png)

**例:**

```
@number = (50, 70, 46);             
@names = ("Geeks", "For", "Geeks");

```

**数组创建:**在 Perl 编程中，每个数组变量都是使用变量名称前的**“@”**符号来声明的。单个数组也可以存储多种数据类型的元素。例如:

```
# Define an array
@arr = (1, 2, 3);
@arr = (1, 2, 3, "Hello");

```

**数组创建使用 qw 函数:**
***qw()*** 函数是创建单引号单词数组最简单的方法。它将一个表达式作为输入，提取由空格分隔的单词，然后返回这些单词的列表。最好的是表达式可以被任何分隔符包围，比如- () " [] {} //等等。但是一般使用()和//。

**语法:**

```
qw (Expression)
qw /Expression/
qw 'Expression'
qw {Expression}

```

**示例:**

```
# Perl program to demonstrate qw function

# using qw function
@arr1 = qw /This is a Perl Tutorial by GeeksforGeeks/;

# Creates array2 with elements at
# index 2,3,4 in array1
@arr2 = @arr1[2,3,4]; 

print "Elements of arr1 are:\n";
foreach $ele (@arr1)
{
    print "$ele \n";
}

print "Elements of arr2 are:\n";
foreach $ele (@arr2)
{
     print "$ele \n";
}
```

**输出:**

```
Elements of arr1 are:
This 
is 
a 
Perl 
Tutorial 
by 
GeeksforGeeks 
Elements of arr2 are:
a 
Perl 
Tutorial 

```

**访问数组元素:**要访问数组元素，我们必须在**“{ content }”前加前缀；**数组变量名前的符号，后跟方括号内的索引。例如:

```
# Define an array
@arr = (1, 2, 3);

# Accessing and printing first 
# element of an array
print "$arr[0]\n";

# Accessing and printing second
# element of an array
print "$arr[1]\n";

```

**示例:**

```
# Perl program to demonstrate Array's
# creation and accessing the array's elements

# Creation an array fruits
@fruits = ("apple", "banana", "pineapple", "kiwi");

# printing the array
print "@fruits\n";

# Prints the array's elements
# one by one using index
print "$fruits[0]\n";
print "$fruits[1]\n";
print "$fruits[2]\n";
print "$fruits[3]\n";
```

**输出:**

```
apple banana pineapple kiwi
apple
banana
pineapple
kiwi

```

**注意:**数组索引总是从零开始。要访问第一个元素，它必须给出 0 作为索引。我们也可以给一个*负指数*。但是给出负的索引将导致从结尾而不是从开头选择数组元素。

**示例:**

```
# Perl program to demonstrate 
# negative index of array

# Creation an array fruits
@fruits = ("apple", "banana", "pineapple", "kiwi");

# Prints the array's elements
# one by one using negative index
print "$fruits[-1]\n";
print "$fruits[-2]\n";
```

**输出:**

```
kiwi
pineapple
```

**顺序数字数组:** Perl 还提供了一个制作数字或字母顺序数组的快捷方式。这使得用户的任务变得容易。当数到 1000 或字母 A 到 Z 等时，使用顺序数字数组，用户可以跳过循环并键入每个元素。

**示例:**

```
@array = (1..9); # array with numbers from 1 to 9
@array = (a..h); # array with letters from a to h

```

**程序:**

```
# Perl program to demonstrate
# Sequential Number Arrays

# Sequential Number Arrays for 
# numbers and letters
@nums = (1..9);
@letters = (a..h);

# Prints array- nums
print "@nums\n"; 

# Prints array- letters
print "@letters\n";  
```

**输出:**

```
1 2 3 4 5 6 7 8 9
a b c d e f g h

```

**数组的大小:**数组的大小(数组的物理大小)可以通过在标量上下文中评估数组来找到。返回值将是数组中的元素数。一个数组可以在标量上下文中使用两种*方式进行计算:*

1.  **隐式标量上下文**

    ```
    $size = @array;
    ```

2.  **使用关键字标量的显式标量上下文**

    ```
    $size = scalar @array;
    ```

两种方式都会产生相同的输出，因此最好使用隐式标量上下文。

**示例:**

```
# Perl program to demonstrate 
# the length of an array

# declaring an array
@arr = (11, 22, 33, 44, 55, 66);

# Storing the length of array 
# in variable imp_size
# implicit scalar context
$imp_size = @arr;

# Storing the length of array
# in variable exp_size
# explicit scalar context
$exp_size = scalar @arr;

print "Size of arr(imp_size) $imp_size\n";
print "Size of arr(exp_size) $exp_size";
```

**输出:**

```
Size of arr(imp_size) 6
Size of arr(exp_size) 6

```

**注意:**在 Perl 数组中，数组的大小总是等于(maximum_index + 1)，即

```
size = maximum_index + 1
```

并且可以使用**$ #数组**找到数组的最大索引。所以*@数组*和标量*@数组*总是用来求数组的大小。

**示例:**

```
# Perl program to find size and 
# maximum index of an array

#!/usr/bin/perl

# Array declaration and 
# assigning values to it
@arr = (10, 17, 19, 20, 25);

# to find size of array
$size_of_array = @arr;

# to find Maximum index of array
$maximum_index = $#arr;

# displaying result
print "Maximum Index of the Array: $maximum_index\n";
print "The Size of the Array:  $size_of_array\n";
```

**输出:**

```
Maximum Index of the Array: 4
The Size of the Array:  5

```

**迭代数组:**我们可以通过两种方式迭代数组:

*   **Iterating through the range:** We can iterate through the range by finding the size of an array and then running a for loop from 0 to the size – 1 and then accessing the elements of the array.

    **示例:**

    ```
    # Perl program to illustrate 
    # iteration through range

    # array creation
    @arr = (11, 22, 33, 44, 55);

    # size of array
    $len = @arr;

    for ($b = 0; $b < $len; $b = $b + 1)
    {
        print "\@arr[$b] = $arr[$b]\n";
    }
    ```

    **输出:**

    ```
    @arr[0] = 11
    @arr[1] = 22
    @arr[2] = 33
    @arr[3] = 44
    @arr[4] = 55

    ```

*   **Iterating through elements(foreach Loop):** We can iterate through the elements using foreach loop. Using this we can directly access the elements of the array using a loop instead of running a loop over its range and then accessing the elements.

    **示例:**

    ```
    # Perl program to illustrate Iterating 
    # through elements(foreach Loop)

    # creating array
    @l = (11, 22, 33, 44, 55);

    # foreach loop
    foreach $a (@l)
    {
          print "$a ";
    }
    ```

    **输出:**

    ```
    11 22 33 44 55

    ```