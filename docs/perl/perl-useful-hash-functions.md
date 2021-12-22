# Perl |有用的哈希函数

> 原文:[https://www.geeksforgeeks.org/perl-useful-hash-functions/](https://www.geeksforgeeks.org/perl-useful-hash-functions/)

一个[散列](https://www.geeksforgeeks.org/perl-hash/)是一组键值对。Perl 存储散列的元素，这样它就可以根据关键字搜索值。Perl 提供了各种函数来对哈希值执行操作，例如返回值、从哈希值中删除元素等。
T3】例:

```
#!/usr/bin/perl 

# Initializing hash  
%hash1 = ('Welcome' => 10, 'to' => 20, 'Geeks' => 80);  

# To delete the List passed as parameter 
$deleted_element = delete($hash1{'to'}); 

# Printing elements of Hash  
print "$hash1{'Welcome'}\n";  
print "$hash1{'to'}\n";  
print "$hash1{'Geeks'}\n";  

# Printing the deleted element 
print "Deleted element: $deleted_element"; 
```

**Output:**

```
10

80
Deleted element: 20

```

下面列出了一些在 Perl 中用于散列操作的有用函数:

| 功能 | 描述 |
| **[值()](https://www.geeksforgeeks.org/perl-values-function/)** | 返回存储在哈希中的所有值的列表 |
| **[键()](https://www.geeksforgeeks.org/perl-keys-function/)** | 以列表形式返回 HASH 的所有键 |
| **[各()](https://www.geeksforgeeks.org/perl-each-function/)** | 在标量上下文中调用时，返回由列表上下文中的键和值对以及下一个元素的键组成的双元素列表 |
| **[删除()](https://www.geeksforgeeks.org/perl-delete-function/)** | 用于从哈希中删除指定的键及其关联值，或者在数组的情况下删除指定的元素 |