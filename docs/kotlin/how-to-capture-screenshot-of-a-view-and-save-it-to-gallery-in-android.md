# 如何在安卓中抓取一个视图的截图并保存到图库？

> 原文:[https://www . geeksforgeeks . org/如何捕获-查看截图并保存到安卓图库/](https://www.geeksforgeeks.org/how-to-capture-screenshot-of-a-view-and-save-it-to-gallery-in-android/)

在本文中，我们将捕获视图的截图，并将图像存储在图库中。下面给出了一个示例视频，以了解我们将在本文中做什么。注意，我们将使用 **Kotlin** 语言来实现这个项目。

<video class="wp-video-shortcode" id="video-557099-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210208210909/capture_view_android_gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210208210909/capture_view_android_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210208210909/capture_view_android_gfg.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。请注意，选择**科特林**作为编程语言

**步骤 2:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。注意它有一个[材料卡片视图](https://www.geeksforgeeks.org/cardview-in-android-with-example/)，id 为**卡片 _ 视图**，我们将在本文中截图这个视图。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/parentLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    tools:context=".MainActivity">

    <com.google.android.material.card.MaterialCardView
        android:id="@+id/card_View"
        android:layout_width="match_parent"
        android:layout_height="300dp"
        android:layout_margin="20dp"
        android:elevation="10dp"
        app:cardBackgroundColor="@color/black"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="vertical">

            <ImageView
                android:layout_width="match_parent"
                android:layout_height="200dp"
                android:scaleType="center"
                android:src="@drawable/gfg" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_gravity="center"
                android:layout_marginTop="20dp"
                android:text="Geeks For Geeks"
                android:textColor="@color/white"
                android:textSize="20sp"
                android:textStyle="bold" />

        </LinearLayout>
    </com.google.android.material.card.MaterialCardView>

    <Button
        android:id="@+id/btn_capture"
        android:layout_width="wrap_content"
        android:layout_height="50dp"
        android:layout_marginTop="20dp"
        android:backgroundTint="#0F9D58"
        android:text="Capture View"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/card_View" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第三步。在清单中添加权限。**

转到 **AndroidManifest.xml** 文件和以下代码。它有两个权限读取和写入外部存储。在**应用程序**标签中，它有**安卓系统:usesCleartextTraffic =“true”。**

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<manifest 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.geeksforgeeks.captureview">

    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission
        android:name="android.permission.WRITE_EXTERNAL_STORAGE"
        tools:ignore="ScopedStorage" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.CaptureView"
        android:usesCleartextTraffic="true">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

**第 4 步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.Manifest
import android.content.ContentValues
import android.graphics.Bitmap
import android.graphics.Canvas
import android.net.Uri
import android.os.Build
import android.os.Bundle
import android.os.Environment
import android.provider.MediaStore
import android.util.Log
import android.view.View
import android.widget.Button
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.cardview.widget.CardView
import androidx.core.app.ActivityCompat
import java.io.File
import java.io.FileOutputStream
import java.io.OutputStream

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // write permission to access the storage
        ActivityCompat.requestPermissions(this, arrayOf(Manifest.permission.WRITE_EXTERNAL_STORAGE), 1)
        ActivityCompat.requestPermissions(this, arrayOf(Manifest.permission.READ_EXTERNAL_STORAGE), 1)

        // this is the card view whose screenshot
          // we will take in this article
        // get the view using fin view bt id
        val cardView = findViewById<CardView>(R.id.card_View)

        // on click of this button it will capture 
          // screenshot and save into gallery
        val captureButton = findViewById<Button>(R.id.btn_capture)
        captureButton.setOnClickListener {
            // get the bitmap of the view using 
              // getScreenShotFromView method it is
            // implemented below
            val bitmap = getScreenShotFromView(cardView)

            // if bitmap is not null then 
              // save it to gallery
            if (bitmap != null) {
                saveMediaToStorage(bitmap)
            }
        }

    }

    private fun getScreenShotFromView(v: View): Bitmap? {
        // create a bitmap object
        var screenshot: Bitmap? = null
        try {
            // inflate screenshot object 
             // with Bitmap.createBitmap it 
              // requires three parameters
            // width and height of the view and
              // the background color
            screenshot = Bitmap.createBitmap(v.measuredWidth, v.measuredHeight, Bitmap.Config.ARGB_8888)
            // Now draw this bitmap on a canvas
            val canvas = Canvas(screenshot)
            v.draw(canvas)
        } catch (e: Exception) {
            Log.e("GFG", "Failed to capture screenshot because:" + e.message)
        }
        // return the bitmap
        return screenshot
    }

    // this method saves the image to gallery
    private fun saveMediaToStorage(bitmap: Bitmap) {
        // Generating a file name
        val filename = "${System.currentTimeMillis()}.jpg"

        // Output stream
        var fos: OutputStream? = null

        // For devices running android >= Q
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.Q) {
            // getting the contentResolver
            this.contentResolver?.also { resolver ->

                // Content resolver will process the contentvalues
                val contentValues = ContentValues().apply {

                    // putting file information in content values
                    put(MediaStore.MediaColumns.DISPLAY_NAME, filename)
                    put(MediaStore.MediaColumns.MIME_TYPE, "image/jpg")
                    put(MediaStore.MediaColumns.RELATIVE_PATH, Environment.DIRECTORY_PICTURES)
                }

                // Inserting the contentValues to
                  // contentResolver and getting the Uri
                val imageUri: Uri? = resolver.insert(MediaStore.Images.Media.EXTERNAL_CONTENT_URI, contentValues)

                // Opening an outputstream with the Uri that we got
                fos = imageUri?.let { resolver.openOutputStream(it) }
            }
        } else {
            // These for devices running on android < Q
            val imagesDir = Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_PICTURES)
            val image = File(imagesDir, filename)
            fos = FileOutputStream(image)
        }

        fos?.use {
            // Finally writing the bitmap to the output stream that we opened
            bitmap.compress(Bitmap.CompressFormat.JPEG, 100, it)
            Toast.makeText(this , "Captured View and saved to Gallery" , Toast.LENGTH_SHORT).show()
        }
    }
}
```

### **输出:**

<video class="wp-video-shortcode" id="video-557099-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210208210909/capture_view_android_gfg.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210208210909/capture_view_android_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210208210909/capture_view_android_gfg.mp4)</video>

**Github 回购**T2**这里**T5】