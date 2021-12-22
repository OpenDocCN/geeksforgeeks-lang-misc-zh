# Perl |我的关键词

> 原文:[https://www.geeksforgeeks.org/perl-my-keyword/](https://www.geeksforgeeks.org/perl-my-keyword/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 my 关键字声明列出的变量是定义它的封闭块的本地变量。我的目的是定义[静态范围](https://www.geeksforgeeks.org/static-and-dynamic-scoping/)。这可用于多次使用相同的变量名，但使用不同的值。

**注意:**要在我的关键字下指定多个变量，需要使用括号。

> **语法:**我的变量
> 
> **参数:**
> **变量:**定义为局部
> 
> **返回:**
> 不返回任何值。

**例 1:**

```
#!/usr/bin/perl -w

# Local variable outside of subroutine
my $string = "Geeks for Geeks";
print "$string\n";

# Subroutine call
my_func();
print "$string\n";

# defining subroutine 
sub my_func
{
    # Local variable inside the subroutine
    my $string = "This is in Function";
    print "$string\n";
    mysub();
}

# defining subroutine to show
# the local effect of my keyword
sub mysub 
{
    print "$string\n";
}
```

**输出:**

```
Geeks for Geeks
This is in Function
Geeks for Geeks
Geeks for Geeks
```

**例 2:**

```
#!/usr/bin/perl -w

# Local variable outside of subroutine
my $string = "Welcome to Geeks";
print "$string\n";

# Subroutine call
my_func();
print "$string\n";

# defining subroutine 
sub my_func
{
    # Local variable inside the subroutine
    my $string = "Let's GO Geeky!!!";
    print "$string\n";
    mysub();
}

# defining subroutine to show
# the local effect of my keyword
sub mysub 
{
    print "$string\n";
}
```

**输出:**

```
Welcome to Geeks
Let's GO Geeky!!!
Welcome to Geeks
Welcome to Geeks
```

 **如何定义动态范围？**T3“我的”的反义词是“本地”。local 关键字定义动态范围。

```
# A perl code to demonstrate dynamic scoping 
$x = 10; 
sub f 
{ 
   return $x; 
} 
sub g 
{ 
   # Since local is used, x uses   
   # dynamic scoping. 
   local $x = 20; 

   return f(); 
} 

print g()."\n"; 
```