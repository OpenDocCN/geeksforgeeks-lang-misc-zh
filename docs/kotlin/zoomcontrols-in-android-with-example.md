# 安卓中的 ZoomControls 示例

> 原文:[https://www . geeksforgeeks . org/zoomcontrols-in-Android-with-example/](https://www.geeksforgeeks.org/zoomcontrols-in-android-with-example/)

在安卓系统中，缩放控件是一个类，它有一些用来控制缩放功能的方法。它有两个按钮，用于控制缩放功能(即放大和缩小)。**缩放控制类在 API 版本 29** 中已被弃用。ZoomControls 类提供的功能可以通过自定义视图和自定义布局，然后通过专用的缩放控件小部件，以更好的方式进行处理。

![ZoomControls in Android ](img/c69c489f053b617f3eeefd133573cc26.png)

### 缩放控制的重要方法

*   假设 ZoomControls 是 ZoomControl 类的引用，该类用于调用 ZoomControls 类的不同方法。

> 缩放控件=(缩放控件)findviewbyid(r . id . simplezoom 控件)；

*   **show():** 此方法用于在 App UI 上显示缩放控件。

> //将显示缩放控件
> 
> zoomControls.show()

*   **hide():** 此方法用于隐藏 App UI 上的缩放控件。

> //将隐藏缩放控件
> 
> zoomControls.hide()

*   **setonzoominiclicklistener(onclicklistener listener):**按下放大按钮时调用此方法。用于自定义按下放大按钮时显示的用户界面。

> zoomcontrols . setonzoomclicklistener(新视图。OnClickListener(){ 0
> 
> @覆盖
> 
> 公共空间点击(视图 v){ 0
> 
> //添加将在以下情况下执行的代码
> 
> //放大按钮已被按下
> 
> }
> 
> });

*   **setonzoomoutcklistener(onclicklistener listener):**按下缩小时调用此方法。它的工作方式与 setOnZoomInClickListener()方法相同，但它最小化了 ie 聚合用户界面的方式。

> zoom controls . setanoooooutclickstener(新视图)。onclicklistener()& gt
> 
> @覆盖
> 
> 公共空间点击(视图 v){ 0
> 
> //添加将在以下情况下执行的代码
> 
> //缩小按钮已被按下
> 
> }
> 
> });

*   **setiszoomineabled(布尔值 isEnabled):** 这是缩放控件的方法之一，用于启用或禁用放大功能。

> //它将启用 zoomIn 按钮
> 
> zoomcontrols . setiszoominenabled(true)
> 
> //它将禁用 zoomIn 按钮
> 
> zoomcontrols . setiszoominenabled(false)

*   **setiszoomutenabled(boolean isEnabled):**也是缩放控件的方法之一，用于启用或禁用缩小功能。

> //它将启用缩放按钮
> 
> zoomcontrols . setiszoomutenabled(true)
> 
> //它将禁用缩放按钮
> 
> zoom controls . setszoomboutnabled(false)

*   **设置缩放速度(长速度):**这用于设置缩放控件正在进行的缩放的缩放速度

### 缩放控件的重要属性

*   **id:** 该属性用于给缩放控件一个唯一的标识。

*   **背景:**这是用来给缩放控件赋予背景颜色的。

> android:id="@+id/zoom_controls
> 
> android:background="#fffff"/>

*   **填充:**用于在缩放控件的侧面填充。

> android:id="@+id/zoom_controls
> 
> android:填充= " 20dp "/>

### 例子

下面给出一个 GIF 示例，了解一下在这篇 文章中我们要做什么。请注意，我们将使用 **Java** 和 **Kotlin** 语言来实现这个项目。

![ZoomControls in Android](img/c544abdba1895f28e987dc0c71badd08.png)

### 逐步实施

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

现在转到代表应用程序用户界面的 **活动文件。下面是**activity _ main . XML**文件的代码。在代码内部添加注释，更详细地理解代码。**

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--Adding the image view-->
    <ImageView
        android:id="@+id/image_View"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:scaleType="fitXY"
        android:src="@drawable/indiamap" />

    <!--Adding the Zoom Controls 
        within the relative layout-->
    <ZoomControls
        android:id="@+id/zoom_controls"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentEnd="true"
        android:layout_alignParentBottom="true"
        android:layout_margin="10dp" />

</RelativeLayout>
```

**步骤 3:使用主活动文件**

转到 **主活动** 文件，参考至以下代码。下面是 **MainActivity.kt** 和**MainActivity.java**文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
// Kotlin code to implement the zoom controls
import android.os.Bundle
import android.view.View
import androidx.appcompat.app.AppCompatActivity
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // onTouch listener function when the image is clicked
        image_View.setOnTouchListener { v, m -> // Perform tasks here
            zoom_controls.show()
            false
        }

        // This function will be automatically called out,when
        // zoom in button is being pressed
        zoom_controls.setOnZoomInClickListener(
                View.OnClickListener {
                    val x: Float = image_View.getScaleX()
                    val y: Float = image_View.getScaleY()

                    // setting the new scale
                    image_View.setScaleX((x + 0.5f) as Float)
                    image_View.setScaleY((y + 0.5f) as Float)
                    zoom_controls.hide()
                }
        )

        // This function will be called when
        // zoom out button is pressed
        zoom_controls.setOnZoomOutClickListener(
                View.OnClickListener {
                    val x: Float = image_View.getScaleX()
                    val y: Float = image_View.getScaleY()
                    if (x == 1f && y == 1f) {
                        image_View.setScaleX(x as Float)
                        image_View.setScaleY(y as Float)
                        zoom_controls.hide()
                    } else {
                        // setting the new scale
                        image_View.setScaleX((x - 0.5f) as Float)
                        image_View.setScaleY((y - 0.5f) as Float)
                        // hiding the zoom controls
                        zoom_controls.hide()
                    }
                }
        )
    }
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```
// Java code to implement the zoom controls
import androidx.appcompat.app.AppCompatActivity;
import android.graphics.Color;
import android.os.Bundle;
import android.view.MotionEvent;
import android.view.View;
import android.widget.ImageView;
import android.widget.ZoomControls;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    ZoomControls zoomControls;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView=findViewById(R.id.image_View);
        zoomControls=findViewById(R.id.zoom_controls);

        zoomControls.setBackgroundColor(Color.BLACK);
        zoomControls.show();

      // onTouch listener function  when the image is clicked  
      imageView.setOnTouchListener(
                new View.OnTouchListener() {
                    @Override
                    public boolean onTouch(View view, MotionEvent motionEvent) {
                        zoomControls.show();
                        return false;
                    }
                }
        );

        // This function will be automatically called out,when
        // zoom in button is being pressed
        zoomControls.setOnZoomInClickListener(
                new View.OnClickListener() {
                    @Override
                    public void onClick(View view) {
                        float x=imageView.getScaleX();
                        float y=imageView.getScaleY();

                        // setting the new scale
                        imageView.setScaleX((float)(x+0.5f));
                        imageView.setScaleY((float)(y+0.5f));
                        zoomControls.hide();
                    }
                }
        );

        // This function will be called when
        // zoom out button is pressed
        zoomControls.setOnZoomOutClickListener(
                new View.OnClickListener() {
                    @Override
                    public void onClick(View view) {
                        float x=imageView.getScaleX();
                        float y=imageView.getScaleY();
                        if(x==1 && y==1)
                        {
                            // the scale will remain same,since
                            // it is maximum possible zoom out
                            imageView.setScaleX((float)(x));
                            imageView.setScaleY((float)(y));
                            zoomControls.hide();
                        }
                        else
                        {
                            // setting the new scale
                            imageView.setScaleX((float)(x-0.5f));
                            imageView.setScaleY((float)(y-0.5f));
                            // hiding the zoom controls
                            zoomControls.hide();
                        }
                    }
                }
        );
    }
}
```

### **输出**

<video class="wp-video-shortcode" id="video-503308-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201021094320/Zoom_Control_Output_Video.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201021094320/Zoom_Control_Output_Video.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201021094320/Zoom_Control_Output_Video.mp4)</video>