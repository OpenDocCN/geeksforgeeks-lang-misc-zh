# 柯特林验尸官暂停功能

> 原文:[https://www . geeksforgeeks . org/suspend-function-in-kot Lin-coroutines/](https://www.geeksforgeeks.org/suspend-function-in-kotlin-coroutines/)

**先决条件:** [安卓系统上的科特林卡罗廷](https://www.geeksforgeeks.org/kotlin-coroutines-on-android/)

[科特林](https://www.geeksforgeeks.org/kotlin-programming-language/)团队将花冠定义为“**轻质螺纹**”。它们是实际线程可以执行的任务。Coroutines 在 1.3 版本中被添加到 Kotlin 中，并且是基于其他语言的既定概念。Kotlin coroutines 引入了一种新的并发风格，可以在 Android 上使用来简化异步代码。

> ***官方文件称，花冠是轻量级线程。通过轻量级，** **意味着创建协同程序不会分配新的线程。相反，它们使用预定义的线程池和智能调度来决定下一步执行哪个任务以及以后执行哪个任务**。*

### 科特林的暂停功能

挂起功能是可以启动、暂停和恢复的功能。暂停函数需要记住的最重要的一点是，它们只允许从一个[协同函数](https://www.geeksforgeeks.org/kotlin-coroutines-on-android/)或另一个暂停函数中调用。下面给出了一个例子，在这个例子中，我们试图从 coroutine 之外调用 **delay()** 函数。

## 科特林

```
// sample kotlin program to show use of delay function
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // will throw a error
        delay(1000L)

        GlobalScope.launch{
         // delay function (a suspend function) must called within coroutine
         // or another suspend function
        } 
    }
}
```