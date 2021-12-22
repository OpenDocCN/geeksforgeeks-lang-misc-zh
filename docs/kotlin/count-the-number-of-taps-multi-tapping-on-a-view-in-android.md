# 统计安卓系统中视图的点击次数(多次点击)

> 原文:[https://www . geeksforgeeks . org/count-点击次数-android 中多次点击查看/](https://www.geeksforgeeks.org/count-the-number-of-taps-multi-tapping-on-a-view-in-android/)

本文统计了用户在短时间内在特定视图上点击的次数，它可用于添加不同点击的不同响应。例如，在单词上轻按一下将显示该单词的含义，而双击将在字典应用程序中显示其同义词。下面是一个示例，其中 textview 中的拍击次数显示为一个吐司。

**第一步:**在安卓工作室创建一个空活动。创建一个，遵循这篇文章-[https://www . geeksforgeeks . org/Android-如何创建-启动-一个新的项目-在 android-studio/](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/) 。检查选择的主要语言是否为**科特林。**

**步骤 2:**activity _ main . XML 中没有进行任何更改。因为已经存在一个 textview，所以三次点击的响应也随之添加。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Click Here"
        />

</RelativeLayout>
```

**第 3 步:**在这一步中，用视图添加 onTouchListenter。在监听器中，初始化一个变量为 0，它将记录用户点击的次数。每次用户在短时间内点击时，变量值都会增加一。下面是 MainActivity.kt 类的代码。

## 我的锅

```kt
package org.geeksforgeeks.tripletap

import android.os.Bundle
import android.os.Handler
import android.view.MotionEvent
import android.view.View
import android.view.ViewConfiguration
import android.widget.Button
import android.widget.RelativeLayout
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declaring Text View from the Layout file
        val tvv = findViewById<TextView>(R.id.tv)

        // Implementing onTouchListener on our Text View
        tvv.setOnTouchListener(object : View.OnTouchListener {
          // Handler to handle the number of clicks
            var handler: Handler = Handler()
            var numberOfTaps = 0
            var lastTapTimeMs: Long = 0
            var touchDownMs: Long = 0
            override fun onTouch(v: View?, event: MotionEvent): Boolean {
                when (event.action) {
                    MotionEvent.ACTION_DOWN -> touchDownMs = System.currentTimeMillis()
                    MotionEvent.ACTION_UP -> {
                      // Handle the numberOfTaps
                        handler.removeCallbacksAndMessages(null)
                        if (System.currentTimeMillis() - touchDownMs 
                            > ViewConfiguration.getTapTimeout()) {
                            //it was not a tap
                            numberOfTaps = 0
                            lastTapTimeMs = 0
                        }
                        if (numberOfTaps > 0
                            && System.currentTimeMillis() - lastTapTimeMs 
                            < ViewConfiguration.getDoubleTapTimeout()
                        ) {
                          // if the view was clicked once
                            numberOfTaps += 1
                        } else {
                          // if the view was never clicked
                            numberOfTaps = 1
                        }
                        lastTapTimeMs = System.currentTimeMillis()

                        // Handle Multiple Taps on the View////////////////////////////////
                       handler.postDelayed(Runnable {

                         // Toast the number of Taps of current User Event
                                Toast.makeText(applicationContext, "$numberOfTaps Clicks", 
                                               Toast.LENGTH_SHORT)
                                        .show()
                            }, ViewConfiguration.getDoubleTapTimeout().toLong())
                     /////////////////////////////////////////////////////////////////////

                    }
                }
                return true
            }
        })
    }
}
```

#### 仿真器上的输出:

<video class="wp-video-shortcode" id="video-498145-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001125211/Screen-Recording-2020-09-23-at-15.51.56.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001125211/Screen-Recording-2020-09-23-at-15.51.56.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001125211/Screen-Recording-2020-09-23-at-15.51.56.mp4)</video>