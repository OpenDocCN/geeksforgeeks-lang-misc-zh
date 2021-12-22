# Perl 编程中的纯旧文本文档

> 原文:[https://www . geesforgeks . org/plain-old-text-documentation-in-perl-programming/](https://www.geeksforgeeks.org/plain-old-text-documentation-in-perl-programming/)

POD 是一种标记语言，用于为 Perl、Perl 程序和 Perl 模块编写文档。使用起来很简单。

有各种翻译器可用于将 Pod 转换为不同的格式，如纯文本、HTML、手册页等。Pod 标记由三种段落组成:

*   **普通段落:**对于粗体、斜体、代码样式、超链接等使用普通图形中的格式化代码
*   **逐字段落:**不需要任何特殊解析或格式化的代码块或其他文本使用实现，这些也不应该包装。
*   **命令段落**:命令段落用于文本块，通常用作标题或列表的一部分。命令段落以=开头，后跟标识符和任意文本

要在 Perl 模块和脚本中嵌入 Pod(纯文本)文档，请使用以下规则在 Perl 代码中使用嵌入的文档:

*   用一个空行开始你的文档
*   在开头放置一个**'**=**head 1′**命令
*   在末端放置 **'** = **切'**命令

> ***注意:*** Perl 将忽略您在代码中输入的 Pod(纯旧文本)文本

**示例:**

```
=head1 SYNOPSIS
 [GEEKSFORGEEKS].
=cut

```

下面提到的是一个在 Perl 代码中使用嵌入式文档的简单例子

```
#!/usr/bin/perl

print "Hello, World\n";

=head1 Hello, World Example
This example demonstrate very basic syntax of Perl.
=cut

print "Hello, geeksforgeeks\n"
```

**输出:**

```
Hello, World
Hello, geeksforgeeks
```

如果 Pod 放在文件的末尾，并且您使用的是 **__END__** 或 **__DATA__** 剪切标记，那么请确保您在第一个 Pod 命令之前放了一个空行，否则如果在= **head1** 之前没有空行，许多翻译人员将无法识别= **head1** 作为 Pod 块的开始。

```
#!/usr/bin/perl

print "Hello, World\n";

while(<DATA>) {
  print $_;
}

__END__

=head1 Hello, World Example
This example demonstrate very basic syntax of Perl.
print "Hello, geeksforgeeks\n";
```

**输出:**

```
Hello, World

=head1 Hello, World Example
This example demonstrate very basic syntax of Perl.
print "Hello, geeksforgeeks\n";

```