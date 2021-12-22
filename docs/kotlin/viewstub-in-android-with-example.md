# 安卓中的视图存根，示例

> 原文:[https://www . geeksforgeeks . org/views stub-in-Android-with-example/](https://www.geeksforgeeks.org/viewstub-in-android-with-example/)

在安卓中，视图存根是一个零大小的不可见视图，非常灵活，我们可以在运行时懒洋洋地膨胀布局资源。这是一个愚蠢和轻量级的视图，它没有维度。根据需要，无论何时需要，我们都可以在运行时充气。当有复杂的视图需要处理时，这是一个经典的例子。当视图存根膨胀时，它会用膨胀的布局资源替换父视图中的自己。仅当调用**设置可见性(int)** 或**膨胀()**时，其可见性才会存在于视图层次结构中。使用布局参数将膨胀的视图添加到视图存根的父视图中。每当**有项目详情、撤销消息或进度指示器**时，我们就能想到 ViewStub。**它通过仅在需要时加载视图**来减少内存使用并加快渲染速度。人们可以认为它看起来类似于 include tag，但事实并非如此。Include 标记包含布局文件夹下的 XML 文件中的内容。因此，我们可以分别拥有页眉、页脚、左栏和右栏 XMLs，但它们仍然通过使用包含标记包含在主 XML 中。另一方面，视图存根不包括在内，但是当设置为**设置可见性(int)** (对于真选项)或调用膨胀()时，它会直接被加载。

### **重要方法**

首先，让我们获取视图存根的引用

XML 格式的视图存根:

```
<ViewStub
    android:id="@+id/viewStubToLearn"
    android:layout_width="fill_parent"
    android:layout_height="wrap_content"
    android:layout_marginTop="100dp"
    android:inflatedId="@+id/inflatedviewsub"
    android:layout="@layout/custom_viewstub"
 />
```