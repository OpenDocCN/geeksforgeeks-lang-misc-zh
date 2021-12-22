# Perl | LDAP 服务器

> 原文:[https://www.geeksforgeeks.org/perl-ldap-server/](https://www.geeksforgeeks.org/perl-ldap-server/)

**轻量级目录访问协议(LDAP)** 是一种在 TCP/IP 上工作的互联网协议，用于从目录中访问信息。LDAP 协议通常用于访问活动目录。它允许我们保存一个物品目录和关于它们的信息。LDAP 以包含一组属性的记录的形式存储数据。

#### LDAP 服务器

LDAP 分布是 Perl 模块的集合，它为我们提供了一个面向对象的 LDAP 服务器接口。下面给出了 Perl-LDAP 服务器的一些特性:

1.  通过使用 Perl 对象接口，Perl-LDAP 模块提供了一个接口，只需使用少量代码就可以对 LDAP 目录进行复杂的搜索。
2.  所有的 Perl-LDAP 模块都是完全用 Perl 编写的，这使得它的库真正做到了跨平台兼容。
3.  正在积极开发。

使用 LDAP 服务器的四个步骤是连接、身份验证、交互和注销。交互包括搜索、添加、删除和更改记录。为此，我们需要一个负责管理 LDAP 会话的 Perl 模块。

**Net::LDAP** 就是其中之一。它是一个模块集合，允许我们为 Perl 程序实现 LDAP 服务 API。该模块可用于搜索目录和执行维护功能，如添加、删除或修改条目。

要安装**网络::LDAP** 服务器，请使用以下命令:

```
perl -MCPAN -e shell
install Net::LDAP
```

#### 从服务器获取数据

基于 LDAP 的目录服务将信息存储在条目中。每个条目都属于一个或多个对象类，这些对象类指定目录中存储的条目类型。属性是包含条目中数据片段的属性。
基于 LDAP 的目录服务中的每个条目都有一个与之关联的唯一名称。这个“可分辨名称”(DN)由逗号分隔的“相对可分辨名称”(RDN)字符串组成，它们一起指定目录树中条目的位置和名称。相对可分辨名称由一个或多个属性/值对组成，这些属性/值对在目录树中的级别上是唯一的。

> ***注意:**在使用 LDAP 时，我们必须始终搜索或使用扩展操作来获取数据。*

当我们使用搜索方法时，它返回一个包含一组条目(数据)的对象。
搜索方法的基本组成部分是基础和过滤器。基标记正在搜索的树顶，过滤器指示我们感兴趣的记录。
获取条目有 2 种方式:

*   获取整个条目集

## Perl 语言

```
foreach $result ($mesg->all_entries)
{
  # Perform some operation on the data
}
```

*   逐个获取条目

## Perl 语言

```
$num_entries = $mesg->count( ); 
for ($i = 0; $i < $num_entries; $i++)
{ 
  my $entry = $mesg->entry($i);
  # Perform some operation on the data
}
```

***下面给出的是从 LDAP 服务器获取信息并打印出来的基本程序:***

## Perl 语言

```
use strict;
use warnings;
use Net::LDAP; # Package Definition

# Initialization
$ldap = Net::LDAP->new("ldap.example.com") or die $@; 

# Binding
$ldap->bind( ); 

$mesg = $ldap->search(base => $base_dn, 
                       filter => $FILTER); 
$mesg->code( ) && die $mesg->error; 
foreach $result ($mesg->all_entries)
{
  # We can perform any operation on the entries 
  # like adding, removing, modifying the data etc
  print $result->get_value(''), "\n",
} 

$ldap->unbind( );
```

#### 超出管理限制错误

有时，服务器日志中会出现错误，这些错误通常与内部 LDAP 问题有关，从而导致与 LDAP 相关的错误消息。即使这些错误不是致命的，它们也表明需要调查的问题。

*超出管理权限错误*表示已经超出管理权限设置的 LDAP 服务器限制。
假设进行的 LDAP 搜索大于允许的目录服务器的*nsslapd-sizelimit**属性，那么它将不返回全部信息，而是返回部分信息。*

*我们很少有方法可以避免出现这种错误。*

1.  *通过增加*nsslpad-size limit*属性的值。*
2.  *为失败的搜索实施 VL V 指数。*

****示例–***假设我们正在从限制为 50 的大学服务器获取数据。我们寻找一个名叫“托马斯”的姓“谢尔比”的人。它只会给我们带来很少的结果。
但是如果我们搜索“Thomas”而不知道全名，那么我们只搜索“S”。那么该数字可能会超过限制，并显示*“**管理限制超出错误”。**

## *Perl 语言*

```
*use Net::LDAP; # Package Definition

# Initialization
$ldap = Net::LDAP->new("mumbaiuniversity.com") or die $@; 

# Binding
$ldap->bind( ); 

my $result = $ldap->search(  # Searching
    base   => "",
    filter => "(&(cn=Thomas*) (sn=S*))",
);
die $result->error if $result->code;

printf "COUNT: %s\n", $result->count;

$ldap->unbind;*
```