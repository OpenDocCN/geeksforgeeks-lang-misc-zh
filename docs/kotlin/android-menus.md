# 安卓菜单

> 原文:[https://www.geeksforgeeks.org/android-menus/](https://www.geeksforgeeks.org/android-menus/)

在安卓系统中，菜单是用户界面组件的重要组成部分，用于提供应用程序的一些常见功能。在菜单的帮助下，用户可以在整个应用程序中体验流畅一致的体验。

为了使用菜单，我们应该在单独的 XML 文件中定义它，并根据我们的需求在应用程序中使用该文件。此外，我们可以使用菜单 API 来表示我们的 android 应用程序活动中的用户动作和其他选项。

## 如何在 XML 文件中定义菜单？

安卓工作室为菜单类型提供了标准的 XML 格式来定义菜单项。我们可以简单地在 XML 菜单资源中定义菜单及其所有项目，而不是在代码中构建菜单，还可以在我们的 android 应用程序中使用的活动或片段中将菜单资源加载为菜单对象。

在这里，我们应该在项目目录(res/menu)中创建一个新的文件夹菜单来定义菜单，并添加一个新的 XML 文件来构建包含以下元素的菜单。

下面是在 XML 文件(menu_example.xml)中定义菜单的例子。

```kt
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http:// schemas.android.com/apk/res/android">
    <item android:id="@+id/mail"
        android:icon="@drawable/ic_mail"
        android:title="@string/mail" />
    <item android:id="@+id/upload"
        android:icon="@drawable/ic_upload"
        android:title="@string/upload"
        android:showAsAction="ifRoom" />
    <item android:id="@+id/share"
        android:icon="@drawable/ic_share"
        android:title="@string/share" />
</menu>
```

*   **< menu >** It is the root element that helps to define menu in XML file, and it also saves several elements.
*   **< >** is used to create a menu item. It also contains nested < menu > elements to create submenus.
*   **< Group >** It is an optional and invisible option of < item > element, which is used to classify menu items so that they can share attributes such as activity status and visibility.

## activity _ main . XML

如果我们想在菜单项中添加子菜单，那么我们需要添加一个<菜单>元素作为一个<项>的子元素。

下面是在菜单项中定义子菜单的例子。

```kt
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http:// schemas.android.com/apk/res/android">
    <item android:id="@+id/file"
        android:title="@string/file" >
        <!-- "file" submenu -->
        <menu>
            <item android:id="@+id/create_new"
                android:title="@string/create_new" />
            <item android:id="@+id/open"
                android:title="@string/open" />
        </menu>
    </item>
</menu>
```

## 安卓不同类型的菜单

在安卓系统中，我们有三种类型的菜单可以用来定义我们安卓应用中的一组选项和动作。

安卓应用中的菜单如下–

*   Android options menu
*   Android context menu
*   Android pop-up menu

**安卓选项菜单–**安卓选项菜单是安卓应用中菜单项的主要集合，对于对搜索应用有全局影响的动作非常有用。

**Android Context Menu–**Android Context Menu 是一个浮动菜单，只有当用户长时间点击某个元素时才会出现，对于影响所选内容或上下文框架的元素非常有用。

**安卓弹出菜单–**安卓弹出菜单在垂直列表中显示项目列表，该列表呈现给调用菜单的视图，并且有助于提供与特定内容相关的动作的溢出。