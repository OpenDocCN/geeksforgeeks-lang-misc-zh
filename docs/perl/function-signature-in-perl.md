# Perl 中的函数签名

> 原文:[https://www.geeksforgeeks.org/function-signature-in-perl/](https://www.geeksforgeeks.org/function-signature-in-perl/)

一个 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 函数或[子程序](https://www.geeksforgeeks.org/perl-subroutines-or-functions/)是一组共同执行特定任务的语句。在每种编程语言中，用户都希望重用代码。因此，用户将这段代码放在函数或子例程中，这样就不需要反复编写代码。在 Perl 中，函数、子例程和方法这些术语是相同的，但是在某些编程语言中，它们被认为是不同的。子程序这个词在 Perl 编程中使用最多，因为它是使用关键字 sub 创建的。每当有对函数的调用时，Perl 都会停止执行它的所有程序，并跳转到函数来执行它，然后返回到它之前运行的代码部分。可以避免使用 return 语句。

**定义子程序:**在 Perl 中定义子程序的一般形式如下-

```
sub subroutine_name
{
    # body of method or subroutine
}

```

**函数签名:**定义函数时，括号内还定义了一组参数，以定义它将在函数调用中接收的参数类型。这个函数签名可以包含一个参数或一个参数列表。定义了签名的子例程或函数只能接收子例程中定义的类型的参数。如果传递给子例程的参数与其签名不同，将会产生错误。
函数签名讲述了很多关于子程序类型的信息。它使用户能够使用不同的签名(即不同的参数)创建同名的不同子程序。在 Perl 中，不同子程序的子程序名可以相同，但它们的参数必须不同。
**例:**

```
sub example_func($variable)
{
    statement;
}

sub example_func($variable1, $variable2)
{
    statement;
}
```

在上面的例子中，子例程的名称是相同的，但是它们的参数计数是不同的，因此，它们不会被认为是不同的子例程，并且您的 Perl 代码不会产生任何错误。

**传递与签名不同类型的参数:**当用签名定义函数时，该子例程必须接受与其签名相同类型的参数。如果传递了函数签名以外的参数，那么它将生成一个错误，导致代码编译失败。
T3】例:

```
#!/usr/bin/perl

# Defining Function Signature
sub example(Int $variable)
{
    return $variable / 2;
}

# Function Call
print example(44);
```

**输出:**

```
22
```

如果我们传递一个不是函数签名的类型的参数，那么它将产生如下所示的错误:

```
#!/usr/bin/perl

# Defining Function Signature
sub example(Int $variable)
{
    return $variable / 2;
}

# Function Call with 
# string type parameter
print example("44");
```

> 编译 prog.pl 时出错
> 调用示例(Str)将永远无法使用 prog.pl:7 中声明的签名(Int $variable)

**参数数量的差异:**
定义函数签名时，它还保存可以传递给它的参数数量以及参数类型。如果我们用不同数量的参数调用函数，那么它将导致一个错误，因为 Perl 对不同签名的函数有不同的含义。
**例:**

```
#!/usr/bin/perl

# Defining Function Signature
sub example(Int $variable)
{
    return $variable / 2;
}

# Function Call with 
# two arguments
print example(44, 29);
```

**输出:**

> 编译 prog.pl
> 时出错调用示例(Int，Int)将永远无法使用 prog.pl:10 中声明的签名(Int $variable)

函数签名是一个有用的方面，但是它有时对一些程序员来说变得非常烦人，因为定义函数签名将函数的使用限制在特定类型的参数上。如果定义的函数没有签名，那么可以传递给它的参数类型就没有限制。
**例:**

```
#!/usr/bin/perl

# Defining Function Signature
sub example($variable)
{
    return $variable / 2;
}

# Function Call with Integer argument
# written as a string type
print example("44");
```

**输出:**

```
22
```

在上面的代码中，一个函数被声明为没有这种特定的参数类型，因此当一个整数值作为字符串传递给它时，它会自动将参数转换为整数形式并给出结果。但是，如果我们使用字符串参数调用函数，并且要对其执行的操作需要整数值，那么它将导致如下所示的错误:

```
#!/usr/bin/perl

# Defining Function Signature
sub example($variable)
{
    return $variable / 2;
}

# Function Call with 
# string type argument
print example("Geeks");
```

**输出:**

> 无法将字符串转换为数字:以 10 为基数的数字必须以有效数字或“.”开头在 prog.pl 线路 4 的子示例中
> 在 prog.pl 线路 11 的块<unit>中</unit>
> 
> 实际上被扔向:
> 在 prog.pl 线路 4 的子示例中
> 在 prog.pl 线路 11 的块<unit>中</unit>