# 在安卓中使用 GSON 库序列化和反序列化 JSON】

> 原文:[https://www . geesforgeks . org/serialize-and-serialize-JSON-using-gson-library-in-Android/](https://www.geeksforgeeks.org/serialize-and-deserialize-json-using-gson-library-in-android/)

当我们需要将一些数据从一个活动发送到另一个活动时，我们可以使用带有 **putExtra()** 功能的 intents。但是我们 putExtra 支持原始数据类型。因此，如果我们需要传递并且用户定义了对象，我们需要首先序列化它，然后将它发送到目的地。接收数据时，我们需要对其进行反序列化。我们将使用 Gson 库将对象序列化和反序列化为 [JSON](https://www.geeksforgeeks.org/javascript-json/) 。

### **分步实施**

**第一步:** [使用 kotlin 在 android studio 中创建新项目。](https://www.geeksforgeeks.org/how-to-create-project-in-android-studio-using-kotlin/)

**第二步:**创建一个用户自定义的数据类

## 【科特林】

```kt
package com.ayush.serialize_deserialize

data class StudentInfo(val id: Int, val Name :String, val RollNo : Int)
```