# 如何在安卓中使用 Firebase 通过 GitHub 登录后更新用户的个人资料？

> 原文:[https://www . geesforgeks . org/如何更新-用户-档案-通过 github-使用-firebase-in-android/](https://www.geeksforgeeks.org/how-to-update-users-profile-after-signing-through-github-using-firebase-in-android/)

在本文中，我们将学习更新通过 GitHub 登录应用程序的用户的个人资料。该档案将通过用户的 GitHub 信息更新，如 GitHub Id、姓名、关注者、追随者等。开始吧！

**第一步:**首先设置你的 app，让用户可以通过 GitHub 登录。所以你需要**在 firebase 的帮助下使用 GitHub** 认证用户。为此，请遵循文章中的所有步骤:[在安卓系统中使用 Github 认证用户](https://www.geeksforgeeks.org/authenticate-using-github-on-android/)。

**第二步:更新配置文件**

为此，如下所示，在 signInWithGithubProvider()方法的 else 部分声明一个类型映射<string any="">的变量 say‘user ’,使用[**additionalUserInfo**](https://firebase.google.com/docs/reference/android/com/google/firebase/auth/AdditionalUserInfo)**提取用户的 Github 配置文件信息。**</string>

> **private fun signiwitthgithubprovider(){ 0**
> 
> **。。。**
> 
> **如果{**
> 
> **。。。}**
> 
> **else {**
> 
> **。。。**
> 
> **val 用户:地图 <string any="">= it.additionalUserInfo！！。简介为地图 <string any="">//指 AuthResult！</string></string>**
> 
> **。。。**
> 
> **}**
> 
> **}**

**使用 additionalUserInfo，所有需要的信息将从 MainActivity 发送到 HomePageActivity(使用 Intent)，其中包含用户的配置文件信息。所有代码与本文[中的相同](https://www.geeksforgeeks.org/authenticate-using-github-on-android/)找出不同之处，并添加更新用户配置文件所需的代码行。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。**

## **我的锅**

```kt
import android.content.Intent
import android.os.Bundle
import android.text.TextUtils
import android.widget.Button
import android.widget.EditText
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import com.google.android.gms.tasks.OnFailureListener
import com.google.android.gms.tasks.OnSuccessListener
import com.google.android.gms.tasks.Task
import com.google.firebase.auth.AuthResult
import com.google.firebase.auth.FirebaseAuth
import com.google.firebase.auth.FirebaseUser
import com.google.firebase.auth.OAuthProvider
import com.google.firebase.auth.ktx.auth
import com.google.firebase.ktx.Firebase

class MainActivity : AppCompatActivity() {

    private lateinit var firebaseUser: FirebaseUser
    private lateinit var loginBtn: Button
    private lateinit var githubEdit: EditText

    // firebaseAuth variable to be initialized later
    private lateinit var auth: FirebaseAuth

    // an instance of an OAuthProvider using its
      // Builder with the provider ID github.com
    private var provider = OAuthProvider.newBuilder("github.com")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Initialize Firebase Auth
        auth = Firebase.auth

        loginBtn = findViewById(R.id.github_login_btn)
        githubEdit = findViewById(R.id.githubId)

        // Target specific email with login hint.
        provider.addCustomParameter("login", githubEdit.text.toString())

        // Request read access to a user's email addresses.
        // This must be preconfigured in the app's API permissions.
        val scopes: ArrayList<String?> = object : ArrayList<String?>() {
            init {
                add("user:email")
            }
        }
        provider.scopes = scopes

        // call signInWithGithubProvider() method
          // after clicking login Button
        loginBtn.setOnClickListener {
            if (TextUtils.isEmpty(githubEdit.text.toString())) {
                Toast.makeText(this, "Enter email associated to github", Toast.LENGTH_LONG).show()
            } else {
                signInWithGithubProvider()
            }
        }
    }

    // To check if there is a pending 
      // result, call pendingAuthResult
    private fun signInWithGithubProvider() {

        // There's something already here! Finish the sign-in for your user.
        val pendingResultTask: Task<AuthResult>? = auth.pendingAuthResult
        if (pendingResultTask != null) {
            pendingResultTask
                    .addOnSuccessListener {
                        // User is signed in.
                        Toast.makeText(this, "User exist", Toast.LENGTH_LONG).show()
                    }
                    .addOnFailureListener {
                        // Handle failure.
                        Toast.makeText(this, "Error1 : $it", Toast.LENGTH_LONG).show()
                    }
        } else {

            auth.startActivityForSignInWithProvider(this, provider.build())
                    .addOnSuccessListener(
                            OnSuccessListener<AuthResult?> {
                                // User is signed in.
                                // retrieve the current user
                                firebaseUser = auth.currentUser!!
                                val user: Map<String, Any> =
                                        // contains additional user information as 
                                          // a result of a successful sign-in
                                        it.additionalUserInfo!!.profile as Map<String, Any>  //
                                // navigate to HomePageActivity after successful login
                                val intent = Intent(this, HomePageActivity::class.java)
                                // send github user name from MainActivity to HomePageActivity
                                intent.putExtra("githubUserName", firebaseUser.displayName)
                                intent.putExtra("twitterHandle", user["twitter_username"].toString())
                                intent.putExtra("githubBio", user["bio"].toString())
                                intent.putExtra("linkedInLink", user["blog"].toString())
                                intent.putExtra("id", user["login"].toString())
                                intent.putExtra("follower", user["followers"].toString())
                                intent.putExtra("following", user["following"].toString())
                                intent.putExtra("publicRepos", user["public_repos"].toString())
                                intent.putExtra("location", user["location"].toString())
                                intent.putExtra("profilePic", user["avatar_url"].toString())
                                this.startActivity(intent)
                                Toast.makeText(this, "Login Successfully", Toast.LENGTH_LONG).show()

                            })
                    .addOnFailureListener(
                            OnFailureListener {
                                // Handle failure.
                                Toast.makeText(this, "Error2 : $it", Toast.LENGTH_LONG).show()
                            })
        }

    }
}
```

****第三步:创建一个新的空活动****

**参考本文[如何在安卓工作室](https://www.geeksforgeeks.org/how-to-create-constructor-getter-setter-methods-and-new-activity-in-android-studio-using-shortcuts/)新建活动，新建一个活动。将活动命名为**主页活动。**导航到**应用程序> res >布局> activity_home_page.xml** 并将下面的代码添加到该文件中。下面是 **activity_home_page.xml** 文件的代码。**

## **可扩展标记语言**

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HomePageActivity">

    <ImageView
        android:id="@+id/profilePic"
        android:layout_width="120dp"
        android:layout_height="100dp"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_marginEnd="10dp"
        android:contentDescription="profile image"
        android:scaleType="centerCrop"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:srcCompat="@tools:sample/avatars[3]" />

    <LinearLayout
        android:id="@+id/linearLayout2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="8dp"
        android:layout_marginTop="20dp"
        android:orientation="vertical"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/profilePic">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent">

            <TextView
                android:id="@+id/idHeader"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="GitHub Id:"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/githubId"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="github id"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
        </LinearLayout>

        <LinearLayout
            android:id="@+id/linearLayout"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent">

            <TextView
                android:id="@+id/headerId"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="User Name :"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/id"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="user name"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent">

            <TextView
                android:id="@+id/followerHeader"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="Follower:"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/follower"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="no. of follower"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent">

            <TextView
                android:id="@+id/followingHeader"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="Following:"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/following"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="no. of following"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent">

            <TextView
                android:id="@+id/repoHeader"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="Public Repos :"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/repos"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="no. of repos"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent">

            <TextView
                android:id="@+id/twitter"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="Twitter:"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/twitterUserName"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="twitter handle"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent">

            <TextView
                android:id="@+id/bioHeader"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="Bio:"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/bio"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="twitter handle"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:orientation="horizontal"
            android:weightSum="2"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent">

            <TextView
                android:id="@+id/linkedIn"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="0.5"
                android:text="LinkedIn:"
                android:textColor="#06590A"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />

            <TextView
                android:id="@+id/linkedInLink"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1.5"
                android:hint="linkedIn link"
                android:textAlignment="center"
                app:layout_constraintEnd_toEndOf="parent"
                app:layout_constraintStart_toStartOf="parent"
                app:layout_constraintTop_toTopOf="parent" />
        </LinearLayout>

    </LinearLayout>

    <Button
        android:id="@+id/logOut"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="20dp"
        android:gravity="center"
        android:text="Logout"
        android:textColor="#fff"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**转到**HomePageActivity . kt**文件，参考以下代码。下面是**HomePageActivity . kt**文件的代码。代码中添加了注释，以更详细地理解代码。**

## **我的锅**

```kt
package com.anju.kumari.usergithubauth

import android.content.Intent
import android.os.Bundle
import android.widget.Button
import android.widget.ImageView
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity
import com.bumptech.glide.Glide

class HomePageActivity : AppCompatActivity() {

    // declare variables to contain 
    // user's sent information
    // initialize them too
    private var userName = ""
    private var twitterHandle = " "
    private var bio = " "
    private var linkedIn = " "
    private var githubId = " "
    private var follower = " "
    private var following = " "
    private var repos = " "
    private var picUrl = " "

    private lateinit var githubUserName: TextView
    private lateinit var logoutBtn: Button
    private lateinit var handle: TextView
    private lateinit var githubBio: TextView
    private lateinit var linkedInLink: TextView
    private lateinit var userId: TextView
    private lateinit var totalFollower: TextView
    private lateinit var totalFollowing: TextView
    private lateinit var totalRepos: TextView
    private lateinit var userPic: ImageView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_home_page)

        githubUserName = findViewById(R.id.id)
        logoutBtn = findViewById(R.id.logOut)
        handle = findViewById(R.id.twitterUserName)
        githubBio = findViewById(R.id.bio)
        linkedInLink = findViewById(R.id.linkedInLink)
        userId = findViewById(R.id.githubId)
        totalFollower = findViewById(R.id.follower)
        totalFollowing = findViewById(R.id.following)
        totalRepos = findViewById(R.id.repos)
        userPic = findViewById(R.id.profilePic)

        // catching all data sent from MainActivity using Intent
        userName = intent.getStringExtra("githubUserName")!!
        twitterHandle = intent.getStringExtra("twitterHandle")!!
        bio = intent.getStringExtra("githubBio")!!
        linkedIn = intent.getStringExtra("linkedInLink")!!
        githubId = intent.getStringExtra("id")!!
        follower = intent.getStringExtra("follower")!!
        following = intent.getStringExtra("following")!!
        repos = intent.getStringExtra("publicRepos")!!
        picUrl = intent.getStringExtra("profilePic")!!

        // set all information to the widgets 
        // to display them on the screen
        githubUserName.text = userName
        handle.text = twitterHandle
        githubBio.text = bio
        linkedInLink.text = linkedIn
        userId.text = githubId
        totalFollower.text = follower
        totalFollowing.text = following
        totalRepos.text = repos

        // use glide to download the user's 
        // pic using url of the image
        Glide.with(this)
            .load(picUrl)
            .into(userPic)

        // logout button to signOut from the app
        logoutBtn.setOnClickListener {
            val intent = Intent(this, MainActivity::class.java)
            this.startActivity(intent)
        }
    }
}
```

****注意:**确保添加使用[滑动](https://guides.codepath.com/android/Displaying-Images-with-the-Glide-Library)加载用户图片的依赖。**

> **依赖项{**
> 
> **。。。**
> 
> **实现' com . github . bumptech . glide:glide:4 . 11 . 0 '**
> 
> **annotation processor ' com . github . bumptech . glide:编译器:4.11.0 '**
> 
> **。。。**
> 
> **}**

**这里是**输出。****

****输出:****

**<video class="wp-video-shortcode" id="video-630634-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210617131620/userupdate.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210617131620/userupdate.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210617131620/userupdate.mp4)</video>**

****github 上的源代码:**[**https://github . com/anju 1415/github-auth**](https://github.com/Anju1415/Github-Auth)**