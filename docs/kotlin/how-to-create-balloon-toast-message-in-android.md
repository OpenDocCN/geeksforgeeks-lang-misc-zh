# 如何在安卓中创建气球吐司消息？

> 原文:[https://www . geesforgeks . org/如何创建气球-吐司-安卓消息/](https://www.geeksforgeeks.org/how-to-create-balloon-toast-message-in-android/)

在本文中，我们将创建一个气球[吐司](https://www.geeksforgeeks.org/android-what-is-toast-and-how-to-use-it-with-examples/)。该库是大多数安卓应用程序中常用的流行功能之一。我们可以在大多数购物和消息应用程序中看到这一功能。借助该功能，您可以在任何应用程序中获得下一步操作的提示。在输出中，我们可以看到本文要做的事情。

<video class="wp-video-shortcode" id="video-590187-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210403114756/toastb.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210403114756/toastb.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210403114756/toastb.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目。](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)注意选择**科特林**作为编程语言。

**第二步:添加依赖和 JitPack 存储库**

导航到**渐变脚本>构建.渐变(模块:应用)**，并在依赖项部分添加以下依赖项。

> 实现' com . github . bepimenozzi:气球弹出:0.2.8 '

将 JitPack 存储库添加到构建文件中。将其添加到 allprojects{ }部分内存储库末尾的 root build.gradle 中。

> *所有项目{*
> 
> *存储库{*
> 
> *……*
> 
> *maven { URL " https://jitpack . io " }*
> 
> *}*
> 
> *}*

**步骤 3:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/samplegeeks"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="GeeksForGeeks"
        android:textColor="#E91E63"
        android:textSize="32sp"
        android:textStyle="bold" />

</LinearLayout>
```

**第 4 步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.graphics.Color
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import it.beppi.balloonpopuplibrary.BalloonPopup

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val bp = BalloonPopup.Builder(applicationContext, findViewById(R.id.samplegeeks))
                .text("Showing Balloon Toast")    // set the text displayed (String or resource)
                .timeToLive(5000)                 // Milliseconds before closing the popup. 0 = persistent
                .animation(BalloonPopup.BalloonAnimation.fade_and_scale)    // animation style used. Available:
                // pop, scale, fade, fade75
                // and all the possible combinations.
                // When fade75 is used (up to alpha .75) the view is slightly transparent
                .shape(BalloonPopup.BalloonShape.rounded_square)      // Circle (oval) or rounded square
                .bgColor(Color.CYAN)        // unused yet
                .fgColor(Color.RED)         // text color
                .textSize(20)               // text size
                .offsetX(10)                // offsets to move the position accordingly
                .offsetY(15)
                .positionOffset(510, 815)
                .drawable(R.drawable.bg_circle) // custom background drawable
                .show();
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-590187-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210403114756/toastb.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210403114756/toastb.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210403114756/toastb.mp4)</video>