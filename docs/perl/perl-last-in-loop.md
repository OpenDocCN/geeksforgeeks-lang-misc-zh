# Perl |循环中的最后一个

> 原文:[https://www.geeksforgeeks.org/perl-last-in-loop/](https://www.geeksforgeeks.org/perl-last-in-loop/)

last 关键字用于循环控制语句，该语句会立即导致循环的当前迭代成为最后一次迭代。如果给定了一个标签，那么它就由标签循环而来。

> **语法:**
> #从当前循环中出来。
> 最后
> 
> #从
> #我的标签
> 最后一个我的标签指定的循环中出来

**例 1:**

```
#!/usr/bin/perl
$sum = 0;
$a = 0;
$b = 0;

while(1) 
{

$sum = $a + $b;
$a = $a + 2;

# Condition to end the loop
if($sum > 10) 
{
    print "Sum = $sum\n";
    print "Exiting the loop\n";
    last;
} 
else
{
    $b = $b - 1;
}
}
print "Loop ended at Sum > 10\n";
```

**输出:**

```
Sum = 11
Exiting the loop
Loop ended at Sum > 10

```

**例 2:**

```
#!/usr/local/bin/perl

$a = 1;
$sum = 0;

# Outer Loop
Label1: while($a < 16) 
{
   $b = 1;

   # Inner Loop
   Label2: while ($b < 8)
   {
      $sum = $sum + $b;
      if($a == 8) 
      {
         print "Sum is $sum";

         # terminate outer loop
         last Label1;
      }
      $b = $b * 2;
   }
   $a = $a * 2;
}
```

**输出:**

```
Sum is 22
```