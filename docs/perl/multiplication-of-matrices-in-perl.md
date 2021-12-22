# Perl 中矩阵的乘法

> 原文:[https://www . geesforgeks . org/perl 矩阵乘法/](https://www.geeksforgeeks.org/multiplication-of-matrices-in-perl/)

矩阵是多维数组，以行和列的形式存储数据。 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 允许对这些矩阵执行各种操作，如加法、减法、除法和乘法。Perl 在语法上与 C 非常相似，对于有 C、C++知识的用户来说很容易。

给定两个矩阵，任务是将它们相乘。矩阵可以是正方形或矩形。

**例:**

```
Input : mat1[][] = {{2, 4}, 
                    {3, 4}}
        mat2[][] = {{1, 2}, 
                    {1, 3}}       
Output : {{6, 16}, 
          {7, 18}}
```

首先，用户需要借助[**<【STDIN】>**](https://www.geeksforgeeks.org/perl-use-of-stdin-for-input/)提供两个矩阵的维度。

## Perl

```
print "Enter the Dimensions of matrices: ";
my $a = <STDIN>, my $b = <STDIN>,
my $c = <STDIN>, my $d = <STDIN>;
```