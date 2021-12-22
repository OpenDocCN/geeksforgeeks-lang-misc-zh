# 从安卓系统的图像中提取颜色轮廓

> 原文:[https://www . geesforgeks . org/color-profile-extraction-from-in-images-in-Android/](https://www.geeksforgeeks.org/color-profile-extraction-from-images-in-android/)

颜色配置文件可以使用安卓系统的调色板应用编程接口从安卓系统上的图像中提取；通常，颜色配置文件将用于基于图片生成颜色协调的小部件。例如，卡片可以包括图像和标题文本，它们根据图片的颜色配置文件被着色。[调色板 API](https://www.geeksforgeeks.org/selecting-colors-with-the-palette-api-in-android-with-example/) 允许您获取以下颜色配置文件:

1.  充满活力的光
2.  响亮的
3.  黑暗而充满活力
4.  灯光静音
5.  柔和的
6.  暗静音

### 理解核心

每个颜色配置文件都包含一个具有三种主要颜色的色板:

代码，以便更好地理解代码

1.  **RGB** :色板的原色。
2.  **标题文本颜色**:出现在样本原色上方的“标题”文本的颜色。
3.  **正文颜色**:出现在色板原色上方的“正文”文本的颜色。

### **分步实施**

这个应用程序由一个按钮和一张图片组成。当您按下按钮时，图像会变成不同的图像。在下面找到六个不同的图像标题。这些图片的背景和文本颜色会随着图片的变化而变化，这是调色板应用编程接口从图像中检索到的。

**步骤#1:添加依赖项**

```
dependencies {
    // AndroidX Pallete
    implementation 'androidx.palette:palette-ktx:1.0.0'
    // Picasso
    implementation 'com.squareup.picasso:picasso:2.7'
}
```

**第二步:添加互联网权限，让我们的 app 可以使用互联网**

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.geeksforgeeks.android.androidx.palette">
    <uses-permission android:name="android.permission.INTERNET" />

...<!--The rest of the manifest goes here-->
</manifest>
```

**第三步:设计布局**

导航到 **app > res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是**activity _ main . XML**文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.appcompat.widget.LinearLayoutCompat 
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:orientation="vertical"
  tools:context=".GeeksActivity">

        <Button
            android:id="@+id/changeImage"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Change Image" />

        <ImageView
            android:id="@+id/image_source"
            android:layout_width="match_parent"
            android:layout_height="200dp"
            android:contentDescription="Palette Demand Image"
            android:scaleType="centerCrop"
            tools:src="@tools:sample/backgrounds/avatars" />

        <androidx.appcompat.widget.LinearLayoutCompat
            android:id="@+id/layout_light_vibrant"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="15dp">

          <TextView
                android:id="@+id/text_light_vibrant"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Light Vibrant" />

        </androidx.appcompat.widget.LinearLayoutCompat>

        <androidx.appcompat.widget.LinearLayoutCompat
            android:id="@+id/layout_vibrant"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="15dp">

            <TextView
                android:id="@+id/ gfg _vibrant"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Vibrant" />

        </androidx.appcompat.widget.LinearLayoutCompat>

        <androidx.appcompat.widget.LinearLayoutCompat
            android:id="@+id/layout_gfg_vibrant"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="15dp">

            <TextView
                android:id="@+id/text_ gfg _vibrant"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Dark Vibrant" />

        </androidx.appcompat.widget.LinearLayoutCompat>

        <androidx.appcompat.widget.LinearLayoutCompat
            android:id="@+id/layout_light_gfg "
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="15dp">

          <TextView
                android:id="@+id/text_ gfg _muted"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Light Muted" />

        </androidx.appcompat.widget.LinearLayoutCompat>

        <androidx.appcompat.widget.LinearLayoutCompat
            android:id="@+id/layout_gfg "
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="15dp">

            <TextView
                android:id="@+id/text_muted"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Muted" />
        </androidx.appcompat.widget.LinearLayoutCompat>

        <androidx.appcompat.widget.LinearLayoutCompat
            android:id="@+id/layout_dark_muted"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="15dp">

            <TextView
                android:id="@+id/text_dark_muted"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Dark Muted" />

        </androidx.appcompat.widget.LinearLayoutCompat>

</androidx.appcompat.widget.LinearLayoutCompat>
```

**第四步:使用** **主活动文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.graphics.Bitmap
import android.graphics.drawable.Drawable
import android.os.Bundle
import android.widget.Button
import android.widget.ImageView
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity
import androidx.appcompat.widget.LinearLayoutCompat
import androidx.core.content.ContextCompat
import androidx.palette.graphics.Palette
import com.squareup.picasso.Picasso

class MainActivity : AppCompatActivity() {

        private lateinit var target: com.squareup.picasso.Target
        private lateinit var layoutLightVibrant: LinearLayoutCompat
        private lateinit var gfgVibrant: LinearLayoutCompat
        private lateinit var darkGfG: LinearLayoutCompat
        private lateinit var layoutLightMuted: LinearLayoutCompat
        private lateinit var gfgMuted: LinearLayoutCompat
        private lateinit var gfgMutedDark: LinearLayoutCompat
        private lateinit var gfgLightVibrant: TextView
        private lateinit var gfgText: TextView
        private lateinit var gfgTextVib: TextView
        private lateinit var gfgGfgTextMutedMore: TextView
        private lateinit var gfgTextMutedMore: TextView
        private lateinit var gfgTextMutedDark: TextView

        private val imageUrls = listOf(
            "http://placeimg.com/160/120/animals",
            "http://placeimg.com/160/120/arch",
            "http://placeimg.com/160/120/nature",
            "http://placeimg.com/160/120/people",
            "http://placeimg.com/160/120/tech",
            "http://placeimg.com/160/120/grayscale",
            "http://placeimg.com/160/120/sepia",
        )

        private var imageUrlIndex = 0

        override fun onCreate(savedInstanceState: Bundle?) {
            super.onCreate(savedInstanceState)
            setContentView(R.layout.activity_main)

            setupLayout()
            setupImage()

            findViewById<Button>(R.id.button_change_image).setOnClickListener {
                imageUrlIndex++
                setupImage()
            }
        }

        // Initializes all widgets in the layout
        private fun setupLayout() {
            layoutLightVibrant = findViewById(R.id.layout_light_vibrant)
            gfgVibrant = findViewById(R.id.layout_vibrant)
            darkGfG = findViewById(R.id.layout_dark_vibrant)
            layoutLightMuted = findViewById(R.id.layout_light_muted)
            gfgMuted = findViewById(R.id.layout_muted)
            gfgMutedDark = findViewById(R.id.layout_dark_muted)
            gfgLightVibrant = findViewById(R.id.text_light_vibrant)
            gfgText = findViewById(R.id.text_vibrant)
            gfgTextVib = findViewById(R.id.text_dark_vibrant)
            gfgGfgTextMutedMore = findViewById(R.id.text_light_muted)
            gfgTextMutedMore = findViewById(R.id.text_muted)
            gfgTextMutedDark = findViewById(R.id.text_dark_muted)
        }

        // Fetch image from a URL, display them in 
          // an [ImageView], and extract its color profiles.
        private fun setupImage() {
            val url = imageUrls[imageUrlIndex % imageUrls.size]
            target = object : com.squareup.picasso.Target {
                override fun onBitmapLoaded(bitmap: Bitmap?, from: Picasso.LoadedFrom?) {

                    // Set image to ImageView
                    findViewById<ImageView>(R.id.image_source).setImageBitmap(bitmap)

                    // Extract color profiles
                    bitmap?.let {
                        val palette = Palette.from(it).generate()

                        // Light Vibrant
                        setupColorProfile(
                            palette.lightVibrantSwatch,
                            layoutLightVibrant,
                            gfgLightVibrant,
                        )
                        // Vibrant
                        setupColorProfile(
                            palette.vibrantSwatch,
                            gfgVibrant,
                            gfgText,
                        )
                        // Dark Vibrant
                        setupColorProfile(
                            palette.darkVibrantSwatch,
                            darkGfG,
                            gfgTextVib,
                        )
                        // Light Muted
                        setupColorProfile(
                            palette.lightMutedSwatch,
                            layoutLightMuted,
                            gfgGfgTextMutedMore,
                        )
                        // Muted
                        setupColorProfile(
                            palette.mutedSwatch,
                            gfgMuted,
                            gfgTextMutedMore,
                        )
                        // Dark Muted
                        setupColorProfile(
                            palette.darkMutedSwatch,
                            gfgMutedDark,
                            gfgTextMutedDark,
                        )
                    }
                }

                override fun onPrepareLoad(placeHolderDrawable: Drawable?) {
                    findViewById<ImageView>(R.id.image_source).setImageResource(R.color.purple_200)
                }

                override fun onBitmapFailed(e: Exception?, errorDrawable: Drawable?) {
                }
            }
            Picasso.get()
                .load(url)
                .into(target)
        }

        // Set colors of a color profile.
        private fun setupColorProfile(
            swatch: Palette.Swatch?,
            layoutCompat: LinearLayoutCompat,
            textView: TextView,
        ) {
            layoutCompat.setBackgroundColor(swatch?.rgb ?: ContextCompat.getColor(this, R.color.white))
            textView.setTextColor(swatch?.titleTextColor ?: ContextCompat.getColor(this, R.color.black))
        }
    }
```

**输出:**

<video class="wp-video-shortcode" id="video-683281-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210918105649/geeksforgeekscameracolor.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210918105649/geeksforgeekscameracolor.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210918105649/geeksforgeekscameracolor.mp4)</video>