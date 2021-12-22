# 科特林动态滚动视图

> 原文:[https://www.geeksforgeeks.org/dynamic-scrollview-in-kotlin/](https://www.geeksforgeeks.org/dynamic-scrollview-in-kotlin/)

在**安卓**滚动视图包含多个视图，并允许滚动。

在本文中，我们将讨论如何以编程方式在 Kotlin 中创建一个 Scroll 视图。

让我们首先在安卓工作室创建一个项目。为此，请遵循以下说明:

*   点击**文件**，然后点击【新建】，然后点击**新建**项目，随便命名
*   然后，选择 **Kotlin** 语言支持，点击下一步按钮。
*   选择最小 **SDK** ，无论你需要什么。
*   选择空活动，然后点击**完成**。

## 修改 activity_main.xml 文件

第二步是设计我们的布局页面。在这里，我们将使用线性布局从柯特林文件中获取滚动视图。

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/layout"
        tools:context=".MainActivity">

</LinearLayout>
```

**添加图像**

我们将需要一些图像在应用中使用。您可以使用您喜欢的图像，但图像需要从我们的本地计算机路径复制到 app/res/drawable 文件夹。

## 在主活动文件中创建滚动视图

打开 app/src/main/Java/your package name/main activity . kt .在这个文件中，我们声明了一个变量 ScrollView 来创建滚动视图小部件，如下所示:

```
val scrollView = ScrollView(this)
        val layoutParams = LinearLayout.LayoutParams(
        ViewGroup.LayoutParams.MATCH_PARENT, 
        ViewGroup.LayoutParams.MATCH_PARENT)
        scrollView.layoutParams = layoutParams

```

然后使用以下命令在布局中添加小部件

```
linearLayout1?.addView(scrollView)
```

```
package com.geeksforgeeks.myfirstkotlinapp 

import androidx.appcompat.app.AppCompatActivity 
import android.os.Bundle
import android.view.Gravity
import android.view.ViewGroup
import android.widget.ImageView
import android.widget.LinearLayout
import android.widget.ScrollView

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val scrollView = ScrollView(this)
        val layoutParams = LinearLayout.LayoutParams(
        ViewGroup.LayoutParams.MATCH_PARENT,
        ViewGroup.LayoutParams.MATCH_PARENT)
        scrollView.layoutParams = layoutParams

        val linearLayout = LinearLayout(this)
        val linearParams = LinearLayout.LayoutParams(
        ViewGroup.LayoutParams.MATCH_PARENT,
        ViewGroup.LayoutParams.WRAP_CONTENT)
        linearLayout.orientation = LinearLayout.VERTICAL
        linearLayout.layoutParams = linearParams

        scrollView.addView(linearLayout)

        val imageView1 = ImageView(this)
        val params1 =
            LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, 
            ViewGroup.LayoutParams.WRAP_CONTENT)
        //setting margin 
        params1.setMargins(0, 30, 0, 30)
        //aligning the layout to center of the screen
        params1.gravity = Gravity.CENTER
        imageView1.setLayoutParams(params1)
        //setting our own downloaded/custom image to the imageView
        imageView1.setImageResource(R.drawable.image1)
        linearLayout.addView(imageView1)

        val imageView2 = ImageView(this)
        val params2 =
            LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, 
            ViewGroup.LayoutParams.WRAP_CONTENT)
        params2.setMargins(0, 0, 0, 30)
        params2.gravity = Gravity.CENTER
        imageView2.setLayoutParams(params2)
        imageView2.setImageResource(R.drawable.image2)
        linearLayout.addView(imageView2)

        val imageView3 = ImageView(this)
        val params3 =
            LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, 
            ViewGroup.LayoutParams.WRAP_CONTENT)
        params3.setMargins(0, 0, 0, 30)
        params3.gravity = Gravity.CENTER
        imageView3.setLayoutParams(params3)
        imageView3.setImageResource(R.drawable.image3)
        linearLayout.addView(imageView3)

        val imageView4 = ImageView(this)
        val params4 =
            LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, 
            ViewGroup.LayoutParams.WRAP_CONTENT)
        params4.setMargins(0, 0, 0, 30)
        params4.gravity = Gravity.CENTER
        imageView4.setLayoutParams(params4)
        imageView4.setImageResource(R.drawable.image4)
        linearLayout.addView(imageView4)

        val linearLayout1 = findViewById<LinearLayout>(R.id.layout)
        linearLayout1?.addView(scrollView)
    }
}
```

## AndroidManifest.xml 文件

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="i.apps.myapplication">

    <application
            android:allowBackup="true"
            android:icon="@mipmap/ic_launcher"
            android:label="@string/app_name"
            android:roundIcon="@mipmap/ic_launcher_round"
            android:supportsRtl="true"
            android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>

                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## 作为模拟器运行:

<center>
<video class="wp-video-shortcode" id="video-360137-1" width="292" height="404" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191117123557/scrollview.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191117123557/scrollview.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191117123557/scrollview.mp4)</video>
</center>