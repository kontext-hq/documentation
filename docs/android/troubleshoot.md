

# Troubleshooting Android

## Error:Execution failed for task ':app:processDebugGoogleServices'.

If you are receiving the following Android Studio error when building your project

```
Error:Execution failed for task ':app:processDebugGoogleServices'.
> Please fix the version conflict either by updating the version of the google-services plugin (information about the latest version is available at https://bintray.com/android/android-tools/com.google.gms.google-services/) or updating the version of com.google.android.gms to 9.0.0.
```

Remove the following line from your `.gradle` file.

```
apply plugin: 'com.google.gms.google-services'
```

## Error: Failed to resolve: com.android.support:customtabs:[26.0.0,26.2.0) OR com.android.support:support-v4:[26.0.0,26.2.0)

```
Failed to resolve: com.android.support:customtabs:[26.0.0,26.1.0)
Could not resolve all dependencies for configuration ':appName:'.
   > Could not find any version that matches com.android.support:customtabs:[26.0.0,26.2.0).
     Versions that do not match:
         26.0.0-alpha1
         25.3.1
         + 19 more
     Required by:
         project :appName > com.kontext:kontext:3.6.0
```

![Screenshot](/assets/images/trouble-1.png)

Please use one of the Options below to resolve the issue;

#### Option A

Add the new [Google Maven repo](https://developer.android.com/topic/libraries/support-library/setup.html) to your `build.gradle`

- *build.gradle*

```
repositories {
    maven { url 'https://maven.google.com' }
}
```

Also update `compileSdkVersion` to `26` in your `app/build.gradle`.

#### Option B

If you are not ready to update your project to the new support library yet and are still using `targetSdkVersion 25`or lower you can follow Option A or C in the section's instructions.

## Error: All gms/firesbase libraries must use the exact same version specification

```
All gms/firebase libraries must use the exact same version (mixing versions can lead to runtime crashes).
Found versions 11.0.4, 10.2.1.
Examples include com.google.android.gms:play-services-base:11.0.4 and com.google.android.gms:play-services-gcm:10.2.1.
```

![Screenshot](/assets/images/trouble-2.png)

Kontext automatically adds the following dependencies;

- `com.google.android.gms` - Version 11.2.+
- `com.android.support` - Version 26.1.+

To fix this issue, all dependencies must be matching versions.

Upgrade - Find all `com.google.android.gms` compile lines and update them to match.

- *build.gradle*

```
// Update 12.0.1+ so it is using the same gms version as Kontext
compile 'com.google.android.gms:play-services-maps:12.0.1'
```

## Error: java.lang.NoSuchMethodError: com.google.android.gms.common.internal.zzaa.zzb

If you see that some obfuscated Firebase or Google GMS methods are missing, it is most probably a dependency versioning conflict.

You can use the `gradle dependencies` and `gradle dependencyInsight` directives to troubleshoot which libraries are causing classes/methods to go missing. Refer to the official Gradle documentation for more information:

<https://docs.gradle.org/current/userguide/tutorial_gradle_command_line.html#sec:dependency_insight>

For example:

```shell
./gradlew app:dependencyInsight --configuration compile
```

 Error:Execution failed for task ':app:processDebugManifest'

```
Execution failed for task ':app:processDebugManifest'
Manifest merger failed with multiple errors, see logs 
```

![Screenshot](/assets/images/trouble-3.png)

## ERROR: AppId format is invalid

1. Make sure you have `kontext_app_id` in your `build.gradle` and your id is correct.

- *Gradle*

```
android {
   defaultConfig {
      manifestPlaceholders = [kontext_app_id: "PUT YOUR KONTEXT APP ID HERE",
                              // Project number pulled from dashboard, local value is ignored.
                              kontext_google_project_number: "REMOTE"]
    }
 }
```

1. Make sure you are not replacing the `<application>` tag in your `AndroidManifest.xml` with `tools:node="replace"`

```xml
<application
android:icon="@mipmap/ic_launcher"
tools:node="replace" <!-- Remove this line!!! -->
android:name=".ApplicationClass">
```

If you must replace some attributes please use `tools:replace` instead `tools:node`.
Example: `tools:replace="icon, label"`

## How to get a crash or error log from an Android device

### With Android Studio

**1.** Select `Android Monitor` from the bottom of the window.
------If you don't see this select it from `View` > `Tool Windows` > `Android Monitor`
**2.** Select your device from the drop down.
**3.** Ensure no filters are set and the type is set to Verbose.

![Screenshot](/assets/images/trouble-4.png)

**4.** Select all lines in the log by pressing Control + A and then copy them. **5.** Paste them into a `.txt` file and send this to support. Include steps to reproduce the problem as well.

### With the terminal / command line.

**1.** `adb logcat -b all -d -v threadtime > kontext_crash_logcat.txt`
**2.** Send the `kontext_crash_logcat.txt` to support. Include steps to reproduce the problem as well.

If you don't have `adb` in your path you will need to fully path to `adb` in the Android SDK. It is under `<android-sdk>\platform-tools\adb`.
If you don't have the Android SDK installed you can just download the [SDK Platform Tools](https://developer.android.com/studio/releases/platform-tools.html#download) which contains the `adb`executable.

## Android Studio - No resource found that matches the given name: attr 'android:keyboardNavigationCluster'

Make sure you have `compileSdkVersion` to `26` in your `app/build.gradle`. This is required when you update to 26 of the Android Support Library.

## Eclipse - ERROR - "conversion to dalvik format failed with error 1"

If you're getting a `conversion to dalvik format failed with error 1` error with `Dx bad class file magic (cafebabe) or version (0033.0000)` messages before this then you may have the wrong Java version set on your system. See the follow post to fix this as well as the other answers.
<http://stackoverflow.com/a/9041471/1244574>

!!! tip "Still facing issues? We'are happy to help"

    We answer most support queries in under 4 hours during the week, and under 24 hours on weekends. Simply email us at support@kontext.in
    	1. Version of our SDK
    	2. Device OS version
    	3. Android crash lock or stack trace of the app 		starting and the problem point
    	4. Any other libraries or plugins in your app
    	5. Details on reproducing your problem.
