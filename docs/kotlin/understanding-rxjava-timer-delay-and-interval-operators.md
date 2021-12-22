# 了解 RxJava 定时器、延迟和间隔运算符

> 原文:[https://www . geesforgeks . org/understanding-rxjava-timer-delay-and-interval-operators/](https://www.geeksforgeeks.org/understanding-rxjava-timer-delay-and-interval-operators/)

在这篇文章中，我们将学习 RxJava 定时器、延迟和间隔操作符。此外，所有不同的计时器、延迟和间隔操作符的用例将在本文中得到澄清，所以请一直关注到最后。**通过例子，我们将研究以下所有操作。**

*   **Timer**
*   **Delay**
*   **interval**

让我们从 RxJava 计时器操作符开始。当我们想要在一定时间后做某事时，使用 Timer 运算符。

### 计时器操作员示例

## 我的锅

```
Observable.timer(5, TimeUnit.SECONDS)
    .flatMap {
        return@flatMap Observable.create<String> { shooter ->
            Log.d("gfgArticleExampe", "Shoot")
            shooter.onNext("GeeksforGeeks")
            shooter.onComplete()
            // Action to be done when completed 10 secs
        }
    }
    .subscribeOn(Schedulers.io())
    .observeOn(AndroidSchedulers.mainThread())
    .subscribe {
        Log.d("gfgArticleExampe", it)
}
```

上面的例子向我们展示了我们所说的计时器操作符。当我们进入计时器操作器 10 秒钟后，它会以这种方式移动到另一个任务，我们在 10 秒钟内完成任务，并发出值**“geeks forgeeks。”**

> **极客提示#1:** 当我们有一个用例，我们希望在一定时间后完成一项工作，我们可以使用计时器操作符。

现在，我们来看看 **RxJava 延迟算子。**延迟操作器将排放量从可观测值提前一个指定的量。让我们看一个延迟运算符的例子。

### 延迟运算符示例

## 我的锅

```
Observable.create<String> { emitter ->
    Log.d("DelayGFG", "Shoot")
    emitter.onNext("GeeksforGeeks")
    emitter.onComplete()
}
.subscribeOn(Schedulers.io())
.delay(10, TimeUnit.SECONDS)
.observeOn(AndroidSchedulers.mainThread())
.subscribe {
    Log.d("DelayGFG", it)
}
```

我们正在做一些工作，然后发出一个值，但是我们想推迟向订户发出值，所以我们使用了延迟运算符。

> **极客提示#2:** 当我们有一个用例，我们希望先执行工作，然后将排放推迟一段特定的时间，我们可以使用延迟运算符。

让我们看一下 RxJava 区间运算符，它生成一个可观测值，该值发出由时间间隔分隔的整数序列。

### 区间运算符示例

## 我的锅

```
val disposable =
    Observable.interval(1, 10, TimeUnit.SECONDS)
        .flatMap {
            return@flatMap Observable.create<String> { shooter ->
                Log.d("GfGInterval", "Shoot")
                shooter.onNext("GeeksforGeeks")
                shooter.onComplete()
            }
        }
        .observeOn(AndroidSchedulers.mainThread())
        .subscribe {
            Log.d("GfGInterval", it)
        }
compositeDisposable.add(disposable)
```

在这种情况下，任务将在 10 秒钟的延迟后重复。有一点要记住:**会无限期持续下去。**

### **那么如何摆脱这个循环呢？**

嗯，有两种方法可以停止:

*   Using compound configurability.
*   **dispose ()** can be called by the take(n) operator.

### 结论

当我们有一个用例，我们希望以某个时间间隔重复一个作业时，我们可以使用间隔运算符。另一件要记住的事情是，所有的计时器、延迟和间隔操作符都在调度器线程上运行，因此我们不必担心它。为了解决这个有趣的问题，我们可以使用 RxJava 计时器、延迟和间隔运算符。