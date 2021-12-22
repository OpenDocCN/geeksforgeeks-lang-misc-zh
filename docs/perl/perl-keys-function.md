# Perl | keys()函数

> 原文:[https://www.geeksforgeeks.org/perl-keys-function/](https://www.geeksforgeeks.org/perl-keys-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 keys()函数以列表的形式返回 HASH 的所有键。列表中元素的顺序不必总是相同的，但是它与值和每个函数返回的顺序相匹配。

> **语法:**键(HASH)
> 
> **参数:**
> HASH:要打印其密钥的 HASH
> 
> **返回:**对于标量上下文，它返回散列中的键的数量，而对于列表上下文，它返回键的列表。

**例 1:**

```perl
#!/usr/bin/perl

%hash = ('Ten' => 10,
         'Eleven' => 11,
         'Twelve' => 12,
         'Thirteen' => 13);

@values = values( %hash );
print("Values are  ", join("-", @values), "\n");

@keys = keys( %hash );
print("Keys are ", join("-", @keys), "\n");
```

**输出:**

```perl
Values are  11-12-13-10
Keys are Eleven-Twelve-Thirteen-Ten
```

**例 2:**

```perl
#!/usr/bin/perl

%hash = ('Geek' => 1,
         'For' => 2,
         'Geeks' => 3);

@values = values( %hash );
print("Values are  ", join("-", @values), "\n");

@keys = keys( %hash );
print("Keys are ", join("-", @keys), "\n");
```

**输出:**

```perl
Values are  3-2-1
Keys are Geeks-For-Geek

```