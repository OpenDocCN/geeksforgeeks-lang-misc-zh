# Perl | reset()函数

> 原文:[https://www.geeksforgeeks.org/perl-reset-function/](https://www.geeksforgeeks.org/perl-reset-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 reset()函数从传递给它的值所指定的字母范围开始，重置(清除)所有包变量。通常，它只在 continue 块内或循环结束时使用。

**注意:**reset()函数的使用仅限于未使用 my()函数定义的变量。

> **语法:**复位(字母 _ 范围)
> 
> **参数:**
> **字母 _ 范围:**以一个普通字符或一组字符开头的一系列字母
> 
> **返回:**
> 1，并重置给定范围内的所有变量

**例 1:**

```
#!/usr/bin/perl -w

$var1 = 20;
$var2 = 15;

# Values before reset() function call
print "var1 value = $var1, ", 
      "var2 value = $var2\n";

# Now reset all variables whose
# name starts with 'v'
reset('v');

# Values after reset() function call
print "var1 value = $var1, ", 
      "var2 value = $var2\n";
```

**Output:**

```
var1 value = 20, var2 value = 15
var1 value = , var2 value =

```

**例 2:**

```
#!/usr/bin/perl -w

$variable1 = 10;
$variable2 = 30;

# defining private variable using my()
my $variable3 = 40;

# Values before reset() function call
print "variable1 value = $variable1, ", 
      " variable2 value = $variable2\n";
print "variable3 value = $variable3\n";

# Now reset all variables whose 
# name starts with 'v'
reset('v');

# Values after reset() function call
print "variable1 value = $variable1, ",
      " variable2 value = $variable2, \n";
print "variable3 value = $variable3";
```

**Output:**

```
variable1 value = 10,  variable2 value = 30
variable3 value = 40
variable1 value = ,  variable2 value = , 
variable3 value = 40

```

在例 2 给出的代码中，变量 3 是使用 **my()** 函数定义的，因此，它的值没有显示 **reset()** 函数的效果，而其他变量的值被重置。