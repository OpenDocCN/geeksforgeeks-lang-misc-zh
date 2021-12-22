# 安卓系统如何将数据从活动发送到碎片？

> 原文:[https://www . geeksforgeeks . org/如何将数据从活动发送到安卓碎片/](https://www.geeksforgeeks.org/how-to-send-data-from-activity-to-fragment-in-android/)

**先决条件:**

*   [安卓活动介绍](https://www.geeksforgeeks.org/introduction-to-activities-in-android/)
*   [安卓碎片介绍](https://www.geeksforgeeks.org/introduction-fragments-android/)

在安卓系统中，片段是用户界面的一部分，可以反复使用。片段管理自己的布局，有自己的生命周期。由于片段是更大的用户界面的一小部分，它只能在一个活动或另一个片段中初始化。因此，如果我们希望显示任何类型的资源，如字符串或片段中的图像，我们需要在活动中声明它们，然后将其传递给片段。因此，在本文中，我们将向您展示如何将数据从活动传递到片段。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 **Kotlin** 中演示了该应用程序，因此在创建新项目时，请确保选择 Kotlin 作为主要语言。

**第二步:在布局文件夹**中创建自定义片段布局(my_custom_fragment.xml)

我们将向片段传递一个字符串。为了显示这个字符串，我们实现了一个文本视图。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical">

    <!-- TextVIew to display the passed text -->
    <TextView
        android:id="@+id/fragmentTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:textColor="@color/white"
        android:textSize="50sp"
        android:background="#0f9d58"/>

</LinearLayout>
```

**第三步:在布局文件(activity_main.xml)中添加 EditText、Button 和 Frame**

为了更好的理解，请参考代码内部的注释。

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

    <!-- We will type text in this EditText -->
    <EditText
        android:id="@+id/editText"
        android:layout_width="match_parent"
        android:layout_height="50sp"/>

    <!-- Click this button to pass text 
         in EditText to the Fragment -->
    <Button
        android:id="@+id/button"
        android:layout_below="@+id/editText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:text="Pass"/>

    <!-- Text will be displayed in a
          TextView in this Fragment -->
    <FrameLayout
        android:id="@+id/frameLayout"
        android:layout_below="@+id/button"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

</RelativeLayout>
```

**第 4 步:为自定义片段(MyCustomFragment.kt)创建一个类**

这是一个自定义片段类，用于扩展主活动中框架布局中的自定义布局。

## 我的锅

```
import android.os.Bundle
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView
import androidx.fragment.app.Fragment

class MyCustomFragment: Fragment() {

    // Declaring TextView fro the custom fragment layout
    private lateinit var myTextView: TextView

    // Override function when the view is being created
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View {

        // Inflates the custom fragment layout
        val view: View = inflater.inflate(R.layout.my_custom_fragment, container, false)

        // Finds the TextView in the custom fragment
        myTextView = view.findViewById<View>(R.id.fragmentTextView) as TextView

        // Gets the data from the passed bundle
        val bundle = arguments
        val message = bundle!!.getString("mText")

        // Sets the derived data (type String) in the TextView
        myTextView.text = message

        return view
    }
}
```

**第 5 步:初始化 MyCustomFragment 类，并从 EditText (MainActivity.kt)** 传递值

在这个程序中，编辑文本值(输入字符串)是通过点击按钮获取的。自定义片段类被初始化，输入字符串被传递以获得期望的结果。为了更好的理解，请参考下面代码中的注释。

## 我的锅

```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declaring and initializing the EditText and Button from the layout
        val mEditText = findViewById<EditText>(R.id.editText)
        val mButton = findViewById<Button>(R.id.button)

        // Declaring fragment manager from making data
        // transactions using the custom fragment
        val mFragmentManager = supportFragmentManager
        val mFragmentTransaction = mFragmentManager.beginTransaction()
        val mFragment = MyCustomFragment()

        // On button click, a bundle is initialized and the 
        // text from the EditText is passed in the custom
        // fragment using this bundle
        mButton.setOnClickListener {
            val mBundle = Bundle()
            mBundle.putString("mText",mEditText.text.toString())
            mFragment.arguments = mBundle
            mFragmentTransaction.add(R.id.frameLayout, mFragment).commit()
        }
    }
}
```

**输出:**

我们可以看到，当在编辑文本中键入文本并单击按钮时，相同的文本会显示在我们的自定义片段中。

<video class="wp-video-shortcode" id="video-658513-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210803100616/1211.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210803100616/1211.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210803100616/1211.mp4)</video>