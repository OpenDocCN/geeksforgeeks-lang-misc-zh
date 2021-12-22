# Perl | q 运算符

> 原文:[https://www.geeksforgeeks.org/perl-q-operator/](https://www.geeksforgeeks.org/perl-q-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 q 运算符可以用来代替单引号。它使用一组圆括号将字符串括起来。

> **语法:** q(字符串)
> 
> **返回:**单引号字符串。

**注意:**可以使用任何一组分隔符，而不仅仅是括号。

**例 1:**

```
#!/usr/bin/perl -w

# Passing string to q operator
print(q(Geeks For Geeks));
```

**Output:**

```
Geeks For Geeks

```

**例 2:**

```
#!/usr/bin/perl -w

# Defining an Integer variable
$var = 25;

# Passing string and variable to 
# the q operator 
print(q(Welcome to GFG, $var));
```

**输出:**

```
Welcome to GFG, $var

```