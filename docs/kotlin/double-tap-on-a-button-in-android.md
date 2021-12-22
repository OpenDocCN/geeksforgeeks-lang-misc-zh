# 双击安卓系统中的按钮

> 原文:[https://www . geeksforgeeks . org/安卓双击按钮/](https://www.geeksforgeeks.org/double-tap-on-a-button-in-android/)

检测按钮上的双击，即每当用户双击任何按钮时，如何检测它，并且根据按钮，可以添加对应于它的响应。这里显示了一个例子，其中检测到按钮上的双击，并且相应地以烤面包的形式添加响应。

**第一步:**在安卓工作室创建一个空活动。创建一个，跟随这篇文章- [**如何在安卓工作室创建/启动一个新项目？**](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/) 。检查选择的主要语言是否为**科特林。**

**第二步:**在 activity_main.xml 中，添加一个检测双击的按钮。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

  <!--Declare a button which shall be used to detect double taps-->
    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Double Tap"
        />

</RelativeLayout>
```

**步骤 3:** 在这一步中，为双击添加抽象类，并设置 onClickListener，它将使用抽象类。展示祝酒词。下面是 MainActivity.kt 类的代码。

## 我的锅

```kt
package org.geeksforgeeks.doubletap_onbutton

import android.os.Bundle
import android.view.View
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare the button from the layout file as Text View
        // Since the method works only on Views
        val dBtn = findViewById<TextView>(R.id.btn)

        // Implementing a DoubleClickListener on the Button
        dBtn.setOnClickListener(object : DoubleClickListener() {
            override fun onDoubleClick(v: View?) {
                Toast.makeText(applicationContext,"Double Click",Toast.LENGTH_SHORT).show()
            }
        })
    }

    // This class has methods that check if two clicks were registered
    // within a span of DOUBLE_CLICK_TIME_DELTA i.e., in our case
    // equivalent to 300 ms
    abstract class DoubleClickListener : View.OnClickListener {
        var lastClickTime: Long = 0
        override fun onClick(v: View?) {
            val clickTime = System.currentTimeMillis()
            if (clickTime - lastClickTime < DOUBLE_CLICK_TIME_DELTA) {
                onDoubleClick(v)
            }
            lastClickTime = clickTime
        }

        abstract fun onDoubleClick(v: View?)

        companion object {
            private const val DOUBLE_CLICK_TIME_DELTA: Long = 300 //milliseconds
        }
    }
}
```

#### 仿真器上的输出:

<video class="wp-video-shortcode" id="video-497083-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001121032/Screen-Recording-2020-09-23-at-14.46.34.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001121032/Screen-Recording-2020-09-23-at-14.46.34.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001121032/Screen-Recording-2020-09-23-at-14.46.34.mp4)</video>