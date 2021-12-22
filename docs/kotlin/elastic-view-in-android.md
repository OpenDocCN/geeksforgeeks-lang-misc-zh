# 安卓中的弹性视图

> 原文:[https://www.geeksforgeeks.org/elastic-view-in-android/](https://www.geeksforgeeks.org/elastic-view-in-android/)

本文在安卓中增加了 **ElasticView** 。**弹性视图**是常规的 [**卡片视图**](https://developer.android.com/reference/androidx/cardview/widget/CardView) ，可以通过用户触摸进行伸缩。OnClickListener 等各种重要方法也可以添加到 **ElasticView** 的子视图中。它使用户界面更具吸引力，从而增强了用户体验。

### 方法:

**第一步:**在 [**build.gradle**](https://www.geeksforgeeks.org/android-build-gradle/) 文件中添加支持库，并在依赖项部分添加依赖项。它将允许我们直接在 XML 文件中添加弹性视图。

## 可扩展标记语言

```

dependencies {         
       implementation 'com.github.armcha:ElasticView:0.2.0'    
}
```

**步骤 2:** 在 **activity_main.xml** 文件中添加以下代码。在该文件中，**弹性视图**及其子视图**图像视图**被添加到布局中。

## activity_main.xml

```

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <io.armcha.elasticview.ElasticView
        app:flexibility="7"
        android:layout_margin="20dp"
        android:layout_gravity="center"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:cardCornerRadius="10dp"
        app:cardElevation="5dp">

        <ImageView
            android:id="@+id/imageView"
            android:src="@drawable/gfg"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>

    </io.armcha.elasticview.ElasticView>

</LinearLayout>
```

**第三步:**在 **MainActivity.kt** 文件中添加以下代码。在这个文件中，OnClickListner 被添加到 ImageView 中，因此每当用户点击它时，OnClickListner 函数就会被自动调用。

## MainActivity.kt 公司

```

package com.madhav.maheshwari.wavelineview;

import android.os.Bundle
import android.view.View
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        imageView.setOnClickListener(View.OnClickListener {
            Toast.makeText(this,"Click",Toast.LENGTH_SHORT).show()
        })
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-454780-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200714215133/Record_2020-07-14-21-48-52_fb6e1da1539595f53452e77f63671e821.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20200714215133/Record_2020-07-14-21-48-52_fb6e1da1539595f53452e77f63671e821.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200714215133/Record_2020-07-14-21-48-52_fb6e1da1539595f53452e77f63671e821.mp4)</video>

更多信息请参考 [*官方文档*](https://github.com/armcha/ElasticView) 。