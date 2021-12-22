# 正则表达式

中的 Perl | 'e '修饰符

> 原文:[https://www . geesforgeks . org/perl-e-modifier-in-正则表达式/](https://www.geeksforgeeks.org/perl-e-modifier-in-regular-expression/)

在 Perl 中，正则表达式允许使用合适的运算符对给定的字符串执行各种操作。这些运算符可以执行诸如修改字符串、替换其他子字符串等操作。给定字符串中的子字符串的替换是使用“s”(替换)运算符完成的，该运算符接受两个操作数，一个是要替换的子字符串，另一个是替换字符串。

```
s/To_be_replaced/Replacement/
```

此外，如果需要用替换字符串替换子字符串，该替换字符串是要计算的正则表达式，则使用“***【E】***”修饰符。“e”修饰符放在替换表达式的末尾。

```
s/To_be_replaced/Regular_Expression/e;
```

“e”修饰符也可以与“g”(全局)修饰符一起使用，对给定字符串中所有可能的子字符串进行更改。

**示例 1:** 使用角色类进行替换

```
#!/usr/bin/perl

# Defining the string to be converted
$String = "Geeks for Geeks is the best";
print "Original String: $String\n";

# Converting the string to UPPERCASE
# using 'uc' Function
$String =~ s/(\w+)/uc($1)/ge;
print"Uppercased String: $String\n";

# Converting the string to lowercase
# using 'lc' Function
$String =~ s/(\w+)/lc($1)/ge;
print"Lowercased String: $String\n";
```

**输出:**

```
Original String: Geeks for Geeks is the best
Uppercased String: GEEKS FOR GEEKS IS THE BEST
Lowercased String: geeks for geeks is the best

```