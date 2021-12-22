# 如何从 App 编程调整安卓手机音量？

> 原文:[https://www . geeksforgeeks . org/如何通过应用程序以编程方式调整安卓手机的音量/](https://www.geeksforgeeks.org/how-to-adjust-the-volume-of-android-phone-programmatically-from-the-app/)

如本文标题所述，让我们讨论如何通过应用程序以编程方式调整安卓手机的音量。基本上，控制应用程序中的音量意味着

*   在没有音量条用户界面的情况下增加或减少音量
*   使用音量条用户界面增加或减少音量
*   静音或取消静音设备

所以我们将逐步讨论这三个过程。注意，我们将使用 **Kotlin** 语言来实现这个项目。

### 在没有音量条用户界面的情况下增加或减少音量

要以编程方式控制安卓设备中的音量，请执行以下步骤:

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

设置完成后，转到 **activity_main.xml** 文件，该文件代表项目的 UI。创建两个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)，一个用于增加音量，另一个用于降低音量，一个在另一个下面。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/btnUp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_above="@+id/btnDown"
        android:text="+"
        />

    <Button
        android:id="@+id/btnDown"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="-"
        />

</RelativeLayout>
```

**第三步:使用 MainActivity.kt 文件**

在 **MainActivity.kt** 文件中，声明两个按钮和一个音频管理器(参考代码)。将点击式监听器设置为按钮时，我们将使用音频管理器来增加或降低音量。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.media.AudioManager
import android.os.Bundle
import android.widget.Button
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare Buttons
        val upBtn = findViewById<Button>(R.id.btnUp)
        val downBtn = findViewById<Button>(R.id.btnDown)

        // Declare an audio manager
        val audioManager = applicationContext.getSystemService(AUDIO_SERVICE) as AudioManager

        // At the click of upBtn
        upBtn.setOnClickListener {
            // ADJUST_RAISE = Raise the volume, FLAG_PLAY_SOUND = make a sound when clicked
            audioManager.adjustVolume(AudioManager.ADJUST_RAISE, AudioManager.FLAG_PLAY_SOUND)
        }
        // At the click of downBtn
        downBtn.setOnClickListener {
            // ADJUST_LOWER = Lowers the volume, FLAG_PLAY_SOUND = make a sound when clicked
            audioManager.adjustVolume(AudioManager.ADJUST_LOWER, AudioManager.FLAG_PLAY_SOUND)
        }
    }
}
```

### 输出:在模拟器上运行

<video class="wp-video-shortcode" id="video-494711-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001093704/Screen-Recording-2020-09-17-at-14.34.07.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001093704/Screen-Recording-2020-09-17-at-14.34.07.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001093704/Screen-Recording-2020-09-17-at-14.34.07.mp4)</video>

### 使用音量条用户界面增加或减少音量

我们唯一要做的改变就是传递参数 **AudioManager。将**音频管理器改为**。**主活动文件**中的**。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.content.Context
import android.media.AudioManager
import android.os.Bundle
import android.widget.Button
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare Buttons
        val upBtn = findViewById<Button>(R.id.btnUp)
        val downBtn = findViewById<Button>(R.id.btnDown)

        // Declare an audio manager
        val audioManager = applicationContext.getSystemService(Context.AUDIO_SERVICE) as AudioManager

        // At the click of upBtn
        upBtn.setOnClickListener {
            // ADJUST_RAISE = Raise the volume, FLAG_SHOW_UI = show changes made to volume bar
            audioManager.adjustVolume(AudioManager.ADJUST_RAISE, AudioManager.FLAG_SHOW_UI)
        }

        // At the click of downBtn
        downBtn.setOnClickListener {
            // ADJUST_LOWER = LOWER the volume, FLAG_SHOW_UI = show changes made to volume bar
            audioManager.adjustVolume(AudioManager.ADJUST_LOWER, AudioManager.FLAG_SHOW_UI)
        }
    }
}
```

### 输出:在模拟器上运行

可以看出，点击“+”时音量增大，同样点击“-”时音量减小。当手机完全静音时，可以在音量栏上看到变化。

<video class="wp-video-shortcode" id="video-494711-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001094109/Screen-Recording-2020-09-17-at-14.50.34.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20201001094109/Screen-Recording-2020-09-17-at-14.50.34.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001094109/Screen-Recording-2020-09-17-at-14.50.34.mp4)</video>

### 静音或取消静音设备

**步骤 1:使用 activity_main.xml 文件**

设置完成后，转到 **activity_main.xml** 文件，该文件代表项目的 UI。创建两个按钮，一个用于静音，另一个用于取消设备静音，一个在另一个的下方。下面是 **activity_main.xml** 文件的代码。

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

    <Button
        android:id="@+id/btnMute"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:text="Mute"
        android:layout_above="@+id/btnUnmute"
        />

    <Button
        android:id="@+id/btnUnmute"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Unmute"
        />

</RelativeLayout>
```

**步骤 2:使用 MainActivity.kt 文件**

在 **MainActivity.kt** 文件中，声明两个按钮和一个音频管理器(参考代码)。将点击式监听器设置为按钮时，我们将使用音频管理器来静音或取消静音设备。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.content.Context
import android.media.AudioManager
import android.os.Bundle
import android.widget.Button
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare Buttons
        val muteBtn = findViewById<Button>(R.id.btnMute)
        val unmuteBtn = findViewById<Button>(R.id.btnUnmute)

        // Declare an audio manager
        val audioManager = applicationContext.getSystemService(Context.AUDIO_SERVICE) as AudioManager

        muteBtn.setOnClickListener {
            // ADJUST_Mute = Mutes the device, FLAG_SHOW_UI = show changes made to volume bar
            audioManager.adjustVolume(AudioManager.ADJUST_MUTE, AudioManager.FLAG_SHOW_UI)
        }

        unmuteBtn.setOnClickListener {
            // ADJUST_Unmute = Unmutes the device, FLAG_SHOW_UI = show changes made to volume bar
            audioManager.adjustVolume(AudioManager.ADJUST_UNMUTE, AudioManager.FLAG_SHOW_UI)
        }
    }
}
```

### 输出:在模拟器上运行

<video class="wp-video-shortcode" id="video-494711-3" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001094609/Screen-Recording-2020-09-17-at-15.00.55.mp4?_=3">[https://media.geeksforgeeks.org/wp-content/uploads/20201001094609/Screen-Recording-2020-09-17-at-15.00.55.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001094609/Screen-Recording-2020-09-17-at-15.00.55.mp4)</video>