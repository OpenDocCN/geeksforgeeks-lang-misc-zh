# 在安卓中编程检查网速

> 原文:[https://www . geesforgeks . org/programmable-check-network-in-speed-Android/](https://www.geeksforgeeks.org/programmatically-check-the-network-speed-in-android/)

**网速**可以定义为客户端和服务器每秒交换的数据包总数，通常以兆比特每秒(Mbps)计算。位不是 0 就是 1。1 兆位意味着 100 万位。通常，数据包大小取决于协议和各种其他因素，通常范围很广。在本文中，我们实现了一个程序，它以服务器的速度为我们获取**上传**和**下载**的速度。请注意，当设备连接到网络时，程序是成功的。

该程序可用于**研究**以及**优化:**

*   **研究:**人们可以导出内容和可用速度来关联网络依赖性。
*   **优化:**可以持续监控速度和上下文，避免在不需要时连接，或者根据当前速度降低正在广播的视频质量。

**进场:**

**第一步:**在安卓工作室创建一个空活动。创建一个，遵循这篇文章-[https://www . geeksforgeeks . org/Android-如何创建-启动-一个新的项目-在 android-studio/](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/) 。检查选择的主要语言是否为**科特林**。

**第二步:**转到 **AndroidManifest.xml** 文件，添加使用权限 **ACCESS_NETWORK_STATE** 。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="org.geeksforgeeks.networkspeed">

  <!--Add this permission-->
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
  <!----------------------->

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

**第三步:**在 activity_main.xml 中，添加一个按钮。下面是相同的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--Create a Button-->
    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Show Speed"
        android:layout_centerInParent="true"
        />

</RelativeLayout>
```

**第 4 步:**在 MainActivity.kt 中，添加下面的代码。setOnClickListener 添加了按钮，当点击该按钮时，会在屏幕上以祝酒词的形式显示上传速度和下载速度。

## 我的锅

```
package org.geeksforgeeks.networkspeed

import android.content.Context
import android.net.ConnectivityManager
import android.os.Build
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.Toast
import androidx.annotation.RequiresApi

class MainActivity : AppCompatActivity() {
    @RequiresApi(Build.VERSION_CODES.M)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declaring Button from the layout file
        val btn = findViewById<Button>(R.id.btn)

        // Action when the button id clicked
        btn.setOnClickListener {

            // Connectivity Manager
            val cm = applicationContext.getSystemService
          (Context.CONNECTIVITY_SERVICE) as ConnectivityManager

            // Network Capabilities of Active Network
            val nc = cm.getNetworkCapabilities(cm.activeNetwork)

            // DownSpeed in MBPS
            val downSpeed = (nc.linkDownstreamBandwidthKbps)/1000

            // UpSpeed  in MBPS
            val upSpeed = (nc.linkUpstreamBandwidthKbps)/1000

            // Toast to Display DownSpeed and UpSpeed
            Toast.makeText(applicationContext,
                           "Up Speed: $upSpeed Mbps \nDown Speed: $downSpeed Mbps",
                           Toast.LENGTH_LONG).show()
        }
    }
}
```

#### 输出:

<video class="wp-video-shortcode" id="video-498252-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201002150543/Screen-Recording-2020-10-02-at-14.42.30.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201002150543/Screen-Recording-2020-10-02-at-14.42.30.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201002150543/Screen-Recording-2020-10-02-at-14.42.30.mp4)</video>