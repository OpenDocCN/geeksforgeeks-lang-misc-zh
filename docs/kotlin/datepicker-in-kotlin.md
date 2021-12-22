# 科特林的日期选择器

> 原文:[https://www.geeksforgeeks.org/datepicker-in-kotlin/](https://www.geeksforgeeks.org/datepicker-in-kotlin/)

安卓**日期选择器**是一个用户界面控件，用于在我们的安卓应用中按日、月、年选择日期。日期选择器用于确保用户选择有效的日期。
在具有**两个**模式的安卓日期选择器中，第一个显示完整的日历，第二个显示微调视图中的日期。
我们可以通过两种方式创建一个日期选择器控件，要么在 XML 文件中手动创建，要么在 Activity 文件中以编程方式创建。
首先我们按照以下步骤创建一个**新项目【T8:** 

1.  点击文件，然后**新建** = > **新项目**。
2.  之后加入 Kotlin 支持，点击下一步。
3.  根据方便选择最小 SDK，点击下一步按钮。
4.  然后选择**清空**活动= > **下一个** = > **完成**。

## 带日历模式的安卓日期选择器

我们可以使用**安卓:datepikermode**只显示日历视图。在下面的例子中，我们在日历模式下使用日期选择器。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
<DatePicker
    android:id="@+id/datePicker"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:datePickerMode="calendar"/>
```