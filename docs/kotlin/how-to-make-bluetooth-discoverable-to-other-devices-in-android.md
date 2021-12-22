# 如何让蓝牙在安卓系统中被其他设备发现？

> 原文:[https://www . geeksforgeeks . org/如何在安卓系统中让其他设备发现蓝牙/](https://www.geeksforgeeks.org/how-to-make-bluetooth-discoverable-to-other-devices-in-android/)

在安卓设备中，**蓝牙**是一种通信网络协议，允许设备无线连接，与其他蓝牙设备交换数据。一般来说，我们可以利用蓝牙应用编程接口来实现蓝牙功能，例如启用或禁用蓝牙、搜索可用的蓝牙设备、与设备连接以及管理范围内设备之间的数据传输。在安卓系统中，**蓝牙适配器**类执行所有蓝牙相关的活动。默认情况下，蓝牙设备处于无法发现的模式。这意味着，如果我们打开设备中的蓝牙，它只对之前与之配对的人可见。该设备在配对设备以外的设备上不可见。要使该设备可见，我们打开“可发现”选项，这将使该设备对其附近区域是全局的。无论是新设备还是早期配对的设备，该设备现在都会出现在每个列表中。涉及音乐设备或数字手表(通过蓝牙传输同步)与其他设备配对的应用程序非常简单。这些设备被设置为全局设备，任何其他设备都可以发现它们。要在安卓手机上实现这一点，可以进入蓝牙设置，使其成为全局或可发现的。本文想与您分享一个应用程序的实现，当蓝牙打开时，该应用程序使设备的蓝牙可被发现。下面给出一个 GIF 示例，了解一下在这篇 文章中我们要做什么。注意，我们将使用 **Kotlin** 语言来实现这个项目。

![Make Bluetooth Discoverable to Other Devices ](img/b44bef414b38df95f3040f2cf0384d47.png)

### 履行

*   本文中解释的应用程序基本上是为了测试我们是否可以通过编程调用方法来实现我们的目的。
*   我们创建了一个由三个按钮组成的安卓移动应用程序；**开启，可发现，**和**关闭**，让功能调用各种蓝牙适配器方法。
*   此应用程序的更改是全局的，即如果没有单击关闭按钮，蓝牙将继续打开，或者任何其他相关版本。
*   要使设备在其他设备列表中可被发现，必须使用**动作 _ 请求 _ 可被发现**意图，使用**开始活动或结果(意图，int)** 初始化新活动。

> **注意:**蓝牙存在并处于开机模式以使其可被发现是很重要的。

### **分步实施**

要在安卓系统中根据我们的设备以编程方式显示蓝牙配对设备列表，请执行以下步骤:

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:使用 AndroidManifest.xml 文件**

转到 **AndroidManifest.xml** 文件，添加蓝牙适配器所需的这些权限: **BLUETOOTH，BLUETOOTH_ADMIN，**和**ACCESS _ rough _ LOCATION**。

> *<用途-权限安卓:name=“安卓.权限.蓝牙”/ >*
> 
> *<使用-权限安卓:name=“安卓.权限.蓝牙 _ ADMIN”/>*
> 
> *<使用-权限安卓:name = " Android . permission . access _ rough _ LOCATION "/>*

以下是 **和** 文件的完整代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="org.geeksforgeeks.bluetoothdiscoverable">

    <!--Permissions Required for accessing Bluetooth services-->
    <uses-permission android:name="android.permission.BLUETOOTH"/>
    <uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>

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

现在转到代表应用程序用户界面的 **activity_main.xml** 文件。创建三个**按钮**，一个用于打开设备的蓝牙，一个用于使设备的蓝牙在其他设备上可被发现，一个用于关闭蓝牙服务。下面是**activity _ main . XML**文件的代码。代码中添加了注释，以更详细地理解代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingLeft="10dp"
    android:paddingRight="10dp">

    <!--Turn ON Button-->
    <Button
        android:id="@+id/btnOn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toLeftOf="@id/btnDiscoverable"
        android:text="Turn ON" />

    <!--Discoverable Button-->
    <Button
        android:id="@+id/btnDiscoverable"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:text="Discoverable" />

    <!--Turn OFF Button-->
    <Button
        android:id="@+id/btnOFF"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@+id/btnDiscoverable"
        android:text="Turn OFF" />

</RelativeLayout>
```

**第 4 步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.bluetooth.BluetoothAdapter
import android.content.Intent
import android.os.Bundle
import android.widget.Button
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare the three buttons from the layout file
        val btnOn = findViewById<Button>(R.id.btnOn)
        val btnOff = findViewById<Button>(R.id.btnOFF)
        val btnDisc = findViewById<Button>(R.id.btnDiscoverable)

        // Initialize the Bluetooth Adapter
        val bAdapter = BluetoothAdapter.getDefaultAdapter()

        // Action when Turn ON Button is clicked
        btnOn.setOnClickListener {

            // If Bluetooth support or API is absent or private in the device
            if (bAdapter == null) {
                Toast.makeText(applicationContext, "Bluetooth Not Supported", Toast.LENGTH_SHORT).show()
            } else {

                // Turn ON the Bluetooth using an Intent and making a Toast Message
                if (!bAdapter.isEnabled) {
                    startActivityForResult(Intent(BluetoothAdapter.ACTION_REQUEST_ENABLE), 1)
                    Toast.makeText(applicationContext, "Bluetooth Turned ON", Toast.LENGTH_SHORT).show()
                }
            }
        }

        // Action when Turn OFF Button is clicked
        btnOff.setOnClickListener {
            // Disable the Bluetooth Adapter and make a Toast
            bAdapter!!.disable()
            Toast.makeText(applicationContext, "Bluetooth Turned OFF", Toast.LENGTH_SHORT).show()
        }

        // Action when Discoverable Button is clicked
        btnDisc.setOnClickListener {
            // Make the Bluetooth in a Discovering State and make a Toast
            if (!bAdapter!!.isDiscovering) {
                startActivityForResult(Intent(BluetoothAdapter.ACTION_REQUEST_DISCOVERABLE), 1)
                Toast.makeText(applicationContext, "Making Device Discoverable", Toast.LENGTH_SHORT).show()
            }
        }
    }
}
```

### **输出:在物理设备上运行**

输出视频中输入事件的顺序如下:

1.  打开点击(打开蓝牙并检查按钮是否工作)
2.  关闭点击(关闭蓝牙并检查按钮是否工作)
3.  打开点击(再次打开蓝牙)
4.  可发现点按(使设备的蓝牙可被发现)
5.  关闭点击(关闭蓝牙)

<video class="wp-video-shortcode" id="video-502057-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201016133759/2020_10_16_12_54_10_trim2.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201016133759/2020_10_16_12_54_10_trim2.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201016133759/2020_10_16_12_54_10_trim2.mp4)</video>

### **设置自定义发现时间**

默认情况下，设备处于发现模式 120 秒**。我们可以通过使用 putExtra 为意图提供一个特定的值来更改该值:**

## **我的锅**

```kt
startActivityForResult(Intent
                       (BluetoothAdapter.ACTION_REQUEST_DISCOVERABLE)
                       .putExtra(BluetoothAdapter.EXTRA_DISCOVERABLE_DURATION, 40)
                       , 1)
```

**这会将默认值更改为 **40 秒**。**