# 使用 Perl 从网络下载文件

> 原文:[https://www . geesforgeks . org/downling-file-from-web-use-perl/](https://www.geeksforgeeks.org/downloading-files-from-web-using-perl/)

[Perl](https://www.geeksforgeeks.org/introduction-to-perl/) 是一种多用途的解释语言，通常使用 Perl 脚本来实现，这些脚本可以使用。pl 扩展，并直接使用终端或命令提示符运行。它是一种稳定的、跨平台的语言，主要是在文本操作和修改以及从网页中提取信息方面具有强大的能力。它正在积极开发和开源。由于它能够与 HTML、XML 和其他标记语言一起工作，所以它在网络开发、系统管理甚至图形用户界面开发中都有很大的用途。它主要与网络一起使用，因为除了电子商务交易之外，它还可以处理加密的网络数据。

在本文中，我们将看到使用 Perl 脚本下载网页和图像的不同方法。

## 使用 Perl 下载网页

### **使用系统命令 wget** 下载网页

在这种方法中，我们编写了一个子程序，将一个网址传递给一个系统命令。该变量以原始的 HTML 形式存储网页内容。然后我们返回这些内容。

## Perl 语言

```perl
#!usr/bin/perl

# using the strict pragma
use strict;

# using the warnings pragma
# to generate warnings in case of incorrect
# code
use warnings;

# specifying the Perl version 
use 5.010;

# declaring the sub routine
sub getWebPage {

    # variable to store the URL
    my $url = 'http://www.google.com/';

    # variable to store the contents of the 
    # web page
    my $webpage = system 
    "wget --output-document=- $url";

    # returning the contents of the web page
    return $webpage;
}

# printing user friendly message
say "the contents of the downloaded web page : ";

# calling the sub routine
getWebPage();
```

**输出:**

```perl
the contents of the downloaded web page :
<raw HTML web page>
```

### **使用系统命令 curl 下载网页**

这种方法与上面完全相同，唯一的区别是这里使用的系统命令是“curl”代替“wget”。

## Perl 语言

```perl
#!usr/bin/perl

# using the strict pragma
use strict;

# using the warnings pragma to 
# generate warnings in case of 
# erroneous code
use warnings;

# specifying the Perl version
use 5.010;

# declaring the sub routine
sub getWebPage {

    # variable to store the URL
    my $url = 'http://www.google.com/';

    # variable to store the contents of the
    # downloaded web page
    my $downloadedPage = system "curl $url";

    # returning the contents using the variable
    return $downloadedPage;
}

# displaying a user friendly message
say "the contents of the web page : ";

# calling the sub routine
getWebPage();
```

**输出:**

```perl
the contents of the downloaded web page :
<raw HTML web page>
```

### **使用 LWP::简单模块**下载网页

LWP::Simple 是 Perl 中的一个模块，它提供了一个 get()，该 get 将 URL 作为参数并返回文档的正文。如果服务器无法处理请求的网址，它将返回 undef。

## Perl 语言

```perl
#!usr/bin/perl

# using the strict pragma
use strict;

# using the warnings pragma to
# generate warnings in case of 
# erroneous codes
use warnings;

# specifying the Perl version
use 5.010;

# calling the LWP::Simple module
use LWP::Simple;

# declaring the sub routine
sub getWebPage {

    # variable to store the URL 
    my $url = 'http://www.google.com';

    # passing the URL to the get function
    # of LWP::Simple module
    my $downloadedPage = get $url;

    # printing the contents of the web page
    say $downloadedPage;
}

# displaying a user friendly message
say 'the contents of the web page are : ';

#calling the sub routine
getWebPage();
```

**输出:**

```perl
the contents of the downloaded web page :
<raw HTML web page>
```

### **使用 HTTP 下载网页::微小**

HTTP::Tiny 是一个简单的 HTTP/1.1 客户端，这意味着它用于获取、放置、删除、头(基本的 HTTP 动作)。它用于执行简单的请求，而没有大型框架的开销。首先，使用新的运算符实例化一个 HTTP 变量。接下来，我们通过在 get 方法中传递 URL 来获取请求的代码。在成功的代码中，我们在指定的网址获取网页的长度和内容。在代码不成功的情况下，我们会显示适当的消息，并提到连接失败的原因。

## Perl 语言

```perl
#!usr/bin/perl

# using the warnings pragma to
# generate warnings in case of 
# erroneous code
use warnings;

# specifying the Perl version
use 5.010;

# calling the HTTP::Tiny module
use HTTP::Tiny;

# declaring the sub routine
sub getWebPage{

    # variable to store the URL
    my $url = 'http://www.google.com/';

    # instantiating the HTTP variable
    my $httpVariable = HTTP::Tiny->new;

    # storing the response using the get
    # method
    my $response = $httpVariable->get($url);

    # checking if the code returned successful
    if ($response -> {success}){

        # specifying the length of the
        # web page content using the 
        # length keyword
        say 'the length of the web page : ';
        my $length = length $response->{content};
        say $length;

        # displaying the contents of the webpage
        say 'the contents of the web page are : ';
        my $downloadedPage = $response->{content};
        say $downloadedPage;
    }

    # logic for when the code is
    # unsuccessful
    else{

        # displating the reason for failed
        # request
        say "Failed to establish connection : 
        $response->{status}.$response->{reasons}";
    }
}

# calling the sub routine
getWebPage();
```

**输出:**

```perl
the length of the web page : 
15175
the contents of the web page are :
<html code of the web page>
```

### **使用 HTTP 下载多个网页::微小**

使用 HTTP::Tiny 下载多个网页的方法与上面提到的方法相同。唯一的修改是，这里所有网页的网址都存储在一个数组中，我们在数组中循环显示每个网页的内容。

## Perl 语言

```perl
#!usr/bin/perl

# using the warnings pragma
# to generate warnings for
# erroneous code
use warnings;

# specifying the Perl version
use 5.010;

# calling the HTTP::Tiny module
use HTTP::Tiny;

# declaring the sub routine
sub getWebPages{

    # instantiating the HTTP client
    my $httpVariable = HTTP::Tiny->new;

    # array of URLs
    my @urls = ('http://www.google.com/',
    'https://www.geeksforgeeks.org/'
    );

    # start of foreach loop to
    # loop through the array of URLs
    foreach my $singleURL (@urls){

        # dsiplaying user friendly message
        say 'downloading web page...';

        # variable to store the response
        my $response = $httpVariable->
        get($singleURL);

        # logic for successful connection
        if ($response->{success}){
            say $singleURL.
            " downloaded successfully";

            # displaying the length of
            # the web page
            # the contents can be displayed
            # similarly
            say "Length : length 
            $response->{content}";
        }

        # logic for unsuccessful connection
        else{
            say $singleURL.
            " could not be downloaded";

            # displaying the reason for
            # unsuccessful connection
            say "$response->{status}
            $response->{reasons}";
        }
    }
}

# calling the sub routine
getWebPages();
```

**输出:**

```perl
downloading web page...
downloaded successfully
Length : 15175
<html content of the landing page of google>
downloading web page...
downloaded successfully
Length : <Length of the landing page of GFG>
<html content of the landing page of GFG>
```

## **使用 Perl 下载图像**

在本节中，我们将看到两种使用 Perl 脚本下载图像的方法。为了获得这些图像的网址，我们首先右键单击它们。接下来，我们从下拉列表中单击复制图像地址，并将其粘贴为图像的网址。

### **使用 LWP 下载图片::简单**

在这种方法中，我们使用 LWP::Simple 模块，并使用 getstore 函数获取 HTTP 代码。在这个函数中，我们必须指定要下载的图像的网址和存储下载图像的位置。接下来，我们检查代码是否成功，并向用户显示相应的消息。

## Perl 语言

```perl
#!usr/bin/perl

# using the strict pragma
use strict;

# using the warnings pragma
# to generate warnings for
# erroneous code
use warnings;

# specifying the Perl version
use 5.010;

# calling the module
use LWP::Simple;

# declaring the sub routine
sub getImage {

    # displaying a user friendly message
    say "Downloading ... ";

    # variable to store the status code
    # first parameter is the URL of the image
    # second parameter is the location
    # of the downloaded image
    my $statusCode = getstore
    ("https://www.geeksforgeeks.org/wp-content/uploads/gfg_200X200-1.png",
    "downloaded_image.png");

    # checking for successful
    # connection
    if ($statusCode == 200) {
        say "Image successfully downloaded.";
    }
    else {
        say "Image download failed.";
    }
}

# calling the sub routine
getImage();
```

**输出:**

```perl
Downloading...
Image successfully downloaded.
(the downloaded image will be saved at the specified location
with the given name. If no location is specified then the image
would be saved in the current working directory.
```

### **使用图像::抓取模块下载图像**

**Image::Grab** 是一个简单的模块，用于下载由其网址指定的图像。它也适用于可能被某种方法隐藏的图像。在这种方法中，我们使用 Image::Grab 模块，在实例化它之后，我们传递 URL。接下来，我们调用 grab 方法并将下载的图像保存到磁盘。

## Perl 语言

```perl
#!usr/bin/perl

# using the strict pragma
use strict;

# using the warnings pragma to
# generate warnings for erroneous
# code
use warnings;

# specifying the Perl version
use 5.010;

# calling the Image::Grab module
use Image::Grab;

# instantiating the module
# and storing it in a variable
my $instantiatedImage = new Image::Grab;

# declaring the sub routine
sub getImage {

    # specifying the URL
    $instantiatedImage->url
    ('https://www.geeksforgeeks.org/wp-content/uploads/gfg_200X200-1.png');

    # calling grab to grab the image
    $instantiatedImage->grab;

    # creating a file to store
    # the downloaded image
    open(DOWNLOADEDIMAGE, '>downloaded_image1.png') || 
                        die'downloaded_image1.png: $!';

    # for MSDOS only
    binmode DOWNLOADEDIMAGE;

    # saving the image in the created
    # file
    print DOWNLOADEDIMAGE $instantiatedImage->image;

    # closing the file
    close instantiatedImage;
}

# calling the sub routine
getImage();
```

**输出:**

```perl
The image is stored with the specified file name.
```

**下载图像:**

![](img/386963573f5d8e808e86819a574ffbdb.png)