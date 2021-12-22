# Perl |下一个运算符

> 原文:[https://www.geeksforgeeks.org/perl-next-operator/](https://www.geeksforgeeks.org/perl-next-operator/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中的 next 运算符跳过当前的循环执行，将迭代器转移到 next 指定的值。如果程序中指定了一个标签，那么执行将跳到标签标识的下一个迭代。

> **语法:**下一个标签

**例 1:**

```
#!/usr/bin/perl -w

# Perl Program to find the frequency
# of an element

@Array = ('G', 'E', 'E', 'K', 'S');
$c = 0;
foreach $key (@Array)
{
    if($key eq 'E') 
    {
        $c = $c + 1;    
    }
    next;
}

print "Frequency of E in the Array: $c";
```

**Output:**

```
Frequency of E in the Array: 2

```

**例 2:**

```
#!/usr/bin/perl
$i = 0;

# label for outer loop
outer:
while ( $i < 3 ) {

    $j = 0;
    while ( $j < 3 ) {

        # Printing values of i and j
        print "i =  $i and j =  $j\n";

        # Skipping the loop if i==j
        if ( $j == $i ) {

            $i = $i + 1;
            print "As i == j, hence going back to outer loop\n\n";

            # Using next to skip the iteration
            next outer;
        }
        $j = $j + 1;
    }

    $i = $i + 1;

}# end of outer loop
```

**Output:**

```
i =  0 and j =  0
As i == j, hence going back to outer loop

i =  1 and j =  0
i =  1 and j =  1
As i == j, hence going back to outer loop

i =  2 and j =  0
i =  2 and j =  1
i =  2 and j =  2
As i == j, hence going back to outer loop

```