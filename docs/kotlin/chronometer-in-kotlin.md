# 科特林的计时器

> 原文:[https://www.geeksforgeeks.org/chronometer-in-kotlin/](https://www.geeksforgeeks.org/chronometer-in-kotlin/)

安卓**计时器**是用户界面控件，在视图中显示计时器。我们可以使用计时器小部件轻松启动带基本时间的向上或向下计数器。默认情况下， **start()** 方法可以假定基准时间并启动计数器。
一般来说，我们可以在 XML 布局中创建使用**计时器**的小部件，但是我们也可以通过编程来实现。

首先，我们按照以下步骤创建一个**新项目**:

1.  点击**文件**，然后**新建** = > **新建项目**。
2.  之后加入 Kotlin 支持，点击下一步。
3.  根据方便选择最小 SDK，点击下一步按钮。
4.  然后选择**清空**活动= > **下一个** = > **完成**。

## 计时器小部件的不同属性

<figure class="table">

| XML 属性 | 描述 |
| --- | --- |
| android:id | 用于指定视图的 id。 |
| 安卓:文本对齐 | 用于下拉列表中的文本对齐。 |
| 安卓:背景 | 用于设置视图的背景。 |
| 安卓:填充 | 用于设置视图的填充。 |
| 安卓:可见性 | 用于设置视图的可见性。 |
| 安卓:重力 | 用于指定视图的重心，如中心、顶部、底部等 |
| 安卓:格式 | 用于定义要显示的字符串的格式。 |
| 安卓:倒计时 | 用于定义计时器是递增计数还是递减计数。 |

</figure>

## 修改 activity_main.xml 文件

在这个文件中，我们使用计时小部件和一个按钮来启动或停止计时器，并为它们设置属性。

## Java 语言(一种计算机语言，尤用于创建网站)

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:id="@+id/constraint_layout">

    <Chronometer
        android:id="@+id/c_meter"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20dp"
        android:layout_marginStart="68dp"
        android:layout_marginTop="256dp"
        android:layout_marginEnd="68dp"
        android:layout_marginBottom="28dp"
        android:textAppearance="@style/TextAppearance.AppCompat.Large"
        android:textColor="#092FEC"
        android:textSize="36sp"
        app:layout_constraintBottom_toTopOf="@+id/btn"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="163dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="163dp"
        android:text="@string/start"
        app:layout_constraintEnd_toEndOf="@id/c_meter"
        app:layout_constraintHorizontal_bias="0.485"
        app:layout_constraintStart_toEndOf="@+id/c_meter"
        app:layout_constraintStart_toStartOf="@id/c_meter"
        app:layout_constraintTop_toBottomOf="@+id/c_meter" />

</androidx.constraintlayout.widget.ConstraintLayout>
```