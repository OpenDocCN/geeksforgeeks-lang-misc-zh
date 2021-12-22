# 如何以编程方式显示安卓设备中存在的传感器列表？

> 原文:[https://www . geesforgeks . org/如何以编程方式显示安卓设备中存在的传感器列表/](https://www.geeksforgeeks.org/how-to-display-the-list-of-sensors-present-in-an-android-device-programmatically/)

全球生产的所有安卓设备都带有内置传感器，可以测量运动、方向和各种环境条件。这些传感器通常通过为各种应用提供来自传感器的数据来促进安卓架构。例如，温度传感器提供设备的温度，从中获得的信息可用于关闭一些不需要的服务。这种传感器是一种通用类型，但广义上，传感器分为**三种**类型:

1.  **运动传感器:**运动传感器测量沿 x-y-z 三个轴的加速度和旋转力。运动传感器包括加速度计、重力传感器、陀螺仪和旋转矢量传感器。
2.  **环境传感器:**环境传感器测量各种环境参数，如压力、环境温度(室温)、照度(光线落在设备上)和湿度。它们包括气压计、光度计和温度计。
3.  **位置传感器:**位置传感器测量设备在空间中的物理位置。它们包括方位传感器和磁力计。

### 安卓设备中常见的传感器

一般来说，安卓 4.4 版(Kitkat)或更高版本上的任何安卓设备都有这些传感器:

1.  **加速度计**–硬件传感器–运动传感器
2.  **重力传感器**–基于程序(软件)–从用于重力计算的运动传感器获得的原始数据。
3.  **环境温度**–硬件传感器–环境传感器
4.  **陀螺仪**–硬件传感器–运动传感器
5.  **光传感器**–硬件传感器–环境传感器
6.  **方位传感器**–基于程序(软件)–从位置和运动传感器获得的原始数据
7.  **接近传感器**–硬件传感器–位置传感器

### 方法

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

转到代表应用程序用户界面的 **activity_main.xml** 文件，并在[滚动视图](https://www.geeksforgeeks.org/scrollview-in-android/)中创建一个[文本视图](https://www.geeksforgeeks.org/textview-in-kotlin/)，该视图将列出设备中存在的传感器。下面是**activity _ main . XML**文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<ScrollView
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--Text View that shall display the sensor information list-->
    <TextView
        android:id="@+id/tv"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true" />

</ScrollView>
```

**第 4 步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.content.Context
import android.hardware.Sensor
import android.hardware.SensorManager
import android.os.Bundle
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    // Information about Sensors present in the 
    // device is supplied by Sensor Manager of the device
    private lateinit var sensorManager: SensorManager

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Initialize the variable sensorManager
        sensorManager = getSystemService(Context.SENSOR_SERVICE) as SensorManager

        // getSensorList(Sensor.TYPE_ALL) lists all the sensors present in the device
        val deviceSensors: List<Sensor> = sensorManager.getSensorList(Sensor.TYPE_ALL)

        // Text View that shall display this list
        val textView = findViewById<TextView>(R.id.tv)

        // Converting List to String and displaying 
        // every sensor and its information on a new line
        for (sensors in deviceSensors) {
            textView.append(sensors.toString() + "\n\n")
        }
    }
}
```

### **输出:在仿真器上运行**

<video class="wp-video-shortcode" id="video-498047-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001130326/Screen-Recording-2020-09-28-at-12.50.45.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001130326/Screen-Recording-2020-09-28-at-12.50.45.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001130326/Screen-Recording-2020-09-28-at-12.50.45.mp4)</video>