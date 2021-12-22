# Perl |每个()函数

> 原文:[https://www.geeksforgeeks.org/perl-each-function/](https://www.geeksforgeeks.org/perl-each-function/)

当在列表上下文中调用时，此函数返回一个双元素列表，该列表由哈希的下一个元素的键和值对组成，以便您可以对其进行迭代。而当在标量上下文中调用时，它只返回散列的下一个元素的键。

> **语法:**每个 MY_HASH
> **参数:**
> MY_HASH 作为参数传递给这个函数
> 
> **返回:**
> 列表上下文的 2 元素键值对列表，而标量上下文只有键。

**例 1:**

```
#!/usr/bin/perl

# Initializing a Hash
%hash = (Geeks => 1, of => 2 , Geek => 3);

# each() function
while (($key, $value) = each(%hash))
{

    # Printing(key, value) pair
    print("$key = $value\n");
}
```

**Output:**

```
Geek = 3
of = 2
Geeks = 1

```

**例 2:**

```
#!/usr/bin/perl

# Initializing a Hash
%hash = (Geeks, of, Geek);

# each() function for scalar context
while (($key) = each(%hash))
{

    # Printing(key)
    print("$key ");
}
```

**Output:**

```
Geek Geeks

```