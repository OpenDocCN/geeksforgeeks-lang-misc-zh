# 带演示应用的安卓意图过滤器

> 原文:[https://www . geesforgeks . org/intent-filter-in-Android-with-demo-app/](https://www.geeksforgeeks.org/intent-filter-in-android-with-demo-app/)

[意图](https://www.geeksforgeeks.org/what-is-intent-in-android/)是一个消息对象，它告诉要执行哪种操作。意图最重要的用途是活动的启动。意图有助于组件之间的通信。

> **注:** App 组件是 App 的基本构件。

### **意图的基本用例**

**开始活动**

一个活动代表应用程序中的单个屏幕，绕过意图实例，我们可以开始一个活动。

**例:**

## 科特林

```kt
var intent = Intent(this, SecondActivity:: class.java)
startIntent(intent)
```

您可以使用 putExtra()添加额外的信息。

**启动服务**

服务是在没有用户界面的情况下在后台执行操作的组件，也称为后台进程。

**发送广播**

广播是任何应用程序都能接收到的消息。在安卓系统中，该系统提供各种广播系统事件，如设备开始充电、禁用或启用飞机模式等。

### 意图类型

有两种意图

1.  **显式意图:**显式意图可以执行由代码设置的特定应用程序操作，如更改活动，在显式意图中，用户知道所有的事情，如单击按钮后将启动哪个活动，显式意图用于应用程序内部的通信
2.  **隐式意图:**隐式意图不像显式意图那样命名特定组件，而是声明要执行的一般操作，这允许来自另一个应用程序的组件进行处理。

例如:当您轻按任何应用程序中的共享按钮时，您可以看到 Gmail、蓝牙和其他共享应用程序选项。

### **意图过滤器**

*   隐式意图使用意图过滤器来服务用户请求。
*   意图过滤器指定活动、服务或广播接收器可以响应的意图类型。
*   意图过滤器在安卓清单文件中声明。
*   意图过滤器必须包含

**示例:**

## XML

```kt
<intent-filter
  android:icon="drawable resource"
  android:label="string resource"
  android:priority="integer" >
   . . .
</intent-filter>
```

大部分意图过滤器都是通过其

1.  **< Action >**
2.  **< Category >** and
3.  **< Data >** .

### **1。<行动>**

**语法:**

## 【XML】

```kt
<action android:name="string" />
```

向意图过滤器添加操作。一个<intent-filter>元素必须包含一个或多个<action>元素。如果意图过滤器中没有<action>元素，则过滤器不接受任何意图对象。</action></action></intent-filter>

**常见动作示例:**

*   **Action _ view:** When you have some activities to display information to users, such as displaying images in the gallery application or displaying the address to be viewed in the map application.
*   **Action _ send:** When you have some data that users can share through another application (such as email application or social sharing application), you should use this action in startActivity ().

### **2。<类别>**

**语法:**

## XML

```kt
<category android:name="string" />
```