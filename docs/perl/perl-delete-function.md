# Perl | delete()函数

> 原文:[https://www.geeksforgeeks.org/perl-delete-function/](https://www.geeksforgeeks.org/perl-delete-function/)

**Delete()** 在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中用于从散列中删除指定的键及其关联值，或者在数组的情况下删除指定的元素。此操作仅适用于单个元素或切片。

> **语法:**删除(列表)
> 
> **参数:**
> 待删除列表
> 
> **如果密钥不存在，则返回:**
> unde，否则返回与删除的密钥相关联的值

**示例 1:** 在哈希上实现 delete()

```perl
#!/usr/bin/perl

# Initializing hash 
%hash1 = ('Geeks' => 45, 'for' => 30, 'Now' => 40); 

# To delete the List passed as parameter
$deleted_element = delete($hash1{'for'});

# Printing elements of Hash 
print "$hash1{'Geeks'}\n"; 
print "$hash1{'for'}\n"; 
print "$hash1{'Now'}\n"; 

# Printing the deleted element
print "Deleted element: $deleted_element";
```

**输出:**

```perl
45

40
Deleted element: 30
```

**示例 2:** 在数组上实现 delete()

```perl
#!/usr/bin/perl

# Initializing array
@array1 = (10, 20, 30, 40, 50, 60); 

# To delete the array element at index 2
$deleted_element = delete(@array1[2]);

# Printing elements of Array 
print "Updated Array: @array1";

# Printing the deleted element
print "\nDeleted element: $deleted_element";
```

**输出:**

```perl
Updated Array: 10 20  40 50 60
Deleted element: 30
```