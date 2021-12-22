# Perl | oct()函数

> 原文:[https://www.geeksforgeeks.org/perl-oct-function/](https://www.geeksforgeeks.org/perl-oct-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 oct()函数将传递的八进制值转换为各自的十进制值。例如，oct('1015 ')将返回' 525 '。该函数以字符串的形式返回结果十进制值，该值可以用作数字，因为 Perl 会在数字上下文中将字符串自动转换为数字。如果传递的参数不是八进制数，那么结果将是 0。

> **语法:** oct(oct_value)
> 
> **参数:**
> **oct_value:** 要转换为十进制的八进制数
> 
> **返回:**
> 八进制值转换为十进制值

**例 1:**

```
#!/usr/bin/perl -w

# Converting and printing 
# the decimal value
print("oct(31) ", oct('31'), "\n");
print("oct(50) ", oct('50'), "\n");
```

**Output:**

```
oct(31) 25
oct(50) 40

```

**例 2:**

```
#!/usr/bin/perl -w

# Converting and printing 
# the decimal value
print("oct(106) ", oct('106'), "\n");
print("oct(125) ", oct('125'), "\n");
```

**Output:**

```
oct(106) 70
oct(125) 85

```