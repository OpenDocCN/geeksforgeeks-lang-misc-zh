# Perl | qq 操作符

> 原文:[https://www.geeksforgeeks.org/perl-qq-operator/](https://www.geeksforgeeks.org/perl-qq-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 qq()运算符可以用来代替双引号。它使用一组圆括号将字符串括起来。

> **语法:** qq(字符串)
> 
> **返回:**
> 一个双引号字符串

**注意:**任何一组分隔符都可以用来代替括号。

**例 1:**

```
#!/usr/bin/perl -w

# Passing string to qq operator
print(qq(Welcome to GeeksForGeeks));
```

**输出:**

```
Welcome to GeeksForGeeks
```

**例 2:**

```
#!/usr/bin/perl -w

# Defining an Integer variable
$var = 15;

# Passing string and variable to
# the qq operator
print(qq(GeeksforGeeks, $var));
```

**输出:**

```
GeeksforGeeks, 15
```