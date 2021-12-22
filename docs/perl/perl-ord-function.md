# Perl | order()函数

> 原文:[https://www.geeksforgeeks.org/perl-ord-function/](https://www.geeksforgeeks.org/perl-ord-function/)

order()函数是 Perl中的一个内置函数，它返回字符串第一个字符的 ASCII 值。该函数将字符串作为参数，并返回该字符串第一个字符的 ASCII 值。

> **语法:**顺序字符串
> 
> **参数:**
> 这个函数接受一个参数‘字符串’，从中我们可以得到一个 ASCII 值。
> 
> **返回:**
> 一个整数值，代表作为参数传递给该函数的字符串中第一个字符的 ASCII 值。

**示例:**

```
Input: Geeksforgeeks
Output: 71
Explanation: The ASCII value of G is 71

Input: WelcometoGFG
Output: 87
Explanation: The ASCII value of W is 87
```

下面的程序说明了 order()函数在 Perl 中的使用:

**程序 1:**

```
#!/usr/bin/perl -w

# ASCII value of 'G' is printed
print(ord('GeeksforGeeks'));
```

**Output:**

```
71

```

**程序 2:**

```
#!/usr/bin/perl -w

# ASCII value of 'W' is printed
print(ord('WelcometoGFG'));
```

**Output:**

```
87

```