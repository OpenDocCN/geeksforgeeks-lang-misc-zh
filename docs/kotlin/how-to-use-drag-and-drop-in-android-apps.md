# 如何在安卓应用中使用拖拽？

> 原文:[https://www . geesforgeks . org/如何使用拖放式安卓应用/](https://www.geeksforgeeks.org/how-to-use-drag-and-drop-in-android-apps/)

您可以利用安卓拖放框架，让您的用户通过图形拖放操作来移动数据。这可以从您自己程序中的一个视图切换到另一个视图，或者在启用多窗口模式时在您的应用程序和另一个应用程序之间切换。拖动事件类、拖动侦听器以及辅助方法和类都包含在框架中。

### 拖放的示例用例

1.  帮助您在实时数据上拖动指针以获得对象或事物颜色的东西
2.  在你的移动设备的启动器屏幕上，每个程序都会显示出来，我们可以毫不费力地将应用程序图标从一个位置拖放到另一个位置。

> **极客提示:**要通知系统拖动事件正在被调用，您的应用程序调用 startDrag()函数。这种技术还将数据从一个视图分发到另一个视图。

### 完整事件中使用的手势

安卓中的拖放框架允许您将一个视图拖放到另一个视图，即在一个活动中，如果您有两个或多个视图，您可以使用安卓拖放框架将一个视图的数据从一个视图移动到另一个视图。例如，如果您的安卓活动包含两个文本视图，一个在屏幕的一半，另一个在另一半，第一个文本视图的内容可能会被拖放到另一个文本视图中。

1.  **Start:** You start making a clip data and a clip data. The item of the data being transmitted. As a part of the clip data object, metadata stored in the clip description object in the clip data is provided. For drag-and-drop operations that do not reflect data transfer, you may want to use null instead of real objects.
2.  **Continue:** If the drag event listener returns true, the program can start the drag event. The drag event is in progress, which means that it has started, but it has not finished yet. For example, if you want to drag a text view named tv1 from position 1 to position 2, the intermediate state between them is continuous.
3.  **Drag and drop:** The dragged item is released in the bounding box of the view. Send a drag event with ACTION DROP to the listener of the system view object.
4.  [T0】 end: 【T1] When the user drags the item and drops it, and calls all events related to the drop state, the system sends a signal to the application program, indicating that the drop action is completed and all the required functions have been executed. Therefore, the system shows that the drag-and-drop event has ended.

### 涉及拖动的事件

请参考下表，了解涉及拖动的所有不同事件:

<figure class="table">

| getAction()值 | 

这是什么意思？

 |
| --- | --- |
| **动作 _ 拖动 _ 进入** | When the drag shadow enters the bounding box of the View object, the drag event listener receives the event action type. When the shadow is dragged into the bounding box, the listener receives the first event action type. If the listener wants to receive the drag event of this operation in the future, it must return a Boolean value of true to the system. |
| **动作 _ 拖动 _ 位置** | DRAG LOCATION When the drag shadow is still in the bounding box of the view, the drag event listener of the view object will receive the ACTION DRAG ENTERED event when it gets the action dragentered event. |
| **动作 _ 拖动 _ 开始** | The drag event listener of the View object receives this event operation type immediately after the application runs startDrag () and gets the drag shadow. |
| **动作 _ 拖动 _ 排除** | When the drag event listener of the view object receives an ACTION DRAG ENTERED and at least one ACTION DRAG LOCATION event, and after the user has dragged the drag shadow out of the bounding box of the view, the event action type is received by it. |
| **动作 _ 下降** | 当用户在 View 对象上释放拖拽阴影时，View 对象上的拖拽事件监听器接收到该事件动作类型。只有当侦听器响应 ACTION DRAG STARTED drag 事件而响应 true 时，此操作类型才会传递给视图对象的侦听器。如果用户在未注册侦听器的视图上释放拖动阴影，或者如果用户在不属于当前布局的任何内容上释放拖动阴影，则不会传输此操作类型。如果丢弃被正确处理，监听器应该返回布尔值 true。如果不是，它应该返回 false。 |
| **动作 _ 拖动 _ 结束** | Notifies the view that the drag-and-drop action is complete. |

</figure>

### 拖动中的效果和阴影

系统显示用户在拖放操作期间拖动的图像。此图描述了从数据移动性角度提取的数据。图中显示了其他程序的拖动过程的一些部分。

这幅画被称为拖曳阴影。您可以通过为视图声明方法来构建它。DragShadowBuilder 对象，然后在使用 startDrag()开始拖动时将其传递给系统。系统使用视图中描述的回调方法。DragShadowBuilder 获取一个拖动阴影作为它对 startDrag()的回答的一部分。

### **例**

在本例中，我们将在边界区域内将文本视图从一个位置拖放到另一个位置。

**第一步:首先，添加应用的布局文件**

## XML

```kt
<?xml version="1.0" encoding="utf-8"?>
<ConstraintLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    <LinearLayout
            android:layout_width="match_parent"
            android:id="@+id/gfgLayout"
            android:orientation="vertical"
            android:layout_height="80dp"
            android:background="#0F9D58 ">
        <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:id="@+id/gfgDrop"
                android:text="GFG | First App "
                android:textSize="16p"
                android:layout_margin="24dp"
                android:textColor="#0F9D58 "/>
    </LinearLayout>
</ConstraintLayout>
```

**第二步:使用柯特林文件**

## 柯特林

```kt
package com.geeksforgeeks.sampleDrag

import android.os.Bundle
import android.support.v7.app.AppCompatActivity
import android.util.Log
import android.defGeeksView.DragEvent
import android.defGeeksView.MotionEvent
import android.defGeeksView.DefGeeksView
import android.defGeeksView.DefGeeksViewGroup
import android.widget.LinearLayout
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity: AppCompatActivity(), DefGeeksView.OnTouchListener, DefGeeksView.DragHappeningListener {
    private val TAG = MainActivity::class.java.simpleName
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentDefGeeksView(R.layout.activity_main)
        theDraggers()
    }
    private fun theDraggers() {
        gfgDrop.setOnTouchListener(this)
        geeksforgeeksDefGeeksView.setDragHappeningListener(this)
    }
    override fun dragHappening(defGeeksView:DefGeeksView, dragEvent: DragEvent):Boolean {
        Log.d(TAG, "dragHappening: defGeeksView->$defGeeksView\n DragEvent$dragEvent")
        when (dragEvent.action) {
            DragEvent.ACTION_DRAG_ENDED -> {
                return true
            }
            DragEvent.ACTION_DRAG_EXITED -> {
                return true
            }
            DragEvent.ACTION_DRAG_ENTERED -> {
                return true
            }
            DragEvent.ACTION_DRAG_STARTED -> {
                return true
            }
            DragEvent.ACTION_DROP -> {
                val gfgTextDefGeeksView = dragEvent.localState as DefGeeksView
                val defaultText = gfgTextDefGeeksView.parent as DefGeeksViewGroup
                defaultText.removeDefGeeksView(gfgTextDefGeeksView)
                val container = defGeeksView as LinearLayout
                container.addDefGeeksView(gfgTextDefGeeksView)
                defaultText.removeDefGeeksView(gfgTextDefGeeksView)
                gfgTextDefGeeksView.x = dragEvent.x
                gfgTextDefGeeksView.y = dragEvent.y
                defGeeksView.addDefGeeksView(gfgTextDefGeeksView)
                defGeeksView.setVisibility(DefGeeksView.VISIBLE)
                return true
            }
            DragEvent.ACTION_DRAG_LOCATION -> {
                return true
            }
            else -> return false
        }
    }
    override fun onTouch(defGeeksView:DefGeeksView, motionEvent: MotionEvent):Boolean {
        return if (motionEvent.action === MotionEvent.ACTION_DOWN) {
            val dragShadowBuilder = DefGeeksView.DragShadowBuilder(defGeeksView)
            defGeeksView.startDrag(null, dragShadowBuilder, defGeeksView, 10)
            true
        } else {
            false
        }
    }
}
```

在这里获取完整代码[。](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20210908003121/Geeks-for-Geeks-Android-Annotation-main1.zip)

### 结论

运行 Android 7.0 (API 级别 24)或更高版本的设备启用[多窗口模式](https://www.geeksforgeeks.org/activity-state-changes-in-android-with-example/)，允许用户将数据从一个程序拖放到另一个程序:

1.  The application that originally owns the data is called the source application. It was here when the long journey began.
2.  The app that receives the data is called the target app. This is the moment when the resistance ends.

在本文中，我们学习了如何在我们的安卓应用程序中使用拖放功能。我们发现了一系列与拖动事件相关的事件。最后，我们演示了拖放功能。因此，利用上述方法，您可以在安卓中创建额外的拖放应用程序。