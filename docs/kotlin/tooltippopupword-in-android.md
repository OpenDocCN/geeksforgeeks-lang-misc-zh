# Android 中的工具弹出词

> 原文:[https://www.geeksforgeeks.org/tooltippopupword-in-android/](https://www.geeksforgeeks.org/tooltippopupword-in-android/)

本文在安卓中增加了 **ToolTipopupWord** 。基本上，它是一个弹出窗口，当一个单词或一些文本被长按或鼠标悬停在它上面时出现。任何消息都可以添加到单词中，以向用户提供更多细节。这个弹出窗口是非常可定制的。当应用程序使用图标来表示动作或信息以节省布局空间时，这很有用。如果必须制作一个**读书应用程序**，并且开发者希望如果用户点击某个单词，它会向用户显示关于所选单词的简短描述，那么可以使用这个视图。此外，[工具提示](https://developer.android.com/guide/topics/ui/tooltips)可用于查看单词的简短信息，但不能添加自定义布局，并且用户必须长按屏幕才能显示工具提示，这可能会激怒用户。这就是**tooltipopupword**的默认布局。

![](img/416a08292405c9a5dd49babd7a153202.png)

**优势:**T2】

*   任何单词都可以从文本中选择。
*   将显示基于所选单词的弹出窗口。
*   布局的各种功能，如文本大小，字体，颜色，背景和对齐可以定制
*   工具弹出窗口和箭头可以自定义。

### 方法:

**步骤 1:** 在你的根[中添加支持库**build.gradle**T5】文件(不是你的模块 build . gradle 文件)。这个库 **jitpack** 是一个新颖的包存储库。它是为 JVM 而做的，这样在](https://www.geeksforgeeks.org/android-build-gradle/) [github](https://www.geeksforgeeks.org/ultimate-guide-git-github/) 和 [bigbucket](https://www.geeksforgeeks.org/bitbucket-vs-github-vs-gitlab/) 中存在的任何库都可以直接在应用程序中使用。

## 可扩展标记语言

```kt
allprojects {          
 repositories {          
        maven { url 'https://jitpack.io' }          
     }         
}          
```

**第二步:**在 [**build.gradle**](https://www.geeksforgeeks.org/android-build-gradle/) 文件中添加支持库，并在依赖项部分添加依赖项。它允许开发人员在 XML 文件中直接添加 ToolTipopupWord。

## 可扩展标记语言

```kt
dependencies {          
  implementation 'com.github.EusebiuCandrea:ToolTipPopupWordTV:1.0.1'         
}         
```

**输出:**

<video class="wp-video-shortcode" id="video-458511-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200717103053/Record_2020-07-17-10-27-30_a20e20bba8cfd8e40615600f802d7c671.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20200717103053/Record_2020-07-17-10-27-30_a20e20bba8cfd8e40615600f802d7c671.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200717103053/Record_2020-07-17-10-27-30_a20e20bba8cfd8e40615600f802d7c671.mp4)</video>

**参考资料:**[https://github . com/eusebiucandrea/tooltip word TV](https://github.com/EusebiuCandrea/ToolTipPopupWordTV)