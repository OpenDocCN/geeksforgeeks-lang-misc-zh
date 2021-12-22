# 循环裁剪一张图片，保存到安卓的文件中

> 原文:[https://www . geeksforgeeks . org/circular-crop-a-image-and-save-to-file-in-Android/](https://www.geeksforgeeks.org/circular-crop-an-image-and-save-it-to-the-file-in-android/)

市场上有多种应用程序可以帮助处理图像处理，但大多数应用程序都无法产生非常基本的操作。裁剪是一个简单的应用程序，可以通过裁剪来调整图像的大小。当涉及到自由手动或形状裁剪时，这一任务变得复杂，这意味着将图像裁剪成所需的形状。

![](img/b9ddbaa7ec582faa20c2ad70a7af6061.png)

在本文中，我们将向您展示如何创建一个应用程序，以循环方式裁剪图像并将其存储在本地设备中。没有外部库或服务用于生成此应用程序。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 **Kotlin** 中演示了该应用程序，因此在创建新项目时，请确保选择 Kotlin 作为主要语言。

**第二步:在 activity_main.xml 或布局文件**中添加一个 ImageView 和两个 Buttons

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

      <!-- Image will be loaded here -->
    <ImageView
        android:id="@+id/iv"
        android:layout_width="match_parent"
        android:layout_height="500dp"
        android:layout_centerInParent="true" />

      <!-- Button to perform Cropping -->
    <Button
        android:id="@+id/btnCrop"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:text="Crop" />

      <!-- Button to save the image in ImageView -->
    <Button
        android:id="@+id/btnSave"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:text="Save" />

</RelativeLayout>
```

**步骤 3:在 res >可绘制文件夹**中添加所需图像

添加时，为其指定所需的名称。作为参考，这张图片是“image.png”，它是从互联网上下载的，并直接复制到可绘制的文件夹中。

![](img/b04ab927a5fd467424603e53ed44ee31.png)

**第四步:为 MainActivity.kt** 编写以下代码

这段代码中有两个函数:

1.  ***获取圆形位图(位图)*** :裁剪图像
2.  ***保存 MediaToStorage(位图)*** :保存图像。参考[如何在安卓系统中抓取视图截图并保存到图库？](https://www.geeksforgeeks.org/how-to-capture-screenshot-of-a-view-and-save-it-to-gallery-in-android/)

请参考评论，以便更好地理解。

## 我的锅

```
import android.content.ContentValues
import android.graphics.*
import android.net.Uri
import android.os.Build
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Environment
import android.provider.MediaStore
import android.widget.Button
import android.widget.ImageView
import android.widget.Toast
import androidx.annotation.RequiresApi
import java.io.File
import java.io.FileOutputStream
import java.io.OutputStream
import java.lang.Integer.min

class MainActivity : AppCompatActivity() {

    // Declaring the UI elements from the layout file
    private lateinit var buttonCrop: Button
    private lateinit var buttonSave: Button
    private lateinit var imageView: ImageView

    // Declaring the Bitmap
    private lateinit var bitmap: Bitmap

    @RequiresApi(Build.VERSION_CODES.N)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Initializing the UI elements
        imageView = findViewById(R.id.iv)
        buttonCrop = findViewById(R.id.btnCrop)
        buttonSave = findViewById(R.id.btnSave)

        // Declaring resource address ( type integer)
        val bitmapResourceID: Int = R.drawable.image

        // Setting the ImageView with the Image
        imageView.setImageBitmap(BitmapFactory.decodeResource(resources, bitmapResourceID))
        bitmap = BitmapFactory.decodeResource(resources, bitmapResourceID)

        // When Crop button is clicked
        buttonCrop.setOnClickListener {
              // runs a custom function on the original image
            bitmap = getCircularBitmap(bitmap)

            // Sets the ImageView with the editted/cropped Image
            imageView.setImageBitmap(bitmap)
        }

        // When Save button is clicked
        buttonSave.setOnClickListener {
             // Save whatever the bitmap is (edited/uneditted) into the device.
            saveMediaToStorage(bitmap)
        }
    }

    // Function to crop the image in a circle
    @RequiresApi(Build.VERSION_CODES.N)
    private fun getCircularBitmap(srcBitmap: Bitmap?): Bitmap {

        // Select whichever of width or height is minimum
        val squareBitmapWidth = min(srcBitmap!!.width, srcBitmap.height)

        // Generate a bitmap with the above value as dimensions
        val dstBitmap = Bitmap.createBitmap(
            squareBitmapWidth,
            squareBitmapWidth,
            Bitmap.Config.ARGB_8888
        )

        // Initializing a Canvas with the above generated bitmap
        val canvas = Canvas(dstBitmap)

        // initializing Paint
        val paint = Paint()
        paint.isAntiAlias = true

        // Generate a square (rectangle with all sides same)
        val rect = Rect(0, 0, squareBitmapWidth, squareBitmapWidth)
        val rectF = RectF(rect)

        // Operations to draw a circle
        canvas.drawOval(rectF, paint)
        paint.xfermode = PorterDuffXfermode(PorterDuff.Mode.SRC_IN)
        val left = ((squareBitmapWidth - srcBitmap.width) / 2).toFloat()
        val top = ((squareBitmapWidth - srcBitmap.height) / 2).toFloat()
        canvas.drawBitmap(srcBitmap, left, top, paint)
        srcBitmap.recycle()

        // Return the bitmap
        return dstBitmap
    }

    // Function to save an Image
    private fun saveMediaToStorage(bitmap: Bitmap) {
        val filename = "${System.currentTimeMillis()}.jpg"

        var fos: OutputStream? = null

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.Q) {
            this.contentResolver?.also { resolver ->
                val contentValues = ContentValues().apply {
                    put(MediaStore.MediaColumns.DISPLAY_NAME, filename)
                    put(MediaStore.MediaColumns.MIME_TYPE, "image/jpg")
                    put(MediaStore.MediaColumns.RELATIVE_PATH, Environment.DIRECTORY_PICTURES)
                }
                val imageUri: Uri? = resolver.insert(MediaStore.Images.Media.EXTERNAL_CONTENT_URI, contentValues)
                fos = imageUri?.let { resolver.openOutputStream(it) }
            }
        } else {
            val imagesDir = Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_PICTURES)
            val image = File(imagesDir, filename)
            fos = FileOutputStream(image)
        }

        fos?.use {
            bitmap.compress(Bitmap.CompressFormat.JPEG, 100, it)
            Toast.makeText(this , "Captured View and saved to Gallery" , Toast.LENGTH_SHORT).show()
        }
    }
}
```

**第四步:在 AndroidManifest.xml 文件**中添加存储权限

在设备中存储图像需要此权限。

## 可扩展标记语言

```
<manifest....">

    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />

    <application....>
    </application>
</manifest>
```

**输出:**

<video class="wp-video-shortcode" id="video-655899-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210728184517/output1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210728184517/output1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210728184517/output1.mp4)</video>