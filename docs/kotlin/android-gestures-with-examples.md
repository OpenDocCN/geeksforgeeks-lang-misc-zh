# 安卓手势示例

> 原文:[https://www . geesforgeks . org/Android-手势-带示例/](https://www.geeksforgeeks.org/android-gestures-with-examples/)

安卓支持一系列触摸手势，如**轻点**、**双击**、**捏一下**、**刷一下**、**滚动**、**长按**、**拖动**、**甩一下**。拖动和投掷看似相似，但拖动是当用户在触摸屏上拖动手指时发生的滚动类型，而投掷手势发生在用户拖动并快速抬起手指时。运动事件通过动作代码描述触摸事件的状态。安卓支持一长串**动作代码**:

*   **ACTION_DOWN:** 触摸事件已经开始。
*   **动作 _ 移动:**触摸事件期间发生的变化(在动作 _ 向下和动作 _ 向上之间)**。**
*   **ACTION_UP:** 触摸事件已经结束。这包含最终发布位置。
*   **ACTION_CANCEL:** 手势被取消。

> **注意:**您应该在 ACTION_CANCEL 和 ACTION_UP 事件期间执行相同的操作。

### **重要方法**

*   **getAction()** :从事件参数中提取用户执行的动作。

### **重要接口**

*   **手势检测器。OnGestureListener** :当特定触摸事件发生时通知用户。
*   **手势检测器。OnDoubleTalistener**:当双击事件发生时通知用户。

### **例 1**

让我们来看看对 ACTION_DOWN、ACTION_UP 等事件执行一些简单操作的方法。

**第一步** : **新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/gesture"
        android:layout_width="398dp"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:gravity="center"
        android:hint="Gestures"
        android:textAlignment="center"
        android:textColor="@android:color/black"
        android:textSize="50sp"></TextView>

</FrameLayout>
```

**第三步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.os.Bundle
import android.util.Log
import android.view.MotionEvent
import androidx.appcompat.app.AppCompatActivity
import kotlinx.android.synthetic.main.activity_main.*

// logs are added for better understanding. 
private const val TAG = "Gestures"

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }

    override fun onTouchEvent(event: MotionEvent): Boolean {

        return when (event.action) {
            MotionEvent.ACTION_DOWN -> {
                // when we touch or tap on the screen
                Log.d(TAG, "Action was DOWN")
                gesture.text = "Action was DOWN"
                true
            }
            MotionEvent.ACTION_MOVE -> {
                // while pressing on the screen, 
                // we move our finger
                Log.d(TAG, "Action was MOVE")
                gesture.text = "Action was MOVE"

                true
            }
            MotionEvent.ACTION_UP -> {
                // Lifting up the finger after
                // pressing on the screen
                Log.d(TAG, "Action was UP")
                gesture.text = "Action was UP"

                true
            }
            MotionEvent.ACTION_CANCEL -> {
                Log.d(TAG, "Action was CANCEL")
                gesture.text = "Action was CANCEL"

                true
            }
            MotionEvent.ACTION_OUTSIDE -> {
                Log.d(TAG, "Movement occurred outside of screen element")
                gesture.text = "Movement occurred screen element"

                true
            }
            else -> super.onTouchEvent(event)
        }
    }
}
```

> **注意:**你可能会在下面一行得到一个错误:
> 
> **导入 kot linx . Android . synthetic . main . activity _ main。***
> 
> 请参考[这个](https://stackoverflow.com/questions/52271521/import-kotlinx-android-synthetic-main-activity-main-is-not-working)来修复这个错误。

### **输出:**

<video class="wp-video-shortcode" id="video-529866-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201207193134/gfg1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201207193134/gfg1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201207193134/gfg1.mp4)</video>

**输出说明:**

*   当我们点击屏幕或按下屏幕时，可以看到视频中显示**动作为 DOWN**
*   当我们按下鼠标或手指时，文本视图显示**动作为移动**。
*   当我松开鼠标或抬起手指时，它显示**动作为 UP**

### **例 2**

现在让我们来看看在事件上执行一些动作的方法，如单击、双击、长按等。下面的代码使用与上面相同的 **activity_main.xml** 。

**使用 MainActivity.kt 文件:**

## 我的锅

```
import android.os.Bundle
import android.util.Log
import android.view.GestureDetector
import android.view.MotionEvent
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.GestureDetectorCompat
import kotlinx.android.synthetic.main.activity_main.*

// logs are added for better understanding. 
private const val TAG = "Gestures"

// We have to implement the members as well
// because we are implementing the interfaces.
class MainActivity : AppCompatActivity(), GestureDetector.OnGestureListener, 
                                       GestureDetector.OnDoubleTapListener {

    private lateinit var detectorCompat: GestureDetectorCompat

    public override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Instantiate the gesture detector with the
        // application context and an implementation of
        // GestureDetector.OnGestureListener
        // since we have implemented these 
        // interfaces we can simply us the
        // this keyword to refer to the current activity
        detectorCompat = GestureDetectorCompat(this, this)
    }

    // this function connects touch events to gestures
    override fun onTouchEvent(event: MotionEvent): Boolean {
        return if (detectorCompat.onTouchEvent(event)) {
            true
        } else {
            super.onTouchEvent(event)
        }
    }

    override fun onDown(event: MotionEvent): Boolean {
        Log.d(TAG, "onDown: $event")
        return true
    }

    override fun onFling(
            event1: MotionEvent,
            event2: MotionEvent,
            velocityX: Float,
            velocityY: Float
    ): Boolean {
        Log.d(TAG, "onFling: $event1 $event2")
        return true
    }

    override fun onLongPress(event: MotionEvent) {
        Log.d(TAG, "onLongPress: $event")
        gesture.text = "Long Press"
    }

    override fun onScroll(
            event1: MotionEvent,
            event2: MotionEvent,
            distanceX: Float,
            distanceY: Float
    ): Boolean {
        Log.d(TAG, "onScroll: $event1 $event2")
        return true
    }

    override fun onShowPress(event: MotionEvent) {
        Log.d(TAG, "onShowPress: $event")
        gesture.text = "Press"
    }

    override fun onSingleTapUp(event: MotionEvent): Boolean {
        Log.d(TAG, "onSingleTapUp: $event")
        gesture.text = "Single Tap"

        return true
    }

    override fun onDoubleTap(event: MotionEvent): Boolean {
        Log.d(TAG, "onDoubleTap: $event")
        gesture.text = "DoubleTap"

        return true
    }

    override fun onDoubleTapEvent(event: MotionEvent): Boolean {
        Log.d(TAG, "onDoubleTapEvent: $event")

          // simple toast
        Toast.makeText(this, "Double Tap", Toast.LENGTH_SHORT).show() 
        return true
    }

    override fun onSingleTapConfirmed(event: MotionEvent): Boolean {
        Log.d(TAG, "onSingleTapConfirmed: $event")
        gesture.text = "Single Tap Confirmed"

        return true
    }
}
```

### **输出:**

<video class="wp-video-shortcode" id="video-529866-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201207193136/gfg2.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20201207193136/gfg2.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201207193136/gfg2.mp4)</video>

**输出说明:**

*   当我们单次点击屏幕时，它显示**单次点击**，然后**单次点击确认**，因为活动没有取消
*   当我们按下屏幕时，它会显示**按下**，如果我继续按下去，它会显示**长按。**
*   当我们双击**时，双击**会显示在文本视图和吐司中。

> **注意:onTouchEvent()** 用于活动，但您可以附加一个视图。使用**settontouchlistener()**方法将对象设置为任何视图对象。

通过这种方法，您可以在视图内触发事件时执行操作，因为 OnTouchListener 附加到该特定视图。例如，对于 id 为**“小鬼”的 **ImageView** 。**

> img . setontouchlistener { view，motionEvent ->
> 
> // …响应触摸事件
> 
> 真实的
> 
> }
> 
> //用于一般视图
> 
> 查找查看者{ v，事件->
> 
> // …响应触摸事件
> 
> 真实的
> 
> }