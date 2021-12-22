# 如何在安卓中编程检查 GPS 是开还是关？

> 原文:[https://www . geesforgeks . org/如何在安卓系统中以编程方式检查 gps 是打开还是关闭/](https://www.geeksforgeeks.org/how-to-check-gps-is-on-or-off-in-android-programmatically/)

**GPS(全球定位系统)**是一种基于卫星的导航系统，可容纳卫星和设备之间的无线电信号，以坐标形式处理设备的位置。全球定位系统给出了设备的纬度和经度值。最近的手机配备了全球定位系统模块，可以在谷歌地图等软件上知道它们的确切位置。然而，全球定位系统数据被用于许多其他应用程序来寻找该设备，显示与该地理位置相关的新闻，以及许多其他应用程序。

![](img/a9178e495003fc91da95457fc7aa10c6.png)

本文将向您展示如何通过编程检查安卓设备中的全球定位系统是启用还是禁用。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 **Kotlin** 中演示了该应用程序，因此在创建新项目时，请确保选择 Kotlin 作为主要语言。

**第二步:在 AndroidManifest.xml** 中添加权限

## 可扩展标记语言

```
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
```

**步骤 3:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** ，并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。在布局文件中添加一个[文本视图](https://www.geeksforgeeks.org/textview-in-kotlin/)和一个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)。按钮触发时，如果全球定位系统启用或禁用，文本视图将显示。

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

    <TextView
        android:id="@+id/text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:text="Hello Geek!"
        android:layout_above="@+id/button"/>

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Click"/>

</RelativeLayout>
```

**第 4 步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.content.Context
import android.location.LocationManager
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import android.widget.Button
import android.widget.TextView
import android.widget.Toast
import java.util.concurrent.Executors

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declaring TextView and Button from the layout file
        val mTextView = findViewById<TextView>(R.id.text_view)
        val mButton = findViewById<Button>(R.id.button)

        // What happens when button is clicked
        mButton.setOnClickListener {
              // Calling Location Manager
            val mLocationManager = getSystemService(Context.LOCATION_SERVICE) as LocationManager

              // Checking GPS is enabled
              val mGPS = mLocationManager.isProviderEnabled(LocationManager.GPS_PROVIDER)

              // Display the message into the string
              mTextView.text = mGPS.toString()
        }

    }
}
```

**输出:**

您可以看到，当点击按钮时，全球定位系统的状态显示在文本视图中。

<video class="wp-video-shortcode" id="video-684146-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210816203659/o102.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210816203659/o102.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210816203659/o102.mp4)</video>