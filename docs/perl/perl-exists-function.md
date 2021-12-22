# Perl | exists()函数

> 原文:[https://www.geeksforgeeks.org/perl-exists-function/](https://www.geeksforgeeks.org/perl-exists-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 exists()函数用于检查给定数组或哈希中的元素是否存在。如果给定数组中存在所需的元素，则该函数返回 1，否则散列返回 0。

> **语法:**存在(表达式)
> 
> **参数:**
> **表达式:**这个表达式要么是数组，要么是散列，在这个散列上存在要调用的函数。
> 
> **如果给定数组中存在所需元素，则返回:** 1，否则返回 0。

**示例 1:** 本示例在数组上使用 exists()函数。

```
#!/usr/bin/perl 

# Initialising an array
@Array = (10, 20, 30, 40, 50);

# Calling the for() loop over
# each element of the Array
# using index of the elements
for ($i = 0; $i < 10; $i++)
{

    # Calling the exists() function
    # using index of the array elements
    # as the parameter
    if(exists($Array[$i]))
    {
        print "Exists\n";
    }
    else
    {
        print "Not Exists\n"
    }
}
```

 **输出:**

```
Exists
Exists
Exists
Exists
Exists
Not Exists
Not Exists
Not Exists
Not Exists
Not Exists

```

在上面的代码中，可以看到 exists()函数的参数是给定数组的每个元素的索引，因此直到索引 4(索引从 0 开始)它给出输出为“Exists”，随后给出“Not Exists”，因为索引从数组中取出。

**示例 2:** 本示例在哈希上使用 exists()函数。

```
#!/usr/bin/perl 

# Initialising a Hash
%Hash = (Mumbai => 1, Kolkata => 2, Delhi => 3);

# Calling the exists() function
if(exists($Hash{Mumbai}))
{
    print "Exists\n";
}
else
{
    print "Not Exists\n"
}

# Calling the exists() function
# with different parameter
if(exists($Hash{patna}))
{
    print "Exists\n";
}
else
{
    print "Not Exists\n"
}
```

**输出:**

```
Exists
Not Exists

```

在上面的代码中，exists()函数以给定哈希的关键字为参数，检查它是否存在。