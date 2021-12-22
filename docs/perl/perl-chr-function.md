# Perl | chr()函数

> 原文:[https://www.geeksforgeeks.org/perl-chr-function/](https://www.geeksforgeeks.org/perl-chr-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 chr()函数返回一个代表字符的字符串，该字符的 Unicode 代码点是一个整数。

> **语法:** chr(Num)
> **参数:**
> **Num :** 是返回对应字符的 unicode 整数值。
> **返回:**代表 Unicode 码位为整数的字符的字符串。

**例 1:**

## Perl 语言

```
#!/usr/bin/perl

# Taking some unicode integer value as the parameter
# of the chr() function and returning the corresponding
# characters as output
print chr(71), chr(101), chr(101), chr(107), chr(115);
print "\n";
print chr(102), chr(111), chr(114);
print "\n";
print chr(71), chr(101), chr(101), chr(107), chr(115);
```

**输出:**

```
Geeks
for
Geeks
```

**例 2:**

## Perl 语言

```
#!/usr/bin/perl

# Initialising an array of some unicode integer values
# and retrieving each value and printing their
# corresponding characters
my @Array = (71, 101, 101, 107, 115);
foreach my $element (@Array) {
    print chr($element);
}
```

**输出:**

```
Geeks
```