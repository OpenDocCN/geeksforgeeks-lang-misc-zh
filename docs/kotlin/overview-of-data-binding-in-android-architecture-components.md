# 安卓架构组件中数据绑定概述

> 原文:[https://www . geeksforgeeks . org/Android 架构中数据绑定概述-组件/](https://www.geeksforgeeks.org/overview-of-data-binding-in-android-architecture-components/)

本文描述了数据绑定和 MVVM 设计模式及其组件背后的思想。如果你想亲自尝试，用意大利面条代码打开一个旧项目。如果你没有，你可以从 [GitHub](https://github.com/the-rebooted-coder/Take-Notes) 获得一个。然后，尝试使用本文中介绍的 MVVM 组件。

**在某些方面，软件开发在过去十年中没有太大变化。本质上的挑战保持不变:**

*   Write clean code.
*   Various architectural styles.
*   Test code.
*   Create an excellent user experience.
*   The speed of developing features is beyond the consideration of product management department.

当安卓进入市场时，所有这些问题都有了答案。桌面和 web 应用程序开发人员已经有了编写用户界面的知识领域。这些解决方案也适用于安卓系统，但它们离理想还很远。

安卓最初支持 Java，应用通常使用 [MVC(模型视图控制器)](https://www.geeksforgeeks.org/mvc-model-view-controller-architecture-pattern-in-android-with-example/)实现。十年后，有了柯特林……&有了 [MVVM](https://www.geeksforgeeks.org/mvvm-model-view-viewmodel-architecture-pattern-in-android/) 还有数据绑定。因此，这十年是一段漫长的旅程，让我们一起来追吧！

### 使用数据绑定

数据绑定作为一个单独的术语，是指连接来自最终消费者和用户的数据，然后保持它们同步的技术。安卓的数据绑定库允许开发人员将用户界面保留在布局 XML 文件中，并从中生成代码。该库还负责将视图与来自视图模型的数据同步。为了给你的普通安卓项目添加数据绑定，你需要在你的应用的 [build.gradle](https://www.geeksforgeeks.org/android-build-gradle/) 文件中添加以下几行:

```
android {
...
dataBinding {
  enabled = true
  }
}
```

将数据绑定元素设置为“真”后，您需要将其添加到您的 XML 文件中，如:

## 【XML】

```
<layout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto">
    <data>
        <variable
            name="user"
            type="com.geeksforgeeks.example" />
    </data>
    <ConstraintLayout... /> <!-- Your UI layout's root element -->
</layout>
```

将上述代码添加到您的 XML 中后，您可以使用 [**【实时数据】**](https://www.geeksforgeeks.org/livedata-in-android-architecture-components/) 向用户界面通知数据更改:

与实现可观察元素(如:可观察文本字段)的对象不同，实时数据对象实现了订阅信息更改的观察者的生命周期。这些数据带来了许多好处，这在使用 LiveData 的优势中有所解释。在安卓工作室 3.1 及更高版本中，您将在数据绑定代码中用 LiveData 对象替换可观察字段。

## 爪哇

```
class ViewModelActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {

          // Inflating the view to obtain an instance
        UserBinding binding = DataBindingUtil.setContentView(this, R.layout.gfg);

        // Specifying the present (current) activity as the parent
        binding.setLifecycleOwner(this);
    }
}
```

## 科特林

```
class ViewModelActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {

      // Inflating the view to obtain an instance
      val binding: UserBinding = DataBindingUtil.setContentView(this, R.layout.gfg)

      // Specifying the present (current) activity as the parent 
      binding.setLifecycleOwner(this)
    }
}
```

### 为什么绑定到实时数据？

使用生命周期感知组件(如 LiveData)的优势包括:

1.  Since the activity stops, there will be no crash. If the observer's life cycle is inactive, such as when an activity is in the back stack, it will not receive any LiveData events.

2.  **No** memory leak. No, the subscription must be processed manually. When the observer's related life cycle is destroyed, they will pack it by themselves.

### 一句警告

使用双向数据绑定时，注意不要引入无限循环。当用户改变属性时，被注释的战术 **@InverseBindingAdapter** 被命名。这反过来会调用战术注释 **@BindingAdapter** ，这可能会触发对战术注释 **@InverseBindingAdapter** 的另一个调用，以此类推。因此，通过比较注释的方法 **@BindingAdapter 中的新值和旧值来中断可能的无限循环是很重要的。**

### 一些最后的想法

安卓组件的生命周期很复杂，手动管理可能会很麻烦，因为要让用户界面与数据源保持同步，因此引入 LiveData，可能是生命周期管理的一大强化。在考虑到配置和生命周期状态的情况下，数据源中的更改通常会自动传播到用户界面，在这种意义上，将数据绑定添加到项目中可以使代码更加简洁和被动。然而，您使用数据绑定库不应该仅仅受限于将知识模型的属性设置到文本字段中。使用单向和双向绑定绑定到 LiveData 将允许您形成观察者模式和生命周期感知的最重要部分。