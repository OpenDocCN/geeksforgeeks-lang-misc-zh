# 如何在安卓系统中编程启用/禁用 Wi-Fi？

> 原文:[https://www . geesforgeks . org/如何以编程方式启用-禁用-wi-fi-in-android/](https://www.geeksforgeeks.org/how-to-programmatically-enable-disable-wi-fi-in-android/)

在安卓手机中，通过使用 WiFi 图标来启用/禁用 WiFi 非常容易，但是你有没有想过如何在安卓中以编程方式完成这个任务。下面给出了一个 GIF 示例，来了解一下在本文中要做什么。请注意，我们将使用 **Kotlin** 语言来实现该项目。

![Sample WiFi](img/fe9a0020dad4115356d0c444bb1ae309.png)

### 以编程方式启用/禁用无线网络的步骤

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 AndroidManifest.xml 文件**

转到 **AndroidManifest.xml** 文件，添加两个用户权限: **ACCESS_WIFI_STATE** 和 **CHANGE_WIFI_STATE** 。

下面是 **AndroidManifest.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<manifest 
    xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.wifi">

    <!--Put the permissions between the manifest and application opening tags-->
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />

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

**步骤 3:使用 activity_main.xml 文件**

设置完成后，转到 **activity_main.xml** 文件，该文件代表项目的 UI。创建一个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)，通过点击改变无线网络的状态，创建一个[文本视图](https://www.geeksforgeeks.org/textview-in-kotlin/)，显示无线网络的状态。下面是 **activity_main.xml** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--Changes the state of Wi-Fi on button click-->
    <Button
        android:id="@+id/wifiSwitch"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Click" />

    <!--Displays the state of Wi-Fi on button click-->
    <TextView
        android:id="@+id/tv"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_above="@id/wifiSwitch"
        android:layout_centerHorizontal="true"
        android:hint="Wifi Status"
        android:textSize="30sp" />

</RelativeLayout>
```

**第 4 步:使用 MainActivity.kt 文件**

在 **MainActivity.kt** 文件中，声明按钮、文本视图和一个**无线管理器**(参考代码)。将点击监听器设置为按钮时，我们将使用无线管理器来启用或禁用无线。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.net.wifi.WifiManager
import android.os.Build
import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import androidx.annotation.RequiresApi
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    @RequiresApi(Build.VERSION_CODES.LOLLIPOP)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declaring Button and TextView
        // 1\. Changes the state of Wi-Fi on button click
        // 2\. Shows the state of the Wi-Fi
        val btn = findViewById<Button>(R.id.wifiSwitch)
        val textView = findViewById<TextView>(R.id.tv)

        // Declaring Wi-Fi manager
        val wifi = applicationContext.getSystemService(WIFI_SERVICE) as WifiManager

        // On button Click
        btn.setOnClickListener {

            // wifi.isWifiEnabled is a boolean, is Wi-Fi is ON, 
            // it switches down and vice-versa
            wifi.isWifiEnabled = !wifi.isWifiEnabled

            // For displaying Wi-fi status in TextView
            if (!wifi.isWifiEnabled) {
                textView.text = "Wifi is ON"
            } else {
                textView.text = "Wifi is OFF"
            }
        }
    }
}
```

### 输出:在模拟器上运行

<video class="wp-video-shortcode" id="video-494555-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001100044/Screen-Recording-2020-09-17-at-23.32.42.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001100044/Screen-Recording-2020-09-17-at-23.32.42.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001100044/Screen-Recording-2020-09-17-at-23.32.42.mp4)</video>