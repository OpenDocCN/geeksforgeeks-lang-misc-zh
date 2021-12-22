# CGI 中的 Perl |文件上传

> 原文:[https://www.geeksforgeeks.org/perl-file-upload-in-cgi/](https://www.geeksforgeeks.org/perl-file-upload-in-cgi/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 是通用编程语言，专门为文本操作而设计，目前用于各种任务，包括系统管理、web 开发、网络编程、GUI 开发以及其他更多领域。

在 Perl 中， **CGI** (公共网关接口)是一种通过 web 请求执行脚本的协议，或者换句话说，我们可以说它是一组定义自定义脚本和 Web 服务器之间如何交换信息的规则和标准。

**CGI Architecture Diagram**

![](img/6352990ee812b8a9a1f582a86b5a06ac.png)

**How CGI uploads the file**

在 Web 服务器端，软件(在我们的例子中，是一个 CGI 脚本)解释从浏览器发送的表单数据，并提取文件名和内容，以及其他表单字段。通常，文件会保存到服务器上的一个目录中。

**注**:以下是建立 CGI 上传脚本的必要条件:

*   访问兼容 CGI 的网络服务器
*   网络服务器上必须运行一份 Perl
*   您的网络服务器必须包含

在网络服务器上上传文件是使用文件上传表单完成的。此文件上传表单是在任何可用的文本编辑器上创建的，并且表单必须与一起保存。htm 或。html 扩展。文件上传表单的创建包括以下步骤:

**第一步:创建表单元素**
首先，需要创建一个“表单”元素

```perl
<form action="/cgi-bin/upload.cgi" method="post" enctype="multipart/form-data">
```

> **注意:**在上面的代码中，多部分/表单数据是用于文件上传的编码类型，文件 **upload.cgi** 用于存储使用此表单发布的数据

**第二步:创建表单字段**
其次，我们需要为表单提供字段。这些字段用于指导用户在表单中上传需要的文件。
例如，在这里，我们将提供一个上传字段，供用户上传他们的照片并提供他们的电子邮件。

```perl
<p>Upload Photo: <input type="file" name="photo" /></p>
<p>Email: <input type="text" name="email_address" /></p>
```

**第三步:提供提交表单按钮**
第三步是允许用户根据表单中给出的字段提交上传的所有文件。为此，需要一个提交按钮，以便用户可以将表单发送到网络服务器。

```perl
<!--using button for sending the form to web server-->
<p><input type="submit" name="Submit" value="Submit Form" /></p>
```

**示例:在 CGI 中显示文件上传工作的示例表单:**

```perl
<!DOCTYPE html> 
<html lang="en"> 
<head>
    <meta http-equiv = "Content-Type" content = "text/html; charset=utf-8" /> 
    <title>File Upload</title>
</head> 
<body style = "text-align:center;"> 
    <h1 style = "color:green;"> GeeksForGeeks </h1> 
    <form action = "/cgi-bin/upload.cgi"
          method = "post" enctype = "multipart/form-data">
    <p>Upload Photo: <input type = "file" name = "photo" /></p>
    <p>Email: <input type = "text"
                     placeholder = "e.g. GFG@gmail.com"
                     name = "email_address" /></p>
    <p><input type = "submit" name = "Submit" value = "Submit Form" /></p>
    </form> 
</body>
</html>                    
```

**输出:**
![](img/07bbd4a6c77325d6863756a97142e29c.png)