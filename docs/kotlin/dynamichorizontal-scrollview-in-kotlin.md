# 科特林的动脉冲星滚动视图

> 原文:[https://www . geeksforgeeks . org/dynamichorizontal-scroll view-in-kot Lin/](https://www.geeksforgeeks.org/dynamichorizontal-scrollview-in-kotlin/)

安卓**滚动视图**允许滚动父视图组中的多个视图。安卓应用程序中的滚动可以通过两种方式完成:垂直或水平。

在本文中，我们将讨论如何通过编程在 Kotlin 中创建一个水平滚动视图。

让我们首先在安卓工作室创建一个项目。为此，请遵循以下说明:

*   点击**文件**，然后**新建**然后新建项目，随便命名
*   然后，选择科特林语言支持，点击下一步按钮。
*   选择最小的软件开发工具包，无论你需要什么。
*   选择**清空**活动，然后点击完成。

## 修改 activity_main.xml 文件

在这里，我们将使用 RelativeLayout 从 Kotlin 文件中获取滚动视图。

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context=".MainActivity">

    <RelativeLayout
            android:layout_width="match_parent"
            android:layout_height="200dp"
            android:id="@+id/layout"
            android:layout_centerInParent="true"/>

   </RelativeLayout>
```

**更新字符串. xml 文件**

```kt
<resources>
    <string name="app_name">DynamicHorizontal ScrollView</string>
</resources>
```

## 添加图像

我们需要添加一些图像，可以用于滚动的目的。因此，我们必须将图像从本地计算机路径复制到**app/RES/drawing**文件夹。

## 在主活动文件中创建水平滚动视图

打开 app/src/main/Java/your package name/main activity . kt .在这个文件中，我们声明了一个变量 **horizontalScrollView** 来创建 horizontalScrollView 小部件，如下所示:

```kt
 val horizontalScrollView = HorizontalScrollView(this)
    //setting height and width
    val layoutParams = LinearLayout.LayoutParams(
                        ViewGroup.LayoutParams.MATCH_PARENT, 
                        ViewGroup.LayoutParams.MATCH_PARENT)
    horizontalScrollView.layoutParams = layoutParams

```

然后，使用以下命令在布局中添加小部件

```kt
   val linearLayout1 = findViewById(R.id.layout)
       linearLayout1?.addView(horizontalScrollView)

```

```kt
package com.geeksforgeeks.myfirstkotlinapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.ViewGroup
import android.widget.HorizontalScrollView
import android.widget.ImageView
import android.widget.LinearLayout
import android.widget.RelativeLayout

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val horizontalScrollView = HorizontalScrollView(this)
        //setting height and width
        val layoutParams = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.MATCH_PARENT)
        horizontalScrollView.layoutParams = layoutParams

        val linearLayout = LinearLayout(this)
        //setting height and width
        val linearParams = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)
        linearLayout.layoutParams = linearParams

        //adding horizontal scroll view to the layout
        horizontalScrollView.addView(linearLayout)

        val image1 = ImageView(this)
        //setting height and width
        val params1 = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)
        image1.layoutParams = params1
        //accessing images that we downloaded and copied to
        // drawable folder and setting it to imageview
        image1.setImageResource(R.drawable.img1)
        linearLayout.addView(image1)

        val image2 = ImageView(this)
        //setting height and width
        val params2 = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)
        image2.layoutParams = params2
        //accessing images that we downloaded and copied to 
        // drawable folder and setting it to imageview
        image2.setImageResource(R.drawable.img2)
        linearLayout.addView(image2)

        val image3 = ImageView(this)
        //setting height and width
        val params3 = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)
        image3.layoutParams = params3
        //accessing images that we downloaded and copied to 
        // drawable folder and setting it to imageview
        image3.setImageResource(R.drawable.img3)
        linearLayout.addView(image3)

        val image4 = ImageView(this)
        //setting height and width
        val params4 = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)
        image4.layoutParams = params4
        //accessing images that we downloaded and copied to 
        // drawable folder and setting it to imageview
        image4.setImageResource(R.drawable.img4)
        linearLayout.addView(image4)

        val image5 = ImageView(this)
        //setting height and width
        val params5 = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)
        image5.layoutParams = params5
        //accessing images that we downloaded and copied to
        // drawable folder and setting it to imageview
        image5.setImageResource(R.drawable.img5)
        linearLayout.addView(image5)

        //accessing the relative layout where the scrollview will be active
        val linearLayout1 = findViewById<RelativeLayout>(R.id.layout)
        linearLayout1?.addView(horizontalScrollView)

    }
}
```

## AndroidManifest.xml 文件

```kt
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
package="com.geeksforgeeks.myfirstkotlinapp">

<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/AppTheme">
    <activity android:name=".MainActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />

            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>

</manifest>
```

## 作为模拟器运行:

这是 android 应用程序中水平滚动的视频。

<video class="wp-video-shortcode" id="video-354585-1" width="300" height="504" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191030103053/scrollViewmp4.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191030103053/scrollViewmp4.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191030103053/scrollViewmp4.mp4)</video>