# 在安卓中包含并合并标签，示例

> 原文:[https://www . geesforgeks . org/include-and-merge-tags-in-Android-with-example/](https://www.geeksforgeeks.org/include-and-merge-tags-in-android-with-example/)

安卓应用正在增长，其中一个重要方面是**可重用性**。有时候，应用程序设计的复杂性会更高，在此期间，安卓通过 **<包含/ >** 和 **<合并/ >** 标签来提供非常高效的可重用功能。在<合并/ >标签下，我们可以指定布局中必须出现在主布局中的部分。类似于主布局有[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)、[文本视图](https://www.geeksforgeeks.org/textview-in-kotlin/)等。，它可以在一个有意义的 android 命名约定 XML 文件中指定。例如: **custom_layout.xml.** 在主布局中，我们可以通过使用< include/ >标签来重用 custom_layout。主要优势是许多应用程序页面可能需要自定义布局内容，只要有必要，使用< include/ >标签就可以轻松包含这些内容。此外，在修改的情况下，这是一个地方的变化，因此最大限度地避免/减少返工。一般用于定制化的思路，使用<的 app 内容的复用性包括/ >和<合并/ >标签。

### **包含标签**

这用于包含可重用内容的内容。这是在主布局中共享另一个布局的内容的一个非常好的想法。

## 可扩展标记语言

```kt
<!-- custom_layout is a separate layout xml file
     which can be shared, reused in many places-->
<include
  android:id="@+id/custom_layout"
  layout="@layout/custom_layout"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content" />
```

### **合并标签**

当一个布局包含在另一个布局中时，<merge>标签帮助我们消除视图层次结构中的冗余视图组。因此，在我们的示例中，我们直接拥有像 Button 和 [ImageView](https://www.geeksforgeeks.org/imageview-in-kotlin/) 这样的 android 元素，因为这将包含在主视图中，并且它将采用主文件中指定的布局，即 **activity_main.xml(主布局文件)**。</merge>

## 可扩展标记语言

```kt
<merge xmlns:android="http://schemas.android.com/apk/res/android">

    <Button
        android:id="@+id/ButtonToInclude"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:text="Button is under merge tag"
        android:textColor="#fff"
        android:textSize="18sp"
        android:textStyle="italic" />

    <ImageView
        android:id="@+id/imageViewToInclude"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:src="@drawable/cryptocurrency" />

</merge>
```

> **注意:**我们可以发现< include/ >和< merge/ >标签看起来和 ViewStub 类似，其实不然。
> 
> *   视图存根标签有点不同，因为它不是直接包含的，只有在您真正需要的时候才会加载，也就是说，当您将视图存根的可见性设置为“真”时。
> *   但是 include 和 merge 标签是在开始时直接包含和加载的，主要有助于拆分布局并在必要时重用它们。

### **包含的属性**

<figure class="table">

| 

属性

 | 

描述

 |
| --- | --- |
| 身份证明（identification） | 要唯一标识包含标签 |
| 布局 | 将布局资源的标识符提供给在我们的主布局中包含自定义布局。 |

</figure>

### **例**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#fff"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:layout_marginBottom="100dp"
        android:text="Main Layout Text"
        android:textColor="@color/colorAccent"
        android:textSize="20sp" />

    <include
        android:id="@+id/custom_layout"
        layout="@layout/custom_layout"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

</LinearLayout>
```

**第三步:新建布局资源文件**

转到**应用程序> res >布局>右键单击>新建>布局资源文件**，并将文件命名为**自定义 _ 布局**。下面是 **custom_layout.xml** 的代码，该文件应该包含合并内容。

## 可扩展标记语言

```kt
<merge xmlns:android="http://schemas.android.com/apk/res/android">

    <Button
        android:id="@+id/ButtonToInclude"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:text="Button is under merge tag"
        android:textColor="#fff"
        android:textSize="18sp"
        android:textStyle="italic" />

    <ImageView
        android:id="@+id/imageViewToInclude"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:src="@drawable/cryptocurrency" />

</merge>
```

**第 4 步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.os.Bundle
import android.view.View
import android.widget.Button
import android.widget.ImageView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    var customButton: Button? = null
    var customImageView: ImageView? = null

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // As custom layout contents are included, we can refer them as normal way
        // Main advantage lies here only. even this custom_layout can be reusued in different xml
        // and in corresponding activity file, they can be referred and there may be a
        // different functionality can be carried out.
        // get the reference of custom Layout's Button
        customButton = findViewById<View>(R.id.ButtonToInclude) as Button

        // get the reference of custom Layout's ImageView
        customImageView = findViewById<View>(R.id.imageViewToInclude) as ImageView

        // We have clicked on Custom layout button, though it is in separate xml
        // because of include tag, it is getting focus here and we can do
        // activities as we like
        customButton!!.setOnClickListener {
            Toast.makeText(applicationContext, "We have clicked on Custom layout button", Toast.LENGTH_LONG).show()
        }
    }
}
```

### **在电动**黑白混血儿**上运行代码**

我们可以得到视频中的输出。在需要的地方应用<include>和<merge>标签，享受安卓应用的可重用特性。</merge></include>

<video class="wp-video-shortcode" id="video-507253-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201028155639/IncludeTagExample1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201028155639/IncludeTagExample1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201028155639/IncludeTagExample1.mp4)</video>