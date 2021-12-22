# Perl |文件锁定

> 原文:[https://www.geeksforgeeks.org/perl-file-locking/](https://www.geeksforgeeks.org/perl-file-locking/)

文件锁定，或一般意义上的锁定，只是为解决与资源共享相关的问题而提出的各种解决方案之一。
*文件锁定*是一种保护任何文档安全性和完整性的方法。文件锁定的主要动机是允许人们*提交对文档的更改*，而不会造成文档混乱。当一个文件试图被两个或多个用户更改时，可能会出现冲突。

例如，让我们考虑一个包含项目数据的文件。允许整个项目团队修改文件。会有一个 CGI 脚本在网上编码来做以下事情。

```perl
$file = "project.docx";
$commit = $ENV{'QUERY_INFO'};
open(FILE, "$file"); #opening the document
while() {
  if (m/^$commit$/) {
    print "Change already made\n";
    exit;
  }
}
close(FILE);
push(@newcommit, $commit);
open(FILE, ">$file");
print ...
close(FILE);
print "Commit made!";
exit;
```

文件的锁定是在系统级完成的，这意味着用户不必担心应用锁定的实际细节。引入文件锁是为了对某些文件设置临时限制，以限制它们在不同进程之间的共享方式。根据操作的性质，我们提出了两种锁。第一种类型是共享锁，另一种是排他锁。对于文件，读访问可以由多个进程共享，因为读访问不会导致共享资源的状态发生任何变化。因此，可以维护共享资源的一致视图。
文件锁定可以做到，在 Perl 中，用 ***的羊群*** 的命令即可。

<center>**flock()**</center>

**`flock()`** accepts two parameters. The first one is the filehandle. The second argument indicates the locking operation required.

***语法*** :

> **群体【文件句柄】、【操作】**

这里 **OPERATION** 为数值，可以是 **1** 、 **2** 、 **4** 或 **8** 。
这些数值具有不同的含义，用于执行不同的操作，例如:

Perl 使用数字来表示值:

> sub LOCK_SH { 1 } ##设置为共享锁
> sub LOCK_EX { 2 } ##设置为排他锁
> sub LOCK_NB { 4 } ##设置不带任何块的锁
> sub LOCK_UN { 8 } ##解锁 FILEHANDLE

*   **SHARED LOCK:**
    A shared lock can be applied when you simply want to read the file, as well as allowing others to read the same file alongside. Shared Lock not only sets a lock, but it checks for the existence of other locks first. This Lock doesn’t cover the existence check for all the locks but only for ‘Exclusive Lock’. If an Exclusive Lock exists, it waits until the lock is removed. After removal, it will get executed as Shared Lock. There might exist multiple Shared Locks at the same time.

    ***语法*** :

    > 群体(文件，1)；#从上面的代码

*   **排他锁**
    当文件在一群人之间使用时，使用排他锁，并且每个人都获得了进行更改的许可。一个文件中只有一个*T4 独占锁，因此一次只有一个用户/进程进行更改。在排他锁中，规则是“我是唯一的。”flock()在脚本中查找任何其他类型的锁。如果找到了，它会一直保持下去，直到它们都从脚本中删除。在适当的时候，它会锁定文件。*

***语法*** :

> 群体(文件，2)；#从上面的代码

*   **NON-BLOCKING LOCK**
    A non-blocking lock informs the system not to wait for other locks to come off the file. It will return an error message if another lock has been found in the file.

    ***语法*** :

    > 羊群(文件，4)；#从上面的代码

*   **UNBLOCKING**
    Unblock any specified file- same as the close(FILE) function does.

    ***语法*** :

    > 羊群(文件，8)；#从上面的代码

    下面讨论的是一个解释使用 **flock()** 函数的问题:

    **问题:**
    上例中解释的脚本的主要问题是当它打开文件–**project . docx**时，清除第一个文件并使其为空。
    想象人 A、B、C 试图在几乎相同的时间做出承诺。

    人员 A 打开文件检查数据。关闭它，并开始编辑数据。(清除第一个文件)
    同时，人 B 打开文件进行检查/读取，注意到文件完全为空。

    那是一场冲突！整个系统都会被打乱。

    **解决方案:**
    这是**文件锁定**的地方。人甲、乙、丙愿意对该文件作出承诺。人 A 打开文件，那一刻(共享锁被激活)，签出文件内的所有数据并再次关闭(解锁文件)。
    然后，人 A 希望提交对文件的更改，并重新打开文件进行编辑(这是排他锁生效的时候)。当人 A 对文件进行更改时，人 B 或人 C 都不能打开文件进行读取或写入。

    人 A 做他的工作，关闭文件(解锁)。

    现在，如果人员 B 同时试图打开文件，将会得到一个错误——“文件正被其他候选人访问”。
    从而创造出不踩脚趾，保持良好的工作流程。

    <center>**flock() vs lockf()**</center>

    `**lockf()**` function is used to lock parts of a file unlike flock() which locks entire files at once. lockf() can not be used in the perl directly whereas Perl supports the flock system call natively but doesn’t applies on network locks.
    Perl also supports **fcntl()** system call which offers the most locking controls in Perl.