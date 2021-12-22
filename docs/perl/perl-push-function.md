# Perl | push()函数

> 原文:[https://www.geeksforgeeks.org/perl-push-function/](https://www.geeksforgeeks.org/perl-push-function/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 push()函数用于将一个值列表推送到数组的末尾。push()函数经常与 pop 一起使用来实现堆栈。push()函数不依赖于作为列表传递的值的类型。这些值可以是字母数字。

> **语法:**推送(数组、列表)
> 
> **参数:**
> **数组:**其中要添加值列表
> **列表:**使用推送功能添加
> 
> **返回:**
> 新数组中元素的个数。

**例 1:**

```perl
#!/usr/bin/perl -w

# Original Array
@array = ( 10, 20, 30 );

# Printing Array elements
print "Original Array: @array \n";

# Calling push function to 
# add a list of elements
push(@array, (35, 40, 55));

# Printing Updated array elements
print "Updated Array: @array \n";
```

**输出:**

```perl
Original Array: 10 20 30 
Updated Array: 10 20 30 35 40 55 

```

**例 2:**

```perl
#!/usr/bin/perl -w

# Original Array
@array = ( 10, A, 30 );

# Printing Array elements
print "Original Array: @array \n";

# Calling push function to 
# add a list of elements
push(@array, (F, G, H));

# Printing Updated array elements
print "Updated Array: @array \n";
```

**输出:**

```perl
Original Array: 10 A 30 
Updated Array: 10 A 30 F G H 

```