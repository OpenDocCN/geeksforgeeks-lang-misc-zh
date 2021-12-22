# Perl |参考文献中的自动生动化

> 原文:[https://www . geesforgeks . org/perl-auto vivitation-in-references/](https://www.geeksforgeeks.org/perl-autovivification-in-references/)

Perl [引用](https://www.geeksforgeeks.org/perl-references/)是访问相同数据但使用不同变量的一种方式。Perl 中的引用是一种标量数据类型，它保存另一个变量的位置。另一个变量可以是标量、散列、数组、函数名等。嵌套数据结构可以很容易地创建，因为用户可以创建一个包含对另一个列表的引用的列表，该列表可以进一步包含对数组、标量或散列等的引用。
引用用于创建复杂的数据结构，如数组的数组、哈希的哈希、数组的哈希等等。因此，程序员必须对保存该值的每个引用进行引用。

**自动生动化**是一个特性，其中如果对散列或数组中未定义的值进行引用，Perl 会自动为其创建一个引用值。
自动生动化帮助程序员编写一个完整的变量结构并使用它，而不是提前显式声明变量。它还使代码可读。

**注意:**如果一个包含 undef 的变量被取消引用，就好像它是一个散列引用一样，则会插入一个对空匿名散列的引用。

**语法:**

> **$ variable = {
> input 1 =>T2】{
> input 2 =>' value '
> }
> }；**

**例 1:**

```perl
#!/usr/bin/perl
use warnings;
use strict;

my $test->{fullName}->{lastName} = "Bong";

print $test, "\n"; # HASH(0x169af30)
print $test->{fullName},, "\n"; # HASH(0x16b9e48)
print $test->{fullName}->{lastName}, "\n"; # Bong
```

**输出:**

```perl
HASH(0x169af30)
HASH(0x16b9e48)
Bong
```

**例 2:**

```perl
#!/usr/bin/perl
use warnings;
use strict;

my $anime->{manga}->{artist} = "One Piece";

print $anime, "\n"; # HASH(0x2405f30)
print $anime->{manga},, "\n"; # HASH(0x2424e48)
print $anime->{manga}->{artist}, "\n"; # One Piece
```

**输出:**

```perl
HASH(0x2405f30)
HASH(0x2424e48)
One Piece
```