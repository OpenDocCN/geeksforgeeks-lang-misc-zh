# 在安卓系统中使用 onTouchListener 对象三次点击视图

> 原文:[https://www . geeksforgeeks . org/三次点击查看使用-ontouchlistener-object-in-Android/](https://www.geeksforgeeks.org/triple-tap-on-a-view-using-ontouchlistener-object-in-android/)

以检测三次点击，即每当用户在任何视图上三次点击时，如何检测它，并且根据该视图，可以添加对应于它的响应。这里显示了一个例子，其中用户在视图上三次点击，它被检测到，并且对应于视图响应以吐司的形式被添加。

**第一步:**在安卓工作室创建一个空活动。创建一个，遵循这篇文章-[https://www . geeksforgeeks . org/Android-如何创建-启动-一个新的项目-在 android-studio/](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/) 。检查选择的主要语言是否为**科特林。**

**步骤 2:**activity _ main . XML 中没有进行任何更改。因为已经存在一个 textview，所以三次点击的响应也随之添加。

## XML

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Click Here"
        />

</RelativeLayout>
```