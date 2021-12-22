# 科特林动态进度条

> 原文:[https://www . geesforgeks . org/dynamic-progress bar-in-kot Lin/](https://www.geeksforgeeks.org/dynamic-progressbar-in-kotlin/)

安卓 **ProgressBar** 是用户界面控件，用来显示某种进度。例如，加载某个页面、下载某个文件或等待某个事件完成。

在本文中，我们将讨论如何通过编程在 Kotlin 中创建一个进度条。

首先，我们需要在安卓工作室创建一个项目。为此，请遵循以下步骤:

*   点击**文件**，然后**新建**然后**新项目**随便命名
*   然后，选择科特林语言支持，点击下一步按钮。
*   选择最小的软件开发工具包，无论你需要什么。
*   选择**清空**活动，然后点击**完成**。

## 修改 activity_main.xml 文件

第二步是设计我们的布局页面。在这里，我们将使用 RelativeLayout 从 Kotlin 文件中获取 ProgressBar。

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context=".MainActivity">

    <RelativeLayout
            android:id="@+id/layout"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:layout_centerHorizontal="true"
            android:layout_above="@+id/button">

    </RelativeLayout>

    <Button
            android:id="@+id/button"
            android:layout_marginTop="100dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_centerInParent="true"
            android:text="Stop Loading"/>

</RelativeLayout>
```

**更新字符串. xml 文件**

```
<resources>
    <string name="app_name">DynamicProgressBarInKotlin</string>
</resources>
```

## 在 MainActivity.kt 文件中创建 ProgressBar

打开 app/src/main/Java/your package name/main activity . kt .在这个文件中，我们声明了一个变量 **progressBar** 来创建 progressBar 小部件，如下所示

```
       val progressBar = ProgressBar(this)
       //setting height and width of progressBar
       progressBar.layoutParams = LinearLayout.LayoutParams(
           ViewGroup.LayoutParams.WRAP_CONTENT,
           ViewGroup.LayoutParams.WRAP_CONTENT)

```

然后使用以下命令在布局中添加小部件

```
val layout = findViewById(R.id.layout)
     // Add ProgressBar to our layout
     layout?.addView(progressBar) 
```

```
package com.geeksforgeeks.myfirstkotlinapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.view.ViewGroup
import android.widget.Button
import android.widget.LinearLayout
import android.widget.ProgressBar
import android.widget.RelativeLayout

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val progressBar = ProgressBar(this)
        //setting height and width of progressBar
        progressBar.layoutParams = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.WRAP_CONTENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)

        //accessing our relative layout where the progressBar will add up
        val layout = findViewById<RelativeLayout>(R.id.layout)
        // Add ProgressBar to our layout
        layout?.addView(progressBar)

        //accessing the button which will handle the events,
        // whether to show progressBar or not
        val button = findViewById<Button>(R.id.button)

        //set a click listener to show/hide progressBar added in RelativeLayout.
        button?.setOnClickListener {
            val visibility = if (progressBar.visibility == View.GONE){
                View.VISIBLE
            }else
                View.GONE
            progressBar.visibility = visibility

            //setting button text
            //if we click "stop loading" button, text of button will change
            // to "start loading.." and vice versa
            val btnText = if (progressBar.visibility == View.GONE)
                "START LOADING..."
            else
                "STOP LOADING"
            button.text = btnText
        }

    }
}
```

## AndroidManifest.xml 文件

```
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

<video class="wp-video-shortcode" id="video-354224-1" width="300" height="400" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191027205724/untitled1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191027205724/untitled1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191027205724/untitled1.mp4)</video>