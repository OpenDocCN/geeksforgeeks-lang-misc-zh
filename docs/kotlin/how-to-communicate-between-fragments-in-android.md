# 安卓中碎片之间如何交流？

> 原文:[https://www . geeksforgeeks . org/安卓碎片间通信方式/](https://www.geeksforgeeks.org/how-to-communicate-between-fragments-in-android/)

现在，大多数应用程序每天都有如此多的功能，以至于它们在一个应用程序中使用多个[片段](https://www.geeksforgeeks.org/introduction-fragments-android/)，通信是应用程序从一个片段到另一个片段共享数据的重要部分之一，因为两个片段不能直接通信。片段代表任何用户界面的一部分。一个活动中可以有多个片段。它们有自己的生命周期。

### **接近**

我们可以通过多种方式在应用程序中进行交流:

*   We can use the **view model** to communicate in clips.
*   We can also use the **interface to communicate between clips.**

在本文中，我们将使用 Kotlin 解释使用接口在片段之间进行通信。

### **分步实施**

**第一步:在你的安卓工作室创建一个新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。请注意，选择 Kotlin 作为编程语言。

**第二步:创建两个空白片段**

导航到**主活动. kt** 所在的项目文件。右键单击该文件夹，然后单击新包，并将其命名为碎片。现在在这个新创建的文件夹中创建两个空白片段，并将它们命名为**片段 1** & **片段 2** 。

**第三步:处理 XML 文件**

导航到**应用程序> res >布局> fragment1.xml** 并将下面的代码添加到该文件中。下面是 **fragment1.xml** 文件的代码。

## XML

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".fragments.Fragment1">

    <!-- Text View for showing Fragment1 text -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Fragment 1"
        android:textSize="40sp"
        android:layout_centerHorizontal="true"
        android:gravity="center"
        android:layout_marginTop="20dp"
        android:textColor="@color/black"/>

    <!-- Edit Text for taking user input -->
    <EditText
        android:id="@+id/messageInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Enter text to Pass"
        android:layout_marginTop="200dp"
        android:gravity="center"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:textSize="30sp"/>

   <!-- Button for submit user response -->
    <Button
        android:id="@+id/sendBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/etText"
        android:text="Submit"
        android:backgroundTint="#0F9D58"
        android:textSize="20sp"
        android:textAllCaps="false"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:layout_marginTop="20dp" />

</RelativeLayout>
```

导航到**应用程序> res >布局> fragment2.xml** 并将下面的代码添加到该文件中。下面是 **fragment2.xml** 文件的代码。

## XML

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".fragments.Fragment2">

    <!-- Text View for showing Fragment2 text -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Fragment 2"
        android:textSize="40sp"
        android:layout_centerHorizontal="true"
        android:gravity="center"
        android:layout_marginTop="20dp"
        android:textColor="@color/black"/>

    <!-- Frame Layout which will replaced by data from Fragment1 -->
    <FrameLayout
        android:id="@+id/frameLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <TextView
            android:id="@+id/displayMessage"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Text"
            android:textSize="30sp"
            android:layout_centerHorizontal="true"
            android:gravity="center"
            android:layout_marginTop="300dp"
            android:textColor="@color/black"/>

    </FrameLayout>

</RelativeLayout>
```