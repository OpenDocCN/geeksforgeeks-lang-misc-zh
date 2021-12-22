# Perl | srand()函数

> 原文:[https://www.geeksforgeeks.org/perl-srand-function/](https://www.geeksforgeeks.org/perl-srand-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 srand()函数帮助 rand()函数在每次程序运行时生成一个常量值。
每次调用 rand()函数获取恒定的随机值时，该 srand()函数使用相同的参数。

> **语法:** srand(种子)
> 
> **参数:**
> **种子:**为整数值。
> 
> **返回:**该函数不返回值。

**例 1:**

```perl
#!/usr/bin/perl

# Calling the srand() function and 
# Printing a random value 
srand(5);
print("The first random number is ", rand(), ".\n");

# Calling the srand() function and 
# Printing a random value 
srand(5);
print("The second random number is ", rand(), ".\n");

# Calling the srand() function and 
# Printing a random value 
srand(5);
print("The third random number is ", rand(), ".\n");

# Calling the srand() function and 
# Printing a random value 
srand(5);
print("The fourth random number is ", rand(), ".\n");
```

 **输出:**

```perl
The first random number is 0.524839579434232.
The second random number is 0.524839579434232.
The third random number is 0.524839579434232.
The fourth random number is 0.524839579434232.

```

**注意:**在上面的代码中，可以看到 srand()函数的参数是相同的，这就是为什么每次调用 rand()函数都会产生相同的随机值。

**例 2:**

```perl
#!/usr/bin/perl

# Calling the srand() function and 
# Printing a random value 
srand(5);
print("The first random number is ", rand(), ".\n");

# Calling the srand() function and 
# Printing a random value 
srand(6);
print("The second random number is ", rand(), ".\n");

# Calling the srand() function and 
# Printing a random value 
srand(7);
print("The third random number is ", rand(), ".\n");

# Calling the srand() function and 
# Printing a random value 
srand(8);
print("The fourth random number is ", rand(), ".\n");
```

**输出:**

```perl
The first random number is 0.524839579434232.
The second random number is 0.395641888099821.
The third random number is 0.266444196765409.
The fourth random number is 0.137246505430998.
```

**注意:**在上面的代码中，可以看到 srand()函数具有不同的参数，这就是为什么每次调用 rand()函数都会产生不同的随机值。

**例 3:**

```perl
#!/usr/bin/perl

# Printing a random value without calling the srand() function
print("The first random number is ", rand(), ".\n");

# Printing a random value without calling the srand() function
print("The second random number is ", rand(), ".\n");

# Printing a random value without calling the srand() function
print("The third random number is ", rand(), ".\n");

# Printing a random value without calling the srand() function
print("The fourth random number is ", rand(), ".\n");
```

**输出:**

```perl
The first random number is 0.241482914266275.
The second random number is 0.821264154368208.
The third random number is 0.870625858233449.
The fourth random number is 0.012084407123389.
```

**注意:**在上面的代码中，可以看到没有使用 srand()函数，这就是为什么每次调用 rand()函数都会产生不同的随机值。