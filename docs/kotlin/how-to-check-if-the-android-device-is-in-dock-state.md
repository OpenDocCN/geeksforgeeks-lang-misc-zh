# 如何检查安卓设备是否处于 Dock 状态？

> 原文:[https://www . geeksforgeeks . org/如何检查安卓设备是否处于对接状态/](https://www.geeksforgeeks.org/how-to-check-if-the-android-device-is-in-dock-state/)

坞站是一种能够与安卓内核通信以触发坞站相关事件并修改坞站文件状态的设备。一个扩展坞可以让系统和应用程序做任何被编程的事情。一个例子是在停靠状态下显示不同的布局。它还可以打开一个音乐播放器应用程序，在桌面模式下自动播放音乐(如果它是这样编程的)，在汽车模式下打开一个地图/导航应用程序，等等。坞站模式在不同的手机上有所不同，但它通常会将您的手机变成桌面时钟、照片幻灯片显示查看器或音乐播放器。您也可以在接听电话时将其设置为免持话筒。该坞站内置于自放大扬声器或音乐盒中，或者是一个通过 USB 连接到计算机、充电器或家庭影院设备的独立单元。有些坞站使用 USB 充电，使用蓝牙播放音乐。这种模式在某些手机上可以检测到，包括许多三星手机，但不是在每部手机或每种版本的手机上都可以检测到。比如**三星 Galaxy S2、S3、S4 都有坞站模式**，但是 **S5 没有**。请检查您的手机功能，以确保您的手机配备了坞站模式。因此，在本文中，让我们讨论如何检查安卓设备是否处于坞站状态或其他情况。请注意，我们将使用 **Kotlin** 语言来实现该项目。

### 步骤至检查安卓设备是否处于对接状态

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，该文件代表应用程序的用户界面。创建一个按钮，点击该按钮可提供设备的停靠状态。下面是 **activity_main.xml** 文件的代码。

## XML

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--Button to check the Dock state-->
    <Button
        android:id="@+id/btnCheck"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="check" />

</RelativeLayout>
```

**第三步:使用 MainActivity.kt 文件**

以下是**主活动. kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 科特林

```kt
import android.content.Intent
import android.content.Intent.EXTRA_DOCK_STATE
import android.content.IntentFilter
import android.os.Bundle
import android.widget.Button
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Button which onclick gives dock info in the form of a Toast
        val btn = findViewById<Button>(R.id.btnCheck)
        btn.setOnClickListener {

            // The dock-state details are included as an extra in a sticky broadcast of
            // the ACTION_DOCK_EVENT action. Because it's sticky, you can simply call
            // registerReceiver(), passing in null as the broadcast receiver.
            val dockStatus: Intent? = IntentFilter(Intent.ACTION_DOCK_EVENT)
                    .let { ifilter ->
                        applicationContext.registerReceiver(null, ifilter)
                    }

            // dockState is an Integer value received when intent is passed
            val dockState: Int = dockStatus?.getIntExtra(EXTRA_DOCK_STATE, -1) ?: -1

            // isDocked is a Boolean value which if true indicates the device is in dock
            // state and vice-versa
            val isDocked: Boolean = dockState != Intent.EXTRA_DOCK_STATE_UNDOCKED

            // Finally depending upon the isDocked value display the Toasts
            if (isDocked) {
                Toast.makeText(applicationContext, "Docked", Toast.LENGTH_SHORT).show()
            } else {
                Toast.makeText(applicationContext, "Not Docked", Toast.LENGTH_SHORT).show()
            }
        }
    }
}
```

### 输出

根据不同的状态，应用程序显示吐司消息，当设备对接时显示“已对接”，否则显示“未对接”。输出为**不可用**但这是安卓中提取 dock 状态的标准版本。请注意，安卓设备可以对接成几种坞站。其中包括汽车或家用坞站以及数字和模拟坞站。坞站状态通常与充电状态密切相关，因为许多坞站为坞站设备供电。