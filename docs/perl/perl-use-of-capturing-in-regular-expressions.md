# Perl–在正则表达式中捕获的使用

> 原文:[https://www . geesforgeks . org/perl-正则表达式中捕获的用法/](https://www.geeksforgeeks.org/perl-use-of-capturing-in-regular-expressions/)

一个[正则表达式](https://www.geeksforgeeks.org/perl-regular-expressions/)或者一个正则表达式是一串定义我们正在查看的模式的字符。它是一个特殊的字符串，描述给定文本中的搜索模式。
[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 允许我们将这些模式的一部分组合成一个子模式，并且还能记住这些子模式匹配的字符串。这种行为被称为**捕获**。

找到字符串中的匹配很重要，这是通过*正则表达式(正则表达式)来完成的。*当我们将这些匹配从字符串中取出进行进一步处理时，它们会更有用。

Perl 通过在任何正则表达式中的数据周围使用括号()来提取匹配的字符串部分，这让我们变得非常容易。Perl 将这些匹配假设为每组捕获括号的特殊变量，即$1、$2、$3。

**示例:**

```perl
use warnings;
use strict;

# Using the localtime() function
# to get the local time
my $time = localtime(); 

print $time, "\n";

# Using regex to capture time data
# Accessing the captured match 
# using the special variable $1
print ("$1 \n") if($time =~ /(\d\d:\d\d:\d\d)/);
```

#### 命名捕获

允许我们通过应用正则表达式来捕获部分匹配并能够在以后使用它们的捕获称为命名捕获。例如:从联系信息中提取电话号码。

编号捕获的基本语法是:

```perl
(?<capture name> …)
```

括号用于括住捕获。那个？< name >构造用于紧跟左括号，并为该特定捕获提供名称。省略的捕获的剩余部分是正则表达式。

当与封闭模式匹配成功时，Perl 会更新神奇的变量“ ***%+*** ”。该哈希包含捕获的名称作为关键字，字符串中与捕获匹配的部分作为哈希值。
命名捕获通常可以提高正则表达式的可维护性。尽管它们在 Perl 中是可能的，但是它们并不经常被使用。它们只在顶级正则表达式中使用。

**示例:**

```perl
# Extracting the parts of string
$_ = "The brown fox jumps over the lazy dog";
/the (\S+)(?{ $color = $^N }) (\S+)(?{ $animal = $^N })/i;

# Printing the matches
print "color = $color, animal = $animal\n"; 
```

**Output:**

```perl
color = brown, animal = fox
```

#### 编号捕获

编号捕获既不提供任何识别名称，也不对%+做任何事情。相反，在 Perl 中，捕获的字符串存储在一系列神奇的变量中。第一个匹配的捕获存储在$1 中，第二个存储在$2 中，依此类推。捕获计数从捕获的左括号开始。从而使第一个左括号捕捉成$1，第二个捕捉成$2，以此类推。

命名捕获的语法比编号捕获的语法更长，而且还提供了额外的清晰度。对于编号捕获，Regex 的可维护性较差。编号捕获在简单的替换中很有用，在这种替换中，命名捕获不需要花费更多的代码。

**示例:**

```perl
# Extracting forename and surname
print "Please enter your name \n "; 
chop ($name = <'Vishal Raina '>);

if ($name =~ /^\s*(\S+)\s+(\S+)\s*$/) 
{
    print "Hi $1\. Your Surname is $2.";
} 
else 
{
    print " Error";
}
print "\n";
```

**Output**

```perl
Please enter your name 
Hi Vishal. Your Surname is Raina.
```