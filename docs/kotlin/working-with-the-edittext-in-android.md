# 在安卓中使用编辑文本

> 原文:[https://www . geeksforgeeks . org/与安卓版合作/](https://www.geeksforgeeks.org/working-with-the-edittext-in-android/)

[EditText](https://www.geeksforgeeks.org/edittext-widget-in-android-using-java-with-examples/) 是基本的 UI 小部件之一，用于从用户处获取输入。编辑文本是安卓系统中文本视图的派生或扩展。本文详细讨论了安卓系统中的编辑文本。本文还包含了对其他文章的一些重定向，也可以参考它们来获得 Android 中 EditText 小部件的详细视角。看看下面的列表，了解一下整个讨论。

1.  **Input type of editing text**
2.  **Get data or retrieve data input by users**
3.  **User-defined input data**
4.  **Add a hint to the placeholder**
5.  **Change the stroke color**
6.  **Change the highlighted color in the edited text**
7.  **Event Listener [T2 Text]**

## **安卓中 EditText 的详细视角**

**第一步:创建一个空的活动项目**

*   Create an empty active Android Studio project. Refer to [How to create/start a new project in Android Studio](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/) to learn how to create an empty active Android project.

**步骤 2:使用 activity_main.xml 文件**

*   The main layout of the application contains EditText Widget and two buttons. To implement the user interface, call the following code in the **active file. Understand what basic EditText looks like in android.**

## XML

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    tools:ignore="HardcodedText">

    <EditText
        android:id="@+id/editText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginEnd="16dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.321" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:backgroundTint="@color/green_500"
        android:text="SUBMIT"
        android:textColor="@color/white"
        app:layout_constraintEnd_toEndOf="@+id/editText"
        app:layout_constraintTop_toBottomOf="@+id/editText" />

    <Button
        style="@style/Widget.AppCompat.Button.Borderless"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="8dp"
        android:backgroundTint="@color/green_500"
        android:text="CANCEL"
        android:textColor="@color/green_500"
        app:layout_constraintEnd_toStartOf="@+id/button"
        app:layout_constraintTop_toBottomOf="@+id/editText" />

</androidx.constraintlayout.widget.ConstraintLayout>
```