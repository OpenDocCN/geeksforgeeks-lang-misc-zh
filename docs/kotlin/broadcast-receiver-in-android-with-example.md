# 安卓广播接收器示例

> 原文:[https://www . geesforgeks . org/broadcast-带示例的安卓接收器/](https://www.geeksforgeeks.org/broadcast-receiver-in-android-with-example/)

安卓系统中的广播是指当设备启动时、当设备收到消息时、当收到来电时、或者当设备进入飞机模式时等可能发生的全系统事件。广播接收器用于响应这些全系统事件。广播接收器允许我们注册系统和应用程序事件，当事件发生时，注册接收器会收到通知。主要有两种类型的广播接收器:

*   **静态广播接收器:**这些类型的接收器在清单文件中声明，即使应用程序关闭也能工作。
*   **动态广播接收器:**这些类型的接收器只有在应用程序处于活动状态或最小化时才能工作。

由于从 API Level 26 开始，大部分广播只能被动态接收器捕获，因此我们在下面给出的示例项目中实现了动态接收器。意图类中定义了一些静态字段，可以用来广播不同的事件。我们将飞机模式的改变视为广播事件，但是有许多事件可以使用广播寄存器。以下是一些重要的全系统生成意图

<figure class="table">

| 

意图

 | 

事件描述

 |
| --- | --- |
| 安卓.意图.行动.电池 _ 低: | 表示设备电池电量不足。 |
| Android . intent . action . BOOT _ COMPLETED | 这将在系统完成引导后广播一次 |
| 安卓.意图.行动.呼叫 | 给数据指定的人打电话 |
| Android . intent . action . DATE _ CHANGED | 指示日期已更改 |
| 安卓。意图。行动。重启 | 表示设备已经重新启动 |
| Android . net . conn . CONNECTION _ CHANGE | 移动网络或 wifi 连接已更改(或重置) |
| 安卓.意图.行动 _ 飞机 _ 模式 _ 已更改 | 这表明飞机模式已经打开或关闭。 |

</figure>

为了在我们的应用中使用广播接收器，我们必须做的两件主要事情是:

**创建广播接收器:**

> 类 AirplaneModeChangeReceiver:BroadcastReceiver(){ 0
> 
> 覆盖娱乐(上下文:上下文？，意图:意图？) {
> 
> //代码的逻辑需要写在这里
> 
> }
> 
> }

**注册广播接收器:**

> 意图过滤器(意图。动作 _ 飞机 _ 模式 _ 已更改)。另请参见
> 
> //接收器是我们注册的广播接收器
> 
> //这是我们创建的意图过滤器
> 
> 注册接收器
> 
> }

### 例子

下面是示例项目，展示了如何创建广播接收器，如何为特定事件注册它们，以及如何在应用程序中使用它们。

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。

**步骤 2:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
</androidx.constraintlayout.widget.ConstraintLayout>
```

**步骤 3:使用主活动文件**

转到**主活动**文件，参考以下代码。以下是**主活动**文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.content.Intent
import android.content.IntentFilter
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    // register the receiver in the main activity in order
    // to receive updates of broadcasts events if they occur
    lateinit var receiver: AirplaneModeChangeReceiver
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        receiver = AirplaneModeChangeReceiver()

        // Intent Filter is useful to determine which apps wants to receive
        // which intents,since here we want to respond to change of
        // airplane mode
        IntentFilter(Intent.ACTION_AIRPLANE_MODE_CHANGED).also {
            // registering the receiver
            // it parameter which is passed in  registerReceiver() function
            // is the intent filter that we have just created
            registerReceiver(receiver, it)
        }
    }

    // since AirplaneModeChangeReceiver class holds a instance of Context
    // and that context is actually the activity context in which
    // the receiver has been created
    override fun onStop() {
        super.onStop()
        unregisterReceiver(receiver)
    }
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.content.IntentFilter;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    AirplaneModeChangeReceiver airplaneModeChangeReceiver = new AirplaneModeChangeReceiver();

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    protected void onStart() {
        super.onStart();
        IntentFilter filter = new IntentFilter(Intent.ACTION_AIRPLANE_MODE_CHANGED);
        registerReceiver(airplaneModeChangeReceiver, filter);
    }

    @Override
    protected void onStop() {
        super.onStop();
        unregisterReceiver(airplaneModeChangeReceiver);
    }
}
```

**第四步:新建一个类**

转到 **app > java >您的包名(其中有 mainactivity)>右键单击>新建> Kotlin 文件/类**，并将文件命名为**airlanemodechangereceiver**。以下是**飞机模式变更接收器**文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.content.BroadcastReceiver
import android.content.Context
import android.content.Intent
import android.widget.Toast

// AirplaneModeChangeReceiver class extending BroadcastReceiver class
class AirplaneModeChangeReceiver : BroadcastReceiver() {

    // this function will be excecuted when the user changes his
    // airplane mode
    override fun onReceive(context: Context?, intent: Intent?) {

        // intent contains the information about the broadcast
        // in our case broadcast is change of airplane mode

        // if getBooleanExtra contains null value,it will directly return back
        val isAirplaneModeEnabled = intent?.getBooleanExtra("state", false) ?: return

        // checking whether airplane mode is enabled or not
        if (isAirplaneModeEnabled) {
            // showing the toast message if airplane mode is enabled
            Toast.makeText(context, "Airplane Mode Enabled", Toast.LENGTH_LONG).show()
        } else {
            // showing the toast message if airplane mode is disabled
            Toast.makeText(context, "Airplane Mode Disabled", Toast.LENGTH_LONG).show()
        }
    }
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.provider.Settings;
import android.widget.Toast;

public class AirplaneModeChangeReceiver extends BroadcastReceiver {

    @Override
    public void onReceive(Context context, Intent intent) {

        if (isAirplaneModeOn(context.getApplicationContext())) {
            Toast.makeText(context, "AirPlane mode is on", Toast.LENGTH_SHORT).show();
        } else {
            Toast.makeText(context, "AirPlane mode is off", Toast.LENGTH_SHORT).show();
        }
    }

    private static boolean isAirplaneModeOn(Context context) {
        return Settings.System.getInt(context.getContentResolver(), Settings.Global.AIRPLANE_MODE_ON, 0) != 0;
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-507439-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201031202726/Broadcast_Receiver_Output.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201031202726/Broadcast_Receiver_Output.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201031202726/Broadcast_Receiver_Output.mp4)</video>