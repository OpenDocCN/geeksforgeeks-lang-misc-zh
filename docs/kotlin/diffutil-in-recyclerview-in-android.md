# 安卓回收视图中的 DiffUtil

> 原文:[https://www . geeksforgeeks . org/diffutil-in-recycle view-in-Android/](https://www.geeksforgeeks.org/diffutil-in-recyclerview-in-android/)

你在安卓系统中创建过列表吗？你用什么做的？[列表视图](https://www.geeksforgeeks.org/android-listview-in-kotlin/)或[回收视图](https://www.geeksforgeeks.org/android-recyclerview-in-kotlin/)是两种类型的视图。如果你是安卓开发者，你肯定在某个时候使用过回收视图。在本文中，我们将介绍如何使用 DiffUtils 更新 RecyclerView。**回收视图到底是什么？**recycle view 是 ListView 适应性更强、效率更高的版本。它是一个容器，用于显示更大的数据集视图，可以回收和滚动非常快。**在进入 Diff Util 之前，我们先来看一下 RecyclerView 的实现。**

### **简要回顾实施情况**

让我们创建一个 Activity MainActivity，并在 activity main.xml 文件中包含以下代码:

## 【XML】

```kt
<androidx.constraintlayout.widget.ConstraintLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:tools="http://schemas.android.com/tools"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  tools:context=".GeeksforGeeksActivity">

  <androidx.recyclerview.widget.RecyclerView
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/gfgRecyclerView"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintLeft_toLeftOf="parent"
    app:layout_constraintRight_toRightOf="parent"
    app:layout_constraintTop_toTopOf="parent"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

现在让我们创建一个数据模型类和一个数据源，

## 我的锅

```kt
data class GeeksCourses(val courseNumber: Int, val courseRating: Int, val courseName: String)
```

而数据来源似乎是，

## 科特林

```kt
object geeksforGeeks {
    val courseList: List<Course>
        get() {
            val course = ArrayList<Rating>()
            course.add(Rating(1, 10, "GeeksforGeeks"))
            course.add(Rating(2, 12, "Android Dev"))
            course.add(Rating(3, 5, "DSA"))
            return course
        }
}
```

现在让我们制作一个适配器来设置 RecyclerView 中的列表。

## 科特林

```kt
class CourseAdapter : RecyclerView.Adapter<CourseAdapter.ViewHolder>() {
    private val courses = ArrayList<Course>()
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val inflater = LayoutInflater.from(parent.context)
        val view = inflater.inflate(R.layout.course_list, parent, false)
        return ViewHolder(view)
    }
    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        val Course = courses[position]
        holder.name_text.text = Course.name
    }
    fun setData(courses: List<Course>) {
       courses.clear()
       courses.addAll(courses)
    }
    override fun getItemCount(): Int {
        return courses.size
    }
    class ViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
        val name_text: TextView = itemView.findViewById(R.id.name_text)
    }
}
```

**如果我们需要用新的信息更新列表呢？**

我们就称之为，

## 【科特林】

```kt
adapter.setData(/** any new data on courses**/)
```