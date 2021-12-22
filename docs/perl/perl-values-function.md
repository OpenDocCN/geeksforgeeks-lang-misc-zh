# Perl | values()函数

> 原文:[https://www.geeksforgeeks.org/perl-values-function/](https://www.geeksforgeeks.org/perl-values-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 values()函数返回存储在哈希中的所有值的列表。在标量上下文中，它返回存储在哈希中的元素数量。

**注意:**从 value()函数返回的值可能不总是按照相同的顺序。

> **语法:**哈希值
> 
> **返回:**列表上下文中的值列表和标量上下文中的值数量

**例 1:**

```
#!/usr/bin/perl -w

# Hash containing Keys and values
%sample_hash = ('Geeks' => 'A',
                'for' => 'B',
                'Geek' => 10,
                'World' => 20);

# values() in list context returns 
# values stored in the sample_hash
@values = values(%sample_hash);
print("Values in the Hash are: ", 
       join("-", @values), "\n");

# values() in scalar context returns
# the number of values stored in sample_hash
$values = values( %sample_hash);
print "Number of values in Hash are: $values";
```

**Output:**

```
Values in the Hash are  A-B-10-20
Number of values in Hash are: 4

```

**例 2:**

```
#!/usr/bin/perl -w

# Hash containing Keys and values
%sample_hash = (1 => 'Welcome',
                2 => 'to',
                3 => 'Geeks',
                4 => 'World');

# values() in list context returns 
# values stored in the sample_hash
@values = values( %sample_hash);
print("Values in the Hash are ",
      join("-", @values), "\n");

# values() in scalar context returns
# the number of values stored in sample_hash
$values = values(%sample_hash);
print "Number of values in Hash are: $values";
```

**Output:**

```
Values in the Hash are  Welcome-World-to-Geeks
Number of values in Hash are: 4

```