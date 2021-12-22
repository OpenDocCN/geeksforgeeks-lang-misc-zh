# 如何在安卓中编程检查飞机模式状态？

> 原文:[https://www . geesforgeks . org/如何检查-飞机-模式-安卓状态-编程/](https://www.geeksforgeeks.org/how-to-check-airplane-mode-state-in-android-programmatically/)

**飞行模式**经常出现在飞行过程中，避免通话，或者重启手机、平板电脑和笔记本电脑上的网络。飞机模式是设备关闭无线电通信的独立模式。这些可能包括无线网络、全球定位系统、电话网络、热点，具体取决于设备的制造年份、品牌和购买地点，但不包括蓝牙。支持流式传输的应用程序可能需要互联网连接，并且需要随时了解互联网连接的状态。虽然飞机模式会影响互联网连接，但此类应用程序需要替代方案来处理这种情况。通过本文，我们将向您展示如何以编程方式检查飞机模式状态。

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 **Kotlin** 中演示了该应用程序，因此在创建新项目时，请确保选择 Kotlin 作为主要语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** ，并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。在布局文件中创建一个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)。

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

    <Button
        android:id="@+id/Check"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Check"
        android:layout_centerInParent="true"/>

</RelativeLayout>
```

**第三步:使用**T2【主活动. kt】文件

转到**MainActivity.java**文件，参考以下代码。以下是**MainActivity.java**文件的代码。代码中添加了注释，以更详细地理解代码。以下是检查飞机模式状态的代码。

## 我的锅

```kt
import android.os.Build
import android.os.Bundle
import android.provider.Settings
import android.widget.Button
import android.widget.Toast
import androidx.annotation.RequiresApi
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    @RequiresApi(Build.VERSION_CODES.JELLY_BEAN_MR1)

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Find the button from the layout file
        // and add functionality to it
        val btn = findViewById<Button>(R.id.Check)
        btn.setOnClickListener {

            // Get the value of AIRPLANE MODE 
            // from the system settings.
            // This is an Integer. Airplane Mode 
            // is ON is its 1 and 0 otherwise.
            // Toast the message (off/on)
            if(Settings.System.getInt(contentResolver, Settings.Global.AIRPLANE_MODE_ON, 0) == 0){
                Toast.makeText(applicationContext,"Off",Toast.LENGTH_SHORT).show()
            } else {
                Toast.makeText(applicationContext,"On",Toast.LENGTH_SHORT).show()
            }
        }
    }
}
```

**输入:**

检查飞机模式是否关闭。现在点击按钮。我们会得到一个信息，说它已经关了。现在打开飞机模式。返回活动并再次单击按钮。我们将得到一个信息，它已经打开了。

**输出:**

<video class="wp-video-shortcode" id="video-646477-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210713145032/1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210713145032/1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210713145032/1.mp4)</video>

**有用提示:**

请注意，我们**不能通过编程改变**飞机模式的状态。只有在应用程序是系统应用程序的情况下，我们才能更改它。这可以通过在清单文件中添加写设置的权限并在**设置中调用 putInt()函数来实现。系统**。