# Perl 中的特殊变量

> 原文:[https://www.geeksforgeeks.org/special-variables-in-perl/](https://www.geeksforgeeks.org/special-variables-in-perl/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的特殊变量是那些已经被定义为在需要时执行特定功能的变量。Perl 中的特殊变量和随机字符的区别因素是变量后面使用了标点符号，可以是 **@** 、 **$** 或 **%** 等，例如 **$_** 。

[Perl 变量](https://www.geeksforgeeks.org/perl-variables/)帮助开发人员节省时间，因为这些通常是英文大命令的快捷方式。

> 注意:最常见的特殊变量是 **$_** ，用于存储默认输入。

查看以下代码，了解这个特殊变量:

```perl
# Providing some input 
while ( <> ) 
{ 
    # Printing the default value 
    # stored in $_
    print lc($_); 
}
```

**这个和**一样

```perl
#!/usr/bin/perl
while ( $abc = <> ) 
{
    print lc($abc);
}
```

下面是工作格式中上述特殊变量的示例:

```perl
#!/usr/bin/perl
foreach ('Mango', 'Orange', 'Apple')
{
   print($_);
   print("\n");
}
```

**Output:**The output of the above code will be:

```perl
Mango
Orange
Apple

```

## 特殊变量的类型

特殊变量可以根据它们的用途和性质进行分类。这些是:

1.  正则表达式特殊变量
2.  文件句柄特殊变量
3.  全局标量特殊变量
4.  全局数组特殊变量
5.  全局散列特殊变量
6.  全局特殊常数
7.  全局特殊文件句柄

### 正则表达式特殊变量

**$ digit:**`**$digit**`的主要功能是将匹配的文本保存在最后一个匹配模式的一组类似的括号中。但是，嵌套块中已经匹配的模式不计算在内。

**{ content } amp；，$MATCH:** 用于查找上次成功模式搜索中匹配的字符串。虽然匹配在隐藏块中或包含在当前集合中，但不计算在内。这是一个只读变量，其作用域是动态的。

```perl
#!/usr/bin/perl

# Declaring local string
local $_ = 'abcdefghi';

# Pattern matching
/def/;

# Printing the matched pattern
print "{content}amp;\n";  
```

**Output:**

```perl
def

```

# **Perl 中的特殊变量**

**，$PREMATCH:** 引用字符串前面的字符串与上次成功的模式匹配相匹配。它不计算任何包含在块或当前块包含的 eval 中的匹配项。

```perl
#!/usr/bin/perl

# Declaring local string
local $_ = 'abcdefghi';

# Pattern matching
/def/;

# Prematching the pattern
print "
Perl 中的特殊变量
:{content}amp;\n";  
```

**Output:**

```perl
abc:def

```