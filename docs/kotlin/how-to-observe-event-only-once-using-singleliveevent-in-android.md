# 如何在安卓系统中使用 SingleLiveEvent 只观察一次事件？

> 原文:[https://www . geesforgeks . org/how-observing-event-only-use-single live event-in-Android/](https://www.geeksforgeeks.org/how-to-observe-event-only-once-using-singleliveevent-in-android/)

您是否遇到过[对话框](https://www.geeksforgeeks.org/android-alert-dialog-box-and-how-to-create-it/)或[滚动条](https://www.geeksforgeeks.org/how-to-add-a-snackbar-in-android/)在被触发/显示或取消后，在设备旋转后再次被触发/显示的情况？这很可能与使用实时数据观察点在[视图模型](https://www.geeksforgeeks.org/viewmodel-in-android-architecture-components/)和[活动/片段](https://www.geeksforgeeks.org/difference-between-a-fragment-and-an-activity-in-android/)之间进行通信有关。

### 模式的反面

将 LiveData 对象用于事件可能被认为是一个糟糕的设计选择，尤其是当事件只需要一次时。我们可以使用一些布尔标志来帮助视图确定对话框/滚动条是否应该被触发/显示。然而，这可能会导致一个难以理解和维护的解决方案，并且没有吸引力。**可以看到它有直播数据的类型，数据是持续消耗的，但是我们只想得到一次**。

**没有内存泄漏:**

观察器与生命周期对象相关联，当它们所连接的生命周期被破坏时，它们会自行清理。

**没有因活动停止而发生事故:**

如果观察器的生命周期是空闲的，就像在后栈活动的情况下一样，它不会接收任何 LiveData 事件。LiveData 只是遵循观察者的设计，我不认为上述用例保证了它自己的可观察类的变体。那么，我们如何解决对话问题呢？我们不应该改变 LiveData 的行为，我们应该坚持 MVVM 范式的基本原则，如果有必要，让 ViewModel 告诉 ViewModel 关于被忽略的对话。此后，虚拟机可能会重置或更改事件的状态。我意识到很容易忘记提醒视图模型，我们正在增加视图的责任。但是，毕竟视图的工作是:通知虚拟机任何用户操作。

### 如何实现这一点？

创建一个通用的“事件”类(可以称之为 LiveEvent)。给它 observe(所有者，观察者)和 observeForever 函数(观察者)。赋予它与 LiveData 相同的合同和功能。除此之外，LiveEvent 只是在发送数据的同时通知活动观察者，而不是持久值。

## 科特林

```kt
class LiveEvent<C> {
...
  fun sendingValue(data: C) {
    observers.forEach { gfg ->
      if (gfg.isActive()) gfg.onChanged(data)
    }
  }
}
```

如果你想利用 LiveEvent 来发布通知、滚动条或许多屏幕上的任何东西，就把它放在你的基本视图模型类中。然后，在您的基本片段类中初始化视图模型后，观察那个 LiveEvent。

## 科特林

```kt
abstract class GeeksforGeeksViewModel : ViewModel() {
  protected val fireAlertedEvent = LiveEvent<FireAlert>()
}
abstract class BaseFragment : Fragment() {
  fun onViewModelInitialized() {
    viewModel.fireAlertedEvent.observe(this, { fireAlert ->
      fireAlert.show()
    }
  }
}
class GeeksforGeeksSample : GeeksforGeeksViewModel() {
  fun onSaveSuccess() {
    fireAlertedEvent.postValue(FireAlert("yay! we got your stuff!"))
  }
}
```

### 结论

最佳解决方案是在销毁时自动取消订阅的事件源，只要没有观察者在场，它就将事件排队，然后将所有事件发送给第一个订阅的观察者。能够以它认为合适的任何方式处理事件。当您需要管理流程时，使用带有不同成功/失败方法的回调是一个糟糕的想法。利用一个 ADT(密封类)。