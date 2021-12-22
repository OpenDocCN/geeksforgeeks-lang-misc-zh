# 安卓传感器示例

> 原文:[https://www.geeksforgeeks.org/android-sensors-with-example/](https://www.geeksforgeeks.org/android-sensors-with-example/)

在我们的童年，我们都玩过很多安卓游戏，比如 Moto Racing 和 Temple run，其中通过倾斜手机来改变角色的位置。所以，所有这些都是因为你的安卓设备中的传感器。大多数安卓设备都有内置传感器，可以测量运动、方向和各种环境条件。安卓传感器可用于监控三维设备移动或设备环境的变化，如光线、接近度、旋转、移动、磁场等。

### **传感器类型**

1.  **运动传感器:**这些传感器测量沿三个轴的加速力和旋转力。这一类别包括加速度计、重力传感器、陀螺仪和旋转矢量传感器。
2.  **位置传感器:**这些传感器测量设备的物理位置。这一类别包括方位传感器和磁力计。
3.  **环境传感器:**这些传感器测量各种环境参数，如环境空气温度和压力、光照和湿度。这一类别包括气压计、光度计和温度计。

### **安卓传感器 API**

我们可以使用安卓传感器应用编程接口收集原始传感器数据。安卓传感器 API 提供了很多类和接口。一些重要的类和接口是:

1.  **传感器管理器类:**传感器管理器用于访问设备中存在的各种传感器。
2.  **传感器类别:**传感器类别用于获取传感器的信息，如传感器名称、传感器类型、传感器分辨率、传感器类型等。
3.  **SensorEvent 类:**该类用于查找传感器的相关信息。
4.  **SensorEventListener 界面:**用于在传感器精度发生变化时执行一些动作。

### **示例:光传感器 App**

这个应用程序将在手机中的光传感器的帮助下显示我们房间的光线强度。

### **分步实施**

**第一步:在你的安卓工作室创建一个新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 XML 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。

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

      <!-- Textview to show ligt sensor reading -->
    <TextView
        android:id="@+id/tv_text"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Light Sensor"
        android:textSize="20sp"
        android:textColor="@color/black"
        android:layout_centerInParent="true" />

</RelativeLayout>
```

**第三步:使用 MainActivity.kt**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
package com.mrtechy.gfg_sensor

import android.hardware.Sensor
import android.hardware.SensorEvent
import android.hardware.SensorEventListener
import android.hardware.SensorManager
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.TextView
import androidx.appcompat.app.AppCompatDelegate

class MainActivity : AppCompatActivity(), SensorEventListener {

      // Initialised sensorManager & two variables
      // for storing brightness value
    private lateinit var sensorManager: SensorManager
    private var brightness: Sensor? = null
    private lateinit var text: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Set default nightmode
        AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_NIGHT_NO)

        // searched our textview id and stored it
        text = findViewById(R.id.tv_text)

        // setupSensor Called
        setUpSensor()
    }

    // Declared setupSensor function
    private fun setUpSensor() { 
      sensorManager = getSystemService(SENSOR_SERVICE) as SensorManager
      brightness = sensorManager.getDefaultSensor(Sensor.TYPE_LIGHT)
    }

    // These are two methods from sensorEventListner Interface
    override fun onSensorChanged(event: SensorEvent?) {
        if (event?.sensor?.type == Sensor.TYPE_LIGHT) {
            val light1 = event.values[0]

            text.text = "Sensor: $light1\n${brightness(light1)}"
        }
    }
    override fun onAccuracyChanged(sensor: Sensor?, accuracy: Int) {
        return
    }

    // Created a function to show messages according to the brightness
    private fun brightness(brightness: Float): String {

        return when (brightness.toInt()) {
            0 -> "Pitch black"
            in 1..10 -> "Dark"
            in 11..50 -> "Grey"
            in 51..5000 -> "Normal"
            in 5001..25000 -> "Incredibly bright"
            else -> "This light will blind you"
        }
    }

    // This is onResume function of our app
    override fun onResume() {
        super.onResume()
        sensorManager.registerListener(this, brightness, SensorManager.SENSOR_DELAY_NORMAL)
    }

    // This is onPause function of our app
    override fun onPause() {
        super.onPause()
        sensorManager.unregisterListener(this)
    }
}
```

**输出:**

> **注意:** App 那些使用传感器只会在物理安卓设备上工作，不会在任何仿真器上工作。

<video class="wp-video-shortcode" id="video-704681-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20211027001048/Android-Sensors-with-Example.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20211027001048/Android-Sensors-with-Example.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20211027001048/Android-Sensors-with-Example.mp4)</video>