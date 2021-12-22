# 如何在安卓中通过编程改变 EditText 的输入类型？

> 原文:[https://www . geeksforgeeks . org/如何更改输入类型-编辑文本-在 android 中以编程方式输入/](https://www.geeksforgeeks.org/how-to-change-input-type-of-edittext-programmatically-in-android/)

安卓用户界面或应用程序中的编辑文本是一个输入字段，用于向应用程序提供输入文本。该输入文本可以是多种类型，如文本(字符)、数字(整数)等。这些字段可用于接受用户的文本输入，以执行任何所需的操作。假设，我们应用程序中的登录活动包括两个输入，即电子邮件 id 和数字 pin。因此，我们需要创建两个编辑文本字段来接受这两个输入。这就是一般登录活动页面的假设。但是，我们可以使用单个 EditText 创建一个类似的活动，并使用它两次来获取两种相同或不同类型的输入。第一个输入可以存储在一个变量中，只需点击一下按钮。同时，此点击将清除编辑文本。现在，第二次输入可以在按钮点击时给出并存储在另一个变量中。这样，我们将使用单个编辑文本获得两个输入。这是当两个输入属于同一类型时。当两种输入类型不同时，比如说，第一种输入是字符串，第二种输入是数值，就会出现问题。因此，在本文中，我们将向您展示如何使用简单的安卓应用程序演示以编程方式更改编辑文本输入类型。启动集成开发环境后，请遵循以下说明。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 **Kotlin** 中演示了该应用程序，因此在创建新项目时，请确保选择 Kotlin 作为主要语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** ，并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。我们创建了一个[编辑文本](https://www.geeksforgeeks.org/android-edittext-in-kotlin/)和两个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)。单击这两个非功能按钮时，将相应地调用编辑文本输入类型。

## 可扩展标记语言

```
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/edit_text"
        android:layout_width="match_parent"
        android:layout_height="50sp"/>

    <Button
        android:id="@+id/textBtn"
        android:layout_above="@id/numBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:text="text"/>

    <Button
        android:id="@+id/numBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="number"/>

</RelativeLayout>
```

**第三步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。编辑文本和按钮被声明到主代码中。在这里，这两个函数被赋予了这样的功能:当单击时，编辑文本将改变其输入类型。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.text.InputType
import android.widget.Button
import android.widget.EditText

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declaring and initializing the EditText
          // and Buttons from the layout file 
        val mEditText = findViewById<EditText>(R.id.edit_text)
        val mTextBtn = findViewById<Button>(R.id.textBtn)
        val mNumBtn = findViewById<Button>(R.id.numBtn)

        // When this button is clicked, the 
          // EditText input type will change to Text
        mTextBtn.setOnClickListener {
            mEditText.inputType = InputType.TYPE_CLASS_TEXT
        }

        // When this button is clicked, the 
          // EditText input type will change to Numbers
        mNumBtn.setOnClickListener {
            mEditText.inputType = InputType.TYPE_CLASS_NUMBER
        }
    }
}
```

**输出:**

您可以在输出中看到，当单击这些按钮时，输入类型会发生变化。

<video class="wp-video-shortcode" id="video-728386-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210816204127/o103.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210816204127/o103.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210816204127/o103.mp4)</video>