# Perl 中的强制

> 原文:[https://www.geeksforgeeks.org/coercions-in-perl/](https://www.geeksforgeeks.org/coercions-in-perl/)

在 [Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 中，有不同类型的值，比如字符串、整数、有理数等等。强制负责将一种数据类型的数据或对象转换为另一种数据类型或对象，在幕后，我们神奇地得到了我们想要的东西。它通常指“隐式类型转换”，这也是将一种数据类型的实体转换为另一种数据类型的方法之一。

最常见的强制形式是*重载 pragma* ，以及它在 Perl 编程中的字符串重载。在这种情况下，我们的对象被自动强制转换成一个字符串(在 Perl 本身中)。
高阶强制的强制类型是*参数::强制*，主要用于子程序和方法参数。

#### 胁迫的类型

胁迫的类型解释如下:

*   **Boolean Coercion:** Boolean coercion is useful to test the truthiness of value just like in an if or while condition. All the numeric 0, undef, the empty string, and the string ‘0’ evaluate as false values. All the other values including strings which are numerically equal to zero (like ‘0.0’, ‘0e’ and ‘0 but true’)- evaluate as true values.
    When a scalar consists of both string and numeric components, Perl preferably checks the string component for Boolean truth. ‘0 but true’ evaluates to zero numerically, but is not an empty string, hence it gets evaluated as a true value in a Boolean context.

    **示例:**

    ```
    say ?^True; # Falsesay ?^'';   # Truesay ?^0;    # Truesay ?^42;   # False
    ```

    (那个？前缀运算符是布尔强制运算符。它将其操作数转换为布尔值。)

*   **String Coercion:** String coercion comes into action when we use string operators like comparisons (eq and cmp), concatenation, split, substr, and regular expressions, and also while using a value or an expression as a hash key. The undefined value is then stringified to an empty string but produces a “use of uninitialized value” warning. Numbers stringify to string which contains their values. (stringify = to return a string)

    **示例:**

    ```
    use strict;
    use warnings;
    my $x = "4T"; # string
    my $y = 3;    # integer
    my $z = $x.$y;
    print $z;     # coerced
    ```

    **Output:**

    ```
    4T3
    ```

*   **Numeric Coercion:** Numeric coercion occurs when we use a numeric comparison operator such as == and <=>, while performing mathematical operations or while using an expression or a value as an array or list index. The undefined value then numifies to zero and gives us a “Use of uninitialized value” warning. The strings which do not start with any numeric portion numify to zero and give us a warning of “Argument isn’t numeric”. And the ones which begin with character allowed in numeric literals numify to the values specified and produce no warning. *(numify = to return a number).*
    There’s also a function in Perl function which uses the same parsing rules as the Perl grammar to extract a number from a string that is *looks_like_number()* which is included in the core module *Scalar::Util.*

    **示例:**

    ```
    my $a = "23B";
    $a +=0;

    # string part has been removed automatically.
    print $a; 
    ```

    **Output:**

    ```
    23
    ```

*   **Reference Coercion:** When we use a dereferencing operation on a non-reference, it turns a value into a reference. This process is known as Autovivification. This process comes handy while manipulating nested data structures.
    **Example:**

    ```
    my %users;
    $users{John}{id} = 128;
    $users{Thomas}{id} = 129;
    ```

    **解释:**正如我们在这里看到的，散列不包含约翰和托马斯的值，但是 Perl 为他们创建了散列引用，为他们每个人分配了一个以 id 为键的键/值对。

*   **缓存的强制:**Perl 中值的内部表示同时存储字符串和数值。就像当我们用字符串表示一个值时，它不会替换数值，而是将一个用字符串表示的值添加到内部表示中，该内部表示稍后由两个组件组成。类似地，当我们对一个字符串值进行 numify 时，它会填充数值并保持字符串组件不变。
    *例如:*某些 Perl 运算符通常更喜欢使用一个值而不是另一个值(就像布尔检查更喜欢字符串一样)。如果有一个值以我们不期望的形式缓存了表示，那么依赖隐式转换可能会产生一些令人惊讶的结果。了解这是如何发生的可能有助于我们诊断一些奇怪的情况。

#### 对偶变量

Perl 具有多组件特性，用户可以用 dualvars 的形式使用。函数 dualvar()是由核心模块 Scalar :: Util 提供的，它允许我们绕过 Perl 强制，单独操作一个值的字符串和数字部分。

```
use Scalar::Util qw(blessed dualvar set_prototype);
$foo = dualvar 10, "Geeksfor";
$num = $foo + 2;                   
$str = $foo . " Geeks";             
print "$num\n";
print $str;
```

**Output:**

```
12
Geeksfor Geeks
```