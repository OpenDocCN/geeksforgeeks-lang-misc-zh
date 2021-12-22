# Perl | wantarray()函数

> 原文:[https://www.geeksforgeeks.org/perl-wantarray-function/](https://www.geeksforgeeks.org/perl-wantarray-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 wantarray()函数，如果当前执行的子程序期望返回一个列表值，则返回 True，如果正在寻找标量值，则返回 false。

> **语法:** wantarray()
> 
> **返回:**列表值为真，标量值为假

**例 1:**

```
#!/usr/bin/perl -w

# Subroutine to call wantarray() function
sub geeks
{
    return(wantarray() ? ("Geeks", "For", "Geeks") : 1);
}

# Calling the subroutine 
# in scalar and array context
$value = geeks();
@value = geeks();

# Printing the values in both contexts
print("Value in Scalar context: $value\n");
print("Value in List Context: @value");
```

**Output:**

```
Value in Scalar context: 1
Value in List Context: Geeks For Geeks

```

**例 2:**

```
#!/usr/bin/perl -w

# Subroutine to call wantarray() function
sub geeks
{
    if(wantarray())
    {
        # Addition of two numbers when 
        # wantarray() function is called
        # in list context
        $c = $a + $b; 
    }
    else
    {
        # When wantarray() is called 
        # in Scalar context
        return 1;
    }
}

# Driver Code
$a = 10; $b = 20; $c = 0;

# Calling Subroutine in scalar and list contexts
$value = geeks($a, $b);
@value = geeks($a, $b);

# Printing values in both the contexts
print("Value when called in Scalar context: $value\n");
print("Value when called in List Context: @value");
```

**Output:**

```
Value when called in Scalar context: 1
Value when called in List Context: 30

```