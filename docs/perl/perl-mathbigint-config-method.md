# Perl | Math::BigInt->config()方法

> 原文:[https://www . geesforgeks . org/perl-mathbigint-config-method/](https://www.geeksforgeeks.org/perl-mathbigint-config-method/)

`**Math::BigInt**`Perl 中的模块提供了用任意精度和重载算术运算符表示整数的对象。

**config()** 方法中的 **`Math::BigInt`** 模块用来获取关于 Perl 模块的配置信息。

> **语法:**数学:BigInt- >配置()
> 
> **参数:**无
> 
> **返回:**包含配置的散列，例如类名、版本号、库等。

**例 1:**

```
#!/usr/bin/perl 

# Import Data Dumper Module
use Data::Dumper;

# Import Math::BigInt module 
use Math::BigInt; 

print Dumper(Math::BigInt->config());

print Math::BigInt->config()->{version}, "\n";
```

**Output:**

```
$VAR1 = {
          'precision' => undef,
          'upgrade' => undef,
          'accuracy' => undef,
          'div_scale' => 40,
          'trap_nan' => 0,
          'lib_version' => '1.9997',
          'trap_inf' => 0,
          'version' => '1.9997',
          'round_mode' => 'even',
          'lib' => 'Math::BigInt::Calc',
          'class' => 'Math::BigInt',
          'downgrade' => undef
        };
1.9997

```

**例 2:**

```
#!/usr/bin/perl 

# Import Data Dumper Module
use Data::Dumper;

# Import Math::BigInt module 
use Math::BigInt; 

print Dumper(Math::BigInt->config());

print Math::BigInt->config()->{lib}, "\n";
```

**Output:**

```
$VAR1 = {
          'lib' => 'Math::BigInt::Calc',
          'class' => 'Math::BigInt',
          'accuracy' => undef,
          'upgrade' => undef,
          'round_mode' => 'even',
          'div_scale' => 40,
          'trap_nan' => 0,
          'lib_version' => '1.9997',
          'version' => '1.9997',
          'precision' => undef,
          'trap_inf' => 0,
          'downgrade' => undef
        };
Math::BigInt::Calc

```