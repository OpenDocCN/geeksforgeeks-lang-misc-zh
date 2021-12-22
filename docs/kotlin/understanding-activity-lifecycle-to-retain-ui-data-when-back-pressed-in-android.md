# 了解活动生命周期，在安卓系统中按下回车键时保留用户界面数据

> 原文:[https://www . geeksforgeeks . org/了解-活动-生命周期-保留-ui-数据-按回时-在安卓中/](https://www.geeksforgeeks.org/understanding-activity-lifecycle-to-retain-ui-data-when-back-pressed-in-android/)

### 安卓系统中的 onBackPressed()是什么？

这是当用户按下安卓设备上的后退按钮时调用的覆盖函数。它对应用程序的活动生命周期有很大的影响。官方文档指出，当活动检测到用户按下后退键时，将调用 [onBackPressed()](https://developer.android.com/reference/android/app/Activity#onBackPressed()) 方法。默认实现只是完成当前活动，但是您可以覆盖它来做任何您想做的事情。

因此，通过本文，我们将向您展示如何覆盖这个方法并保留活动数据。但在此之前，有必要**了解一下安卓中的活动生命周期。参考本文，更好地了解安卓系统中的活动生命周期:[安卓系统中的活动生命周期，带演示应用](https://www.geeksforgeeks.org/activity-lifecycle-in-android-with-demo-app/)。**

****本文共 4 部分:****

1.  **创建一个模板代码来理解导航键事件和链接的活动生命周期方法(如果您知道活动生命周期，请跳过)**
2.  **重写背面按压方法**
3.  **测试编辑文本**
4.  **测试文本视图**

### **1.创建一个模板代码来理解导航键事件和链接的活动生命周期方法**

****第一步:在安卓工作室新建项目****

**要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 Kotlin 中演示了该应用程序，因此在创建新项目时，请确保选择 **Kotlin** 作为主要语言。**

****步骤 2:覆盖活动生命周期**中的所有方法**

**我们在每个方法中实现了一个 Toast 消息，以了解在活动生命周期中什么时候调用哪个方法。现在只需在设备或模拟器上运行项目。**

## **我的锅**

```kt
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        Toast.makeText(applicationContext, "onCreate", Toast.LENGTH_SHORT).show()

        }
    }

    override fun onPause() {
        super.onPause()
        Toast.makeText(applicationContext, "onPause", Toast.LENGTH_SHORT).show()
    }

    override fun onStop() {
        super.onStop()
        Toast.makeText(applicationContext, "onStop", Toast.LENGTH_SHORT).show()
    }

    override fun onDestroy() {
        super.onDestroy()
        Toast.makeText(applicationContext, "onDestroy", Toast.LENGTH_SHORT).show()
    }

    override fun onRestart() {
        super.onRestart()
        Toast.makeText(applicationContext, "onRestart", Toast.LENGTH_SHORT).show()
    }

    override fun onStart() {
        super.onStart()
        Toast.makeText(applicationContext, "onStart", Toast.LENGTH_SHORT).show()
    }

    override fun onResume() {
        super.onResume()
        Toast.makeText(applicationContext, "onResume", Toast.LENGTH_SHORT).show()
    }
}
```

****第三步:运行程序****

1.  **应用程序启动时: **onCreate，onStart，onResume****
2.  **当按下应用概述按钮时:**开启暂停，开启关闭****
3.  **按下主页按钮时:**暂停，暂停****
4.  **当按下后退按钮时:**暂停、停止、停止****

****输出:****

**<video class="wp-video-shortcode" id="video-645180-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210712112612/v1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210712112612/v1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210712112612/v1.mp4)</video>**

****观察:****

**我们可以看到，在任何情况下，除了背部按压，活动都被停止。基本上，它不会被破坏，数据会被保留。但是，当按下后退按钮时，活动会被破坏，这意味着在此调用期间临时数据会丢失。这就是官方文件中所说的。**

**但是我们不想丢失这些数据。为了保留数据，我们需要重写 back pressed 方法。反压法本质上破坏了活动。我们将做出改变，使活动停止，但不破坏。继续阅读。**

### **2.重写背面按压方法**

**请阅读代码中的注释。**

## **我的锅**

```kt
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        Toast.makeText(applicationContext, "onCreate", Toast.LENGTH_SHORT).show()
    }

    // Overriding onBackPressed method
    override fun onBackPressed() {

        // Implement this method to stop
        // the activity and go back
        this.moveTaskToBack(true)
    }

    override fun onPause() {
        super.onPause()
        Toast.makeText(applicationContext, "onPause", Toast.LENGTH_SHORT).show()
    }

    override fun onStop() {
        super.onStop()
        Toast.makeText(applicationContext, "onStop", Toast.LENGTH_SHORT).show()
    }

    override fun onDestroy() {
        super.onDestroy()
        Toast.makeText(applicationContext, "onDestroy", Toast.LENGTH_SHORT).show()
    }

    override fun onRestart() {
        super.onRestart()
        Toast.makeText(applicationContext, "onRestart", Toast.LENGTH_SHORT).show()
    }

    override fun onStart() {
        super.onStart()
        Toast.makeText(applicationContext, "onStart", Toast.LENGTH_SHORT).show()
    }

    override fun onResume() {
        super.onResume()
        Toast.makeText(applicationContext, "onResume", Toast.LENGTH_SHORT).show()
    }
}
```

****输出:****

**<video class="wp-video-shortcode" id="video-645180-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210712112957/v2.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210712112957/v2.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210712112957/v2.mp4)</video>**

**现在我们可以观察到，在背部按压时，活动会停止，但不会破坏。我们现在将实现一些用户界面来测试这是否真的有效。继续读。**

### **3.测试编辑文本**

****第一步:在布局文件(activity_main.xml)中添加 EditText****

## **可扩展标记语言**

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
    android:id="@+id/et1"
    android:layout_width="match_parent"
    android:layout_height="50sp"
    android:textSize="25sp"
    android:inputType="text"
    android:layout_centerInParent="true"/>

</RelativeLayout>
```

**为了测试 EditText，我们不需要在主代码中编写任何代码，除了在前面的代码中指定的代码(覆盖背面按下的方法)。**

****输入:****

**在编辑文本中键入任何内容，然后按后退按钮。返回应用程序，您会注意到文本保留在编辑文本栏中。**

****输出:****

**<video class="wp-video-shortcode" id="video-645180-3" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210712113856/v4.mp4?_=3">[https://media.geeksforgeeks.org/wp-content/uploads/20210712113856/v4.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210712113856/v4.mp4)</video>**

**编辑文本中的文本将被保留。这意味着我们的方法运行良好。我们现在将在文本视图上测试它。继续读。**

### **4.测试文本视图**

****第一步:在布局文件(activity_main.xml)中添加一个 TextView 和一个 Button****

## **可扩展标记语言**

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click the button"
        android:textSize="40sp"
        android:layout_centerInParent="true"/>

    <Button
        android:id="@+id/btn1"
        android:layout_below="@id/tv1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click"
        android:layout_centerHorizontal="true"/>

</RelativeLayout>
```

****步骤 2:通过主代码(MainActivity.kt)** 给这些元素添加功能**

## **我的锅**

```kt
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import android.widget.Toast

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        Toast.makeText(applicationContext, "onCreate", Toast.LENGTH_SHORT).show()

        // TextView and Button
        val tv1 = findViewById<TextView>(R.id.tv1)
        val btn1 = findViewById<Button>(R.id.btn1)

        // A code to increment a variable and 
        // display it on TextView on Button Click
        var k = 0
        btn1.setOnClickListener {
            tv1.text = k.toString()
            k++
        }
    }

    override fun onBackPressed() {
        this.moveTaskToBack(true)
    }

    override fun onPause() {
        super.onPause()
        Toast.makeText(applicationContext, "onPause", Toast.LENGTH_SHORT).show()
    }

    override fun onStop() {
        super.onStop()
        Toast.makeText(applicationContext, "onStop", Toast.LENGTH_SHORT).show()
    }

    override fun onDestroy() {
        super.onDestroy()
        Toast.makeText(applicationContext, "onDestroy", Toast.LENGTH_SHORT).show()
    }

    override fun onRestart() {
        super.onRestart()
        Toast.makeText(applicationContext, "onRestart", Toast.LENGTH_SHORT).show()
    }

    override fun onStart() {
        super.onStart()
        Toast.makeText(applicationContext, "onStart", Toast.LENGTH_SHORT).show()
    }

    override fun onResume() {
        super.onResume()
        Toast.makeText(applicationContext, "onResume", Toast.LENGTH_SHORT).show()
    }
}
```

****输入:****

**继续点击按钮，文本视图中的数字会不断增加。现在尝试后退按钮，并再次打开应用程序。文本将保留在文本视图中。**

****输出:****

**<video class="wp-video-shortcode" id="video-645180-4" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210712113454/v3.mp4?_=4">[https://media.geeksforgeeks.org/wp-content/uploads/20210712113454/v3.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210712113454/v3.mp4)</video>**

**我们的方法非常有效。现在在代码中使用这种方法来保留活动数据。**