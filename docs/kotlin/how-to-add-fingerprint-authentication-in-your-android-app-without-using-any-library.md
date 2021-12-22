# 如何在不使用任何库的情况下，在你的安卓 App 中添加指纹认证？

> 原文:[https://www . geesforgeks . org/如何在不使用任何库的情况下在您的安卓应用中添加指纹认证/](https://www.geeksforgeeks.org/how-to-add-fingerprint-authentication-in-your-android-app-without-using-any-library/)

**生物指纹认证**是保护应用敏感信息或优质内容的一种方法。如今，所有支付应用程序都在其应用程序中使用这一功能。它非常容易实现。下面给出了一个示例视频，以了解我们将在本文中做什么。请注意，我们将使用 **Java** 和 **Kotlin** 语言来实现这个项目

<video class="wp-video-shortcode" id="video-559116-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210214133207/biometric_auth_fingerprint_gfg_android.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210214133207/biometric_auth_fingerprint_gfg_android.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210214133207/biometric_auth_fingerprint_gfg_android.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意，选择**柯特林/Java** 作为编程语言

**步骤 2:在清单中添加生物识别许可**

转到 **AndroidMenifest.xml** 文件，并在那里添加以下权限。

**步骤 3:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。它只有一个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)，点击它将创建指纹扫描仪对话框。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/start_authentication"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Authenticate"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**步骤 4:使用主活动文件**

转到**主活动**文件，参考以下代码。以下是**主活动**文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.app.KeyguardManager
import android.content.Context
import android.content.DialogInterface
import android.content.pm.PackageManager
import android.hardware.biometrics.BiometricPrompt
import android.os.Build
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.CancellationSignal
import android.widget.Button
import android.widget.Toast
import androidx.annotation.RequiresApi
import androidx.core.app.ActivityCompat

class MainActivity : AppCompatActivity() {

    // create a CancellationSignal variable and assign a value null to it
    private var cancellationSignal: CancellationSignal? = null

    // create an authenticationCallback
    private val authenticationCallback: BiometricPrompt.AuthenticationCallback
        get() = @RequiresApi(Build.VERSION_CODES.P)
            object : BiometricPrompt.AuthenticationCallback() {
                // here we need to implement two methods
                // onAuthenticationError and onAuthenticationSucceeded
                // If the fingerprint is not recognized by the app it will call
                // onAuthenticationError and show a toast
                override fun onAuthenticationError(errorCode: Int, errString: CharSequence?) {
                    super.onAuthenticationError(errorCode, errString)
                    notifyUser("Authentication Error : $errString")
                }

                // If the fingerprint is recognized by the app then it will call
                // onAuthenticationSucceeded and show a toast that Authentication has Succeed
                // Here you can also start a new activity after that
                override fun onAuthenticationSucceeded(result: BiometricPrompt.AuthenticationResult?) {
                    super.onAuthenticationSucceeded(result)
                    notifyUser("Authentication Succeeded")

                    // or start a new Activity

                }
            }

    @RequiresApi(Build.VERSION_CODES.P)
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        checkBiometricSupport()
        // create a biometric dialog on Click of button
        findViewById<Button>(R.id.start_authentication).setOnClickListener {
            // This creates a dialog of biometric auth and
            // it requires title , subtitle ,
            // and description
            // In our case there is a cancel button by
            // clicking it, it will cancel the process of
            // fingerprint authentication
            val biometricPrompt = BiometricPrompt.Builder(this)
                    .setTitle("Title of Prompt")
                    .setSubtitle("Subtitle")
                    .setDescription("Uses FP")
                    .setNegativeButton("Cancel", this.mainExecutor, DialogInterface.OnClickListener { dialog, which ->
                        notifyUser("Authentication Cancelled")
                    }).build()

            // start the authenticationCallback in mainExecutor
            biometricPrompt.authenticate(getCancellationSignal(), mainExecutor, authenticationCallback)
        }
    }

    // it will be called when authentication is cancelled by the user
    private fun getCancellationSignal(): CancellationSignal {
        cancellationSignal = CancellationSignal()
        cancellationSignal?.setOnCancelListener {
            notifyUser("Authentication was Cancelled by the user")
        }
        return cancellationSignal as CancellationSignal
    }

    // it checks whether the app the app has fingerprint permission
    @RequiresApi(Build.VERSION_CODES.M)
    private fun checkBiometricSupport(): Boolean {
        val keyguardManager = getSystemService(Context.KEYGUARD_SERVICE) as KeyguardManager
        if (!keyguardManager.isDeviceSecure) {
            notifyUser("Fingerprint authentication has not been enabled in settings")
            return false
        }
        if (ActivityCompat.checkSelfPermission(this, android.Manifest.permission.USE_BIOMETRIC) != PackageManager.PERMISSION_GRANTED) {
            notifyUser("Fingerprint Authentication Permission is not enabled")
            return false
        }
        return if (packageManager.hasSystemFeature(PackageManager.FEATURE_FINGERPRINT)) {
            true
        } else true
    }

    // this is a toast method which is responsible for showing toast
    // it takes a string as parameter
    private fun notifyUser(message: String) {
        Toast.makeText(this, message, Toast.LENGTH_SHORT).show()
    }
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```
import android.app.KeyguardManager;
import android.content.Context;
import android.content.DialogInterface;
import android.content.pm.PackageManager;
import android.hardware.biometrics.BiometricPrompt;
import android.os.Build;
import android.os.Bundle;
import android.os.CancellationSignal;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;
import androidx.annotation.Nullable;
import androidx.annotation.RequiresApi;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;

public class MainActivity extends AppCompatActivity {

    // create a CancellationSignal
      // variable and assign a
    // value null to it
    private CancellationSignal cancellationSignal = null;

    // create an authenticationCallback
    private BiometricPrompt.AuthenticationCallback authenticationCallback;

    @RequiresApi(api = Build.VERSION_CODES.P)
    @Override
    protected void
    onCreate(@Nullable Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        authenticationCallback = new BiometricPrompt.AuthenticationCallback() {
                  // here we need to implement two methods
                  // onAuthenticationError and
                  // onAuthenticationSucceeded If the
                  // fingerprint is not recognized by the
                  // app it will call onAuthenticationError
                  // and show a toast
                  @Override
                  public void onAuthenticationError(
                      int errorCode, CharSequence errString)
                  {
                      super.onAuthenticationError(errorCode, errString);
                      notifyUser("Authentication Error : " + errString);
                  }
                  // If the fingerprint is recognized by the
                  // app then it will call
                  // onAuthenticationSucceeded and show a
                  // toast that Authentication has Succeed
                  // Here you can also start a new activity
                  // after that
                  @Override
                  public void onAuthenticationSucceeded(BiometricPrompt.AuthenticationResult result)
                  {
                      super.onAuthenticationSucceeded(result);
                      notifyUser("Authentication Succeeded");
                      // or start a new Activity
                  }
              };

        checkBiometricSupport();
        // create a biometric dialog on Click of button
        (Button) findViewById(R.id.start_authentication).setOnClickListener(new View.OnClickListener() {
                @RequiresApi(api = Build.VERSION_CODES.P)
                @Override
                public void onClick(View view)
                {
                    // This creates a dialog of biometric
                    // auth and it requires title , subtitle
                    // , and description In our case there
                    // is a cancel button by clicking it, it
                    // will cancel the process of
                    // fingerprint authentication
                    BiometricPrompt biometricPrompt = new BiometricPrompt
                              .Builder(getApplicationContext())
                              .setTitle("Title of Prompt")
                              .setSubtitle("Subtitle")
                              .setDescription("Uses FP")
                              .setNegativeButton("Cancel", getMainExecutor(), new DialogInterface.OnClickListener() {
                                          @Override
                                          public void
                                          onClick(DialogInterface dialogInterface, int i)
                                          {
                                              notifyUser("Authentication Cancelled");
                                          }
                                      }).build();

                    // start the authenticationCallback in
                    // mainExecutor
                    biometricPrompt.authenticate(
                        getCancellationSignal(),
                        getMainExecutor(),
                        authenticationCallback);
                }
            });
    }

    // it will be called when
      // authentication is cancelled by
    // the user
    private CancellationSignal getCancellationSignal()
    {
        cancellationSignal = new CancellationSignal();
        cancellationSignal.setOnCancelListener(
            new CancellationSignal.OnCancelListener() {
                @Override public void onCancel()
                {
                    notifyUser("Authentication was Cancelled by the user");
                }
            });
        return cancellationSignal;
    }

    // it checks whether the
      // app the app has fingerprint
    // permission
    @RequiresApi(Build.VERSION_CODES.M)
    private Boolean checkBiometricSupport()
    {
        KeyguardManager keyguardManager = (KeyguardManager)getSystemService(Context.KEYGUARD_SERVICE);
        if (!keyguardManager.isDeviceSecure()) {
            notifyUser("Fingerprint authentication has not been enabled in settings");
            return false;
        }
        if (ActivityCompat.checkSelfPermission(this, android.Manifest.permission.USE_BIOMETRIC)!= PackageManager.PERMISSION_GRANTED) {
            notifyUser("Fingerprint Authentication Permission is not enabled");
            return false;
        }
        if (getPackageManager().hasSystemFeature(PackageManager.FEATURE_FINGERPRINT)) {
            return true;
        }
        else
            return true;
    }

    // this is a toast method which is responsible for
    // showing toast it takes a string as parameter
    private void notifyUser(String message)
    {
        Toast.makeText(this, message, Toast.LENGTH_SHORT).show();
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-559116-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210214133207/biometric_auth_fingerprint_gfg_android.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210214133207/biometric_auth_fingerprint_gfg_android.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210214133207/biometric_auth_fingerprint_gfg_android.mp4)</video>

**GitHub 回购** [**这里**](https://github.com/introidx/Finger-print-Authentication.git) **。**