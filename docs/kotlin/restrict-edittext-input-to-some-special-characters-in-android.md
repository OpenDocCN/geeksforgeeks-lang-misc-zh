# 限制安卓系统中某些特殊字符的编辑文本输入

> 原文:[https://www . geesforgeks . org/restrict-edittext-input-to-some-special-characters in-Android/](https://www.geeksforgeeks.org/restrict-edittext-input-to-some-special-characters-in-android/)

在其他一些应用程序中，我们中的大多数人一定目睹了在某些字段中键入时，我们会收到一条警告或一条提示消息，指出某些字符不被允许或不被接受为有效输入。例如，有时，在 Windows 中重命名文件或文件夹时，如果我们简单地键入“？”，我们得到一个信息是什么？不被接受为有效输入。这是因为字符“？”必须在该操作系统的文件系统中具有某种功能意义。同样，对其他特殊字符也可能有限制，因为它们可能在操作系统的文件系统中具有某种功能意义。类似地，这个概念可以应用于任何类型的用户输入。假设注册时输入的是所需的用户名，我们可以应用类似的概念来避免使用数字或特殊字符。因此，在本文中，我们将向您展示如何在安卓系统中将编辑文本的输入限制为一组特定的字符。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在**科特林**中演示了该应用程序，因此在创建新项目时，请确保选择科特林作为主要语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。我们创建了一个[编辑文本](https://www.geeksforgeeks.org/working-with-the-edittext-in-android/)，在这里可以输入。注意 ***安卓:数字*** 属性只允许输入流中的给定字符。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="50sp"
        android:hint="Type something..."
        android:inputType="text"
        android:digits="abcd@#$123"/>

</RelativeLayout>
```

**第三步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。这个文件中不需要额外的代码。

## 我的锅

```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

**输出:**

您可以看到，只有那些字符被打印在针对编辑文本的 ***安卓:数字*** 属性声明的编辑文本中。

<video class="wp-video-shortcode" id="video-728382-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210816203510/o101.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210816203510/o101.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210816203510/o101.mp4)</video>