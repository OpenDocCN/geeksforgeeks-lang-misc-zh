# RxJava 延迟运算符

> 原文:[https://www.geeksforgeeks.org/rxjava-defer-operator/](https://www.geeksforgeeks.org/rxjava-defer-operator/)

在本文中，我们将了解 RxJava 延迟运算符。根据我们的用例，我们将知道何时使用延迟操作符。我们经常在使用 RxJava 延迟运算符时出错。让我们直说吧，这样我们就不会出错了。

**根据文件:**

> **延迟:**等到观察者订阅后再创建可观测值，为每个观察者建立一个新的可观测值。

因此，在这种情况下，我们将使用一个例子来了解 RxJava 的延迟运算符。假设我们有一个 **GfG 类，如下所示:**

## 我的锅

```
class GfG {
    var course: String = "DSA"

    fun getCourseObservable(): Observable<String> {
        return Observable.just(course)
    }

    fun getCourseDeferObservable(): Observable<String> {
        return Observable.defer {
            return@defer Observable.just(course)
        }
    }

}
```

我们在上面描述的 GfG 类中有两种方法:

1.  **getcourseconomous()**:这个函数只需使用 Observable.just(当然)返回 Observable <字符串>。
2.  **getcoursederatobservable()**:可观察的<字符串>是通过使用可观察的. just(当然)返回的，但是被封装在可观察的 defer()中。

**现在，让我们测试这两种方法，看看会发生什么。**

## 我的锅

```
val course = Gfg()
val courseObservable = course.getCourseObservable()
val courseDeferObservable = course.getCourseDeferObservable()
course.price = "DSA"
courseObservable
.subscribe { brand ->
    Log.d("GfGExample", "courseObservable : $course")
}
courseDeferObservable
.subscribe { brand ->
    Log.d("GfGExample", "courseDeferObservable : $course")
}
```

首先，我们要确定价格。然后，使用 price 对象，我们同时使用 getcourseDetailorable 和 getcourseDetailorable 方法来检索可观测值。然后我们将课程的名称指定为“每日生活津贴”接下来，我们订阅了这两个观察点，以确定课程的价格

**上述代码的输出:**

```
GfGExample: courseObservable : DEFAULT
GfGExample: courseDeferObservable : DSA
```

在这里，我们可以看到课程可观测值接收“DEFAULT”作为课程名称，但是课程可观测值接收“DSA”作为课程。因为没有使用 defer 运算符，courseObservable 返回旧值“DEFAULT”。因为使用了延迟运算符，所以 courseDeferObservable 返回最近的值“DSA”它表示延迟直到观察者订阅时才生成可观测值，并且每个观察者都收到一个新的可观测值。

### 结论

**有两个关键点需要记住:**

1.  直到观察者订阅，可观察性才被创建。
2.  对于每个观察者来说，延迟会产生一个新的可观测值。

因此，我们可以利用 RxJava 延迟运算符来解决这个有趣的问题。希望这篇文章帮助你理解题目！