# 安卓中与 LiveData 的数据绑定

> 原文:[https://www . geesforgeks . org/data-binding-with-live data-in-Android/](https://www.geeksforgeeks.org/data-binding-with-livedata-in-android/)

**先决条件:**

*   [Data binding](https://www.geeksforgeeks.org/overview-of-data-binding-in-android-architecture-components/)
*   [Real-time data](https://www.geeksforgeeks.org/livedata-in-android-architecture-components/) and [View model](https://www.geeksforgeeks.org/viewmodel-in-android-architecture-components/)

那么，为什么我们要在 LiveData 中使用数据绑定呢？事实上，如果我们希望我们的视图直接与视图模型(数据源)通信，我们可以简单地不使用实时数据来实现。但是，如果视图模型中的数据发生变化，它将不会反映其视图。这是我们可以借助 LiveData 的地方，只要数据有任何变化，就会自动更新视图。

### 履行

我们需要将视图模型中的数据声明为实时数据，我们可以使用可变的实时数据(最常见的)它只是一个扩展实时数据的类。

## 科特林

```kt
class MainViewModel : ViewModel() {
    var text = MutableLiveData(" Welcome to my application ")

    fun updateText() {
        text.value = " Text is updated successfully "
    }
}
```