# Perl | prototype()函数

> 原文:[https://www.geeksforgeeks.org/perl-prototype-function/](https://www.geeksforgeeks.org/perl-prototype-function/)

**prototype()** 函数在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中返回一个字符串，该字符串包含函数的原型或作为参数传递给它的引用，如果函数没有原型，则返回 undef。

> **语法:**原型(function_name)
> 
> **参数:**
> **函数 _ 名称:**原型待定的函数
> 
> **返回:**
> 传递的函数原型，如果没有原型，则取消定义

**例 1:**

```
#!/usr/bin/perl -w

$prototype_func = prototype ( "GFG" );
print "Prototype of GFG function ", 
            "is $prototype_func\n";

sub GFG(**) 
{
    print "Just a statement\n";
}
```

**Output:**

```
Prototype of GFG function is **

```

**例 2:**

```
#!/usr/bin/perl -w

$prototype_func = prototype ( "GFG" );
print "Prototype of GFG function ", 
            "is $prototype_func\n";

sub GFG($) 
{
    print "Just a statement\n";
}
```

**Output:**

```
Prototype of GFG function is $

```