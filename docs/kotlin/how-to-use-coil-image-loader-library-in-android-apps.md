# 如何在安卓应用中使用 COIL 图像加载器库？

> 原文:[https://www . geesforgeks . org/如何使用-线圈-图像-加载器-安卓库中-应用/](https://www.geeksforgeeks.org/how-to-use-coil-image-loader-library-in-android-apps/)

**COIL** 是 **Coroutine 图像加载器的首字母缩写。** COIL 是安卓中著名的从 URL 加载图像的库之一。这是一个用于从服务器加载图像的现代库。该库用于从服务器、资产文件夹以及安卓项目中的可绘制文件夹加载图像。这个库的重要特点是快速、轻量、易用。在本文中，我们将看到**如何在安卓应用程序**中使用这个图像加载器库。

### 为什么我们应该使用线圈加载图像？

COIL 图像加载库由 [Kotlin Coroutines](https://www.geeksforgeeks.org/kotlin-coroutines-on-android/) 提供，用于在安卓中加载图像。这个库是专门为在 Kotlin 中加载图像而设计的。它是现代的，易于使用，重量轻，从服务器加载图像快。这是一个新的库，为从服务器非常高效地加载图像提供了新的优化。由于 Kotlin 现在被官方宣布为安卓开发的首选语言，这就是为什么在加载图像时，我们应该更喜欢在安卓系统中使用 COIL 来加载图像。

### 与毕加索、格莱德和 UIL 相比，使用 COIL 有什么优势？

*   谷歌已经正式宣布 Kotlin 为安卓开发的首选语言，而 COIL 是用 Kotlin 更好优化的库。因此，使用 Kotlin 对这个库进行优化，可以更容易地从服务器加载图像。
*   COIL 加载图像的速度非常快，优化包括内存、磁盘缓存、位图重用和在内存中缩小图像间距，与其他图像加载库相比速度更快。
*   COIL 为你的 APK 增加了 **~2000 种方法**，与[毕加索](https://www.geeksforgeeks.org/image-loading-caching-library-android-set-1/)[格莱德](https://www.geeksforgeeks.org/image-loading-caching-library-android-set-2/)和 [UIL](https://www.geeksforgeeks.org/how-to-use-universal-image-loader-library-in-android/) 相比，数量少了很多。这使得这个库非常轻量级并且易于使用。
*   COIL 是第一个在 Kotlin 中完全引入的图像加载库，它使用了一些 Android 的现代库，如 Okio、OkHttp 和 AndroidX 生命周期。

### 线圈图像加载库的分步实现

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:在 build.gradle 文件**中添加线圈图像加载库的依赖关系

导航到梯度脚本，然后导航到构建.梯度(模块)级别。在 dependencies 部分的 build.gradle 文件中添加以下行。

> 实现(“io.coil-kt:coil:1.1.0”)

添加依赖项后，单击右上角的“立即同步”选项来同步项目。

**第三步:在 AndroidManifest.xml 文件**中添加互联网权限

导航至**应用程序>清单**打开清单文件。在清单文件中，我们添加了从互联网加载图像的互联网权限。在清单文件中添加以下行。

**第 4 步:在 activity_main.xml.** 中创建新的 ImageView

导航到**应用程序> res >布局**打开 **activity_main.xml** 文件。下面是 **activity_main.xml** 文件的代码。

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

    <!--ImageView is created below-->
    <ImageView
        android:id="@+id/imageView"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerInParent="true"
        android:contentDescription="@string/app_name" />

</RelativeLayout>
```

**步骤 5:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.ImageView
import coil.load

class MainActivity : AppCompatActivity() {

    // image url that we will load in our image view. 
    val imgurl = "https://www.geeksforgeeks.org/wp-content/uploads/gfg_200X200-1.png"

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

          // val created for our imageview and 
          // initializing it with image id. 
        val img = findViewById<ImageView>(R.id.imageView)

          // below line is for loading 
          // image url inside imageview.
        img.load(imgurl) {
            // placeholder image is the image used 
              // when our image url fails to load. 
            placeholder(R.drawable.ic_launcher_background)
        }
    }
}
```

### 输出:

![COIL Image Loader Library Output](img/e22045630503dfac60177d84e9c07d7a.png)