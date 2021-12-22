# perl |‘ee’修饰为 Regex

> 哎哎哎:# t0]https://www . geeksforgeeks . org/perl-ee-in-regex/修改程序

在 Perl 中，正则表达式允许使用合适的运算符对给定的字符串执行各种操作。这些运算符可以执行诸如修改字符串、替换其他子字符串等操作。给定字符串中的子字符串的替换是使用“s”(替换)运算符完成的，该运算符接受两个操作数，一个是要替换的子字符串，另一个是替换字符串。

```perl
s/To_be_replaced/Replacement/
```

Perl 中的修饰符用于使用正则表达式来匹配具有特定模式的字符串。Perl 中的“ee”修饰符类似于“\e”修饰符。它用于评估右侧的字符串，然后进一步评估结果。它基本上是 Perl 中的双“eval”运算符。“e”运算符用于计算右侧的字符串。“ee”是它的下一步。它对已经应用了“\e”的字符串应用“\e”运算符。

```perl
 s///ee;
```

就像“e”修饰符一样，“ee”修饰符也可以与“g”(全局)修饰符一起使用，对给定字符串中所有可能的子字符串进行更改。

**例:**

```perl
#!/usr/bin/perl
my $var = 'for';

# Defining the string 
my $String = 'Geeks $var Geeks is the best';

# String before using 'ee' modifier
print "Original String: $String\n";

# Applying 'ee' modifier using regex
$String =~ s/(\$\w+)/$1/ee;
print "Updated String: $String";
```

**输出:**

```perl
Original String: Geeks $var Geeks is the best
Updated String: Geeks for Geeks is the best

```