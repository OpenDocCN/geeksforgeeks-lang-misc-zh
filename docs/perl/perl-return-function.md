# Perl | return()函数

> 原文:[https://www.geeksforgeeks.org/perl-return-function/](https://www.geeksforgeeks.org/perl-return-function/)

Perl 中的 return()函数在子程序、块或 do 函数的末尾返回 Value。根据所选上下文，返回值可能是标量、数组或哈希。

> **语法:**返回值
> 
> **返回:**
> 标量上下文中的列表

**注意:**如果没有值被传递给返回函数，那么它在列表上下文中返回一个空列表，在标量上下文中不返回任何值，在 void 上下文中不返回任何值。

**例 1:**

```perl
#!/usr/bin/perl -w

# Subroutine for Multiplication
sub Mul($) 
{
    my($a, $b ) = @_;  
    my $c = $a * $b;

    # Return Value    
    return($a, $b, $c);
}

# Calling in Scalar context
$retval = Mul(25, 10);
print ("Return value is $retval\n" );

# Calling in list context
@retval = Mul(25, 10);
print ("Return value is @retval\n" );
```

**Output:**

```perl
Return value is 250
Return value is 25 10 250

```

**例 2:**

```perl
#!/usr/bin/perl -w

# Subroutine for Subtraction
sub Sub($) 
{
    my($a, $b ) = @_; 

    my $c = $a - $b;

    # Return Value    
    return($a, $b, $c);
}

# Calling in Scalar context
$retval = Sub(25, 10);
print ("Return value is $retval\n" );

# Calling in list context
@retval = Sub(25, 10);
print ("Return value is @retval\n" );
```

**Output:**

```perl
Return value is 15
Return value is 25 10 15

```