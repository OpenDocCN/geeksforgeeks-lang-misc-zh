# 如何确定安卓系统中当前的坞站类型？

> 原文:[https://www . geesforgeks . org/如何确定当前的安卓入坞类型/](https://www.geeksforgeeks.org/how-to-determine-the-current-dock-type-in-android/)

**先决条件:** [如何检查安卓设备是否处于对接状态？](https://www.geeksforgeeks.org/how-to-check-if-the-android-device-is-in-dock-state/)

当安卓设备连接到电源或涉及充电和多媒体交换的计量交换系统时，它被称为对接设备。坞站状态与设备的充电状态密切相关。坞站状态提供了关于充电或连接类型的信息。安卓设备能够对接多种坞站。例如，当安卓设备通过兼容的通用串行总线电缆连接到家庭音乐系统等音乐系统时，它被称为停靠在高端桌面上。同样，当安卓设备连接到汽车充电器时，它会停靠在汽车中。所以基本上有**四个**不同类型的坞站:

1.  vehicle
2.  platform
3.  Low-end (analog) station
4.  High-end (digital) platform

> ***注:**低端(模拟)台和高端(数字)台是在 API 级引入安卓的。*

*   **Cardock:** Cardock is a docking center, which allows devices to charge and transmit media when connecting.

*   **Desk Dock:** A deskdock is a docking station. It is an interface device that allows portable computers to connect to other devices with little or no effort. The docking station enables mobile devices to turn it into a desktop computer in the office or home.

*   **Low-end station:** These terminals operate at low current. Example: Low output power group (< 1 amp)
*   **High-end stations:** These docking stations operate at higher current. For example: fast charger, high output power group (2.1 Amp)

因此，在本文中，让我们确定安卓系统中当前的坞站类型。注意，我们将使用**语言来实现这个项目。**

### **接近**

****第一步:创建新项目****

**要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。**

****步骤 2:使用 activity_main.xml 文件****

**与 **activity_main.xml** 文件无关。所以保持文件原样。**

## **XML**

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

****第三步:使用 MainActivity.kt 文件****

**转到**主活动. kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。**

 **## 科特林

```
import android.content.Intent
import android.content.IntentFilter
import android.os.Bundle
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // The dock-state details are included as an extra in a sticky broadcast of
        // the ACTION_DOCK_EVENT action. Because it's sticky, you can simply call
        // registerReceiver(), passing in null as the broadcast receiver.
        val dockStatus: Intent? = IntentFilter(Intent.ACTION_DOCK_EVENT).let { ifilter ->
            applicationContext.registerReceiver(null, ifilter)
        }

        // dockState is an Integer value received when intent is passed
        val dockState: Int = dockStatus?.getIntExtra(Intent.EXTRA_DOCK_STATE, -1) ?: -1

        // isDocked is a Boolean value which if true indicates
        // the device is in dock state and vice-versa
        val isDocked: Boolean = dockState != Intent.EXTRA_DOCK_STATE_UNDOCKED

        // isCar and isDesk are a Boolean values, 
        // either of which if true indicates
        // the device is in a particular dock
        val isCar: Boolean = dockState == Intent.EXTRA_DOCK_STATE_CAR
        val isDesk: Boolean = dockState == Intent.EXTRA_DOCK_STATE_DESK
                || dockState == Intent.EXTRA_DOCK_STATE_LE_DESK
                || dockState == Intent.EXTRA_DOCK_STATE_HE_DESK

        // Output Cases
        when {
            isCar -> Toast.makeText(applicationContext, "Dock CAR", Toast.LENGTH_SHORT).show()
            isDesk -> Toast.makeText(applicationContext, "Dock DESK", Toast.LENGTH_SHORT).show()
            !isDocked -> Toast.makeText(applicationContext, "Not Docked", Toast.LENGTH_SHORT).show()
        }
    }
}
```** 

**根据不同的状态，应用程序显示吐司消息，当设备停靠在汽车上时显示“停靠汽车”，如果停靠在桌子上则显示“停靠桌子”，否则显示“未停靠”。输出为**不可用**但这是安卓中提取 dock 状态的标准版本。**