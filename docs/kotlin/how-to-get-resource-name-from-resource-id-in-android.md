# 如何在安卓中从资源 ID 获取资源名称？

> 原文:[https://www . geesforgeks . org/如何从 android 中的资源 id 获取资源名称/](https://www.geeksforgeeks.org/how-to-get-resource-name-from-resource-id-in-android/)

在安卓系统中，资源名称是在代码或 XML 中声明资源时分配给资源的名称。资源名称的格式为:

```
***[<package_name>.]R.<resource_type>.<resource_name>***
```

在哪里

*   ***<包 _ 名称>*** 是存储资源的包的名称
*   ***<resource _ type>***是资源类型(可绘制、字符串、颜色等)的 R 子类
*   ***<resource _ name>***是资源的名称(如果在布局元素中声明的话)(android: name)或者是没有扩展名的文件名

下面是我们如何在代码和 XML 中声明资源:

*   **在代码中:** R.string.geeksforgeeks
*   **在 XML 中:** @string/geeksforgeeks

在本文中，我们将向您展示如何使用资源 id 获取资源名称。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 **Kotlin** 中演示了该应用程序，因此在创建新项目时，请确保选择 Kotlin 作为主要语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** ，并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。在布局文件中添加一个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)和一个[文本视图](https://www.geeksforgeeks.org/textview-in-kotlin/)。

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

    <!-- We shall find the resource name of this Button -->
    <!-- Also, if we click this button, we shall get 
         the desired results in the TextView below -->
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="click"
        android:layout_centerInParent="true"/>

    <!-- This TextView shall display the resource name
          when the above button is clicked -->
    <TextView
        android:id="@+id/textView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:gravity="center"
        android:layout_above="@id/button"/>

</RelativeLayout>
```

**第三步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。获取资源 id，点击按钮获取并显示资源名称。

## 我的锅

```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.TextView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declaring and initializing the button
        // and text view from the layout file
        val mButton = findViewById<Button>(R.id.button)
        val mTextView = findViewById<TextView>(R.id.textView)

        // Fetching the id of the button (resource
        val resourceId = mButton.id

        // Getting the name of the resource
        val resourceName = resources.getResourceName(resourceId)

        // When button is clicked, the text view
        // will display the value of resourceName
        mButton.setOnClickListener {
            mTextView.text = resourceName.toString()
        }
    }
}
```

**输出:**

您可以看到，单击按钮时，资源名称会显示在文本视图中。

<video class="wp-video-shortcode" id="video-659807-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210804104628/26.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210804104628/26.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210804104628/26.mp4)</video>