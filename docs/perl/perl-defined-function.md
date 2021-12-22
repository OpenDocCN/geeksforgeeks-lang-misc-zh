# Perl | defined()函数

> 原文:[https://www.geeksforgeeks.org/perl-defined-function/](https://www.geeksforgeeks.org/perl-defined-function/)

如果所提供的变量“VAR”的值不是未定义的值，则 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 **Defined()** 返回 true，或者如果未指定 VAR，则检查$_ 的值。这可以与许多功能一起使用来检测操作失败，因为如果出现问题，它们会返回 undef。

如果 VAR 是一个函数或函数的引用，那么如果函数已经被定义，它将返回 true，否则如果函数不存在，它将返回 false。如果指定了哈希元素，如果定义了相应的值，它将返回 true，但不会检查哈希中是否存在该键

> **语法:**已定义(VAR)
> 
> **参数:**
> 待查 VAR
> 
> **返回:**
> 如果 VAR 未定义则返回 0，如果 VAR 包含值则返回 1

**例 1:**

```
#!/usr/bin/perl

# Defining a variable
$X = "X is defined";

# Checking for existence of $X 
# with defined() function
if(defined($X)) 
{
    print "$X\n";
}

# Checking for existence of $Y 
# with defined() function
if(defined($Y)) 
{
    print "Y is also defined\n";
} 
else
{
    print "Y is not defined\n";
}
```

**输出:**

```
X is defined
Y is not defined
```

**例 2:**

```
#!/usr/bin/perl

# Defining a function
sub X
{

    # Defining a variable
    $VAR = 20;
}

# Checking for existence of $X 
# with defined() function
if(defined(X)) 
{
    print "Function Exists\n";
}

# Checking for existence of $Y 
# with defined() function
if(defined($Y)) 
{
    print "Y is also defined\n";
} 
else
{
    print "Y is not defined\n";
}
```

**输出:**

```
Function Exists
Y is not defined

```