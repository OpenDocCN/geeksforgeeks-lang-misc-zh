# Perl |反转一个数组

> 原文:[https://www.geeksforgeeks.org/perl-reverse-an-array/](https://www.geeksforgeeks.org/perl-reverse-an-array/)

在 Perl 中反转数组或字符串。

**迭代方式:**
从 0 到数组中间迭代数组。
用 arr[size-i]元素替换 arr[i]元素。

```
#Perl code to reverse an array iteratively

#declaring an array of integers
@arr = (2, 3, 4, 5, 6, 7);

# Store length on array in $n variable
$n = $#arr;

#Print the original array
print "The original array is : ";
for $i (0 .. $#arr)
{
    print $arr[$i], " ";
}

#run a loop from 0 to mid of array
for my $i (0 .. $#arr/2)
{
    #swap the current element with size-current element
    $tmp = $arr[$i];
    $arr[$i] = $arr[$n-$i];
    $arr[$n-$i] = $tmp;
}

#Print the reversed array
print "\nThe reversed array is : ";
for $i (0 .. $#arr)
{
    print $arr[$i], " ";
}
```

**Output:**

```
The original array is : 2 3 4 5 6 7 
The reversed array is : 7 6 5 4 3 2

```

**使用内置函数:**
Perl 有一个内置函数来反转数组、字符串或数字。

```
#Perl code to reverse an array using inbuilt function reverse

#declaring an array of integers
@arr = (2, 3, 4, 5, 6, 7);

#Print the original array
print "The original array is : ";
for $i (0 .. $#arr)
{
    print $arr[$i], " ";
}

#store the reversed array in @rev_arr
@rev_arr = reverse(@arr);

#Print the reversed array
print "\nThe reversed array is : ";
for $i (0 .. $#rev_arr)
{
    print $rev_arr[$i], " ";
}
```

**Output:**

```
The original array is : 2 3 4 5 6 7 
The reversed array is : 7 6 5 4 3 2

```