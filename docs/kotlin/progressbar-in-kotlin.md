# 科特林的进度条

> 原文:[https://www.geeksforgeeks.org/progressbar-in-kotlin/](https://www.geeksforgeeks.org/progressbar-in-kotlin/)

Android ProgressBar 是一个用户界面控件，用于指示操作的进度。比如下载一个文件，在网上上传一个文件我们可以看到进度条来估算剩余的运行时间。ProgressBar 有两种模式:

*   确定进度栏
*   不确定进度栏

### **确定进度栏**

通常，我们在 ProgressBar 中使用确定进度模式，因为它显示已经发生的进度数量，如下载文件的百分比(%)，在互联网上上传或下载了多少数据等。如果我们必须使用确定，我们将进度条的样式设置如下:

## 可扩展标记语言

```kt
<ProgressBar
    android:id="@+id/pBar"
    style="?android:attr/progressBarStyleHorizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

### **不确定进度条**

在这里，我们不知道工作进度意味着已经完成了多少，或者需要多长时间才能完成。
我们可以通过将不定属性设置为 true 来使用如下的不定 progressBar。

## 可扩展标记语言

```kt
<ProgressBar
    android:id="@+id/pBar"
    style="?android:attr/progressBarStyleHorizontal"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:indeterminate="true"/>
```

### 进度条小部件的不同属性

<figure class="table">

| 

XML 属性

 | 

描述

 |
| --- | --- |
| android:id | 用于唯一标识控件 |
| android:min | 用于设置最小值 |
| android:最大 | 用于设置最大值 |
| 安卓:进步 | 用于设置 0 到最大值之间的默认进度整数值。 |
| android:minHeight | 用于设置进度条的高度。 |
| 安卓:minWidth | 用于设置进度条的宽度。 |
| 安卓:背景 | 用于设置进度条的背景颜色 |
| 安卓:不确定 | 用于启用不确定进度模式。 |
| 安卓:填充 | 用于设置进度条左侧、右侧、顶部或底部的填充。 |

</figure>

### 在 activity_main.xml 文件中添加 ProgressBar 小部件

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!-- adding progress bar -->
    <ProgressBar
        android:id="@+id/progress_Bar"
        style="?android:attr/progressBarStyle"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:layout_marginLeft="70dp"
        android:layout_marginTop="150dp"
        android:indeterminate = "true"
        android:max="100"
        android:minWidth="200dp"
        android:minHeight="50dp"
        android:visibility="invisible"
        android:layout_centerInParent="true"
        android:progress="0"
        android:layout_marginStart="70dp" />

    <!-- adding textview which will show the progress -->
    <TextView
        android:id="@+id/text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@+id/progress_Bar"
        android:layout_centerHorizontal="true" />

     <!-- adding button to start the progress -->
    <Button
        android:id="@+id/show_button"
        android:layout_width="191dp"
        android:layout_height="wrap_content"
        android:layout_below="@+id/text_view"
        android:layout_marginLeft="70dp"
        android:layout_marginTop="20dp"
        android:text="Progress Bar"
        android:layout_centerHorizontal="true"
        android:layout_marginStart="70dp" />

</RelativeLayout>
```

### 访问 MainActivity.kt 文件中的 ProgressBar 小部件

## 我的锅

```kt
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.ProgressBar
import android.widget.TextView
import android.os.Handler

class MainActivity : AppCompatActivity() {

    private var progressBar: ProgressBar? = null
    private var i = 0
    private var txtView: TextView? = null
    private val handler = Handler()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // finding progressbar by its id
        progressBar = findViewById<ProgressBar>(R.id.progress_Bar) as ProgressBar

        // finding textview by its id
        txtView = findViewById<TextView>(R.id.text_view)

        // finding button by its id
        val btn = findViewById<Button>(R.id.show_button)

        // handling click on button
        btn.setOnClickListener {
            // Before clicking the button the progress bar will invisible
            // so we have to change the visibility of the progress bar to visible
            // setting the progressbar visibility to visible
            progressBar.visibility = View.VISIBLE

            i = progressBar.progress

            Thread(Runnable {
                // this loop will run until the value of i becomes 99
                while (i < 100) {
                    i += 1
                    // Update the progress bar and display the current value
                    handler.post(Runnable {
                        progressBar.progress = i                       
                        // setting current progress to the textview
                        txtView!!.text = i.toString() + "/" + progressBar.max
                    })
                    try {
                        Thread.sleep(100)
                    } catch (e: InterruptedException) {
                        e.printStackTrace()
                    }
                }

                // setting the visibility of the progressbar to invisible
                // or you can use View.GONE instead of invisible
                // View.GONE will remove the progressbar
                progressBar.visibility = View.INVISIBLE

            }).start()
        }
    }
}
```

### AndroidManifest.xml 文件

## 可扩展标记语言

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

### 输出:

<video class="wp-video-shortcode" id="video-348384-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210707120803/1625639475757.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210707120803/1625639475757.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210707120803/1625639475757.mp4)</video>