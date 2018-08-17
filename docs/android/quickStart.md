# Android SDK Setup

!!! tip "Upgrade to 3.5.1+"
     A number the methods and classes below were recently added in our 3.5.1 SDK. Make sure you have updated to this version.

### Required For Setup

- [A Kontext Account](https://app.kontext.in/), if you do not already have one
- Your Kontext App ID, available in [Keys & IDs](/android/firebasekey)
- [A Google/Firebase Server API Key](/android/firebase/key)
- A device or emulator that has Google Play services installed and updated on it
- Android Studio 2.3.3 or newer

### 1. Download the SDK

[Click Here to download the SDK](https://gitlab.com/kontext/Kontext-Android-SDK/raw/master/KontextSDK-4.2.aar)

### 2. Gradle Setup

**2.1** Place Kontext SDK in your app's *libs* folder.

**2.2** Add the following to your `dependencies` section.

- *build.gradle*

```
dependencies {
    implementation(name:'kontextSdk', ext:'aar')
    
    // To access Nearby services
    implementation 'com.google.android.gms:play-services-nearby:12.0.1'
    
    // To attribute App install
    implementation 'com.android.installreferrer:installreferrer:1.0'
    
    // To access Location services
    implementation "com.google.android.gms:play-services-location:12.0.1"
}
```

!!! warning "Play Services Version"

```
In order to get access to all Kontext SDK features update all your app play services version to 12.0.1 or above.
```

**2.3** Add the following in your `android` > `defaultConfig` section.

- Update `PUT YOUR KONTEXT APP ID HERE` with your Kontext app id
- *build.gradle*

```
android {
   defaultConfig {
      manifestPlaceholders = [
          kontext_app_id: 'PUT YOUR KONTEXT APP ID HERE',
          kontext_app_secret: 'PUT YOUR KONTEXT SECRET ID HERE''
          kontext_google_project_number: 'PUT YOUR FIREBASE PROJECT NUMBER HERE'
      ]
    }
 }
```

**2.4** Add the following in your `App Manifest application` tag to enable Kontext In-App messaging.

```
<application>
	<activity
	android:name="com.kontext.InAppMessageActivity"
	android:configChanges="orientation|keyboardHidden"
	android:theme="@android:style/Theme.Translucent.NoTitleBar" />
</application>
       
```

**2.5** Add the following in your `App Manifest application` so that KontextSDK can access Internet.

```
<!-- Required to allow the app to send events and user profile information -->
<uses-permission android:name="android.permission.INTERNET"/>
<!-- Recommended so that Kontext knows when to attempt a network call -->
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
       
```

### Sync Gradle

Make sure to press "Sync Now" on the banner that pops up after saving!

### 3. Add Required Code

**3.1** Add the following to the `onCreate` method in your `Application` class.

*Option 1: If you don't have the application class*

Replace **android:name** in your mainfest with following:

```java
<application
        android:icon="@drawable/ic_launcher"
        android:theme="@style/AppTheme"
        android:label="Kontext Example"
        android:name="com.kontext.Application"
        tools:replace="android:label">
        <meta-data 
</application>
```



*Option 2: If you have an  Application class*

```java
import com.kontext.Kontext;

import com.kontext.ActivityLifecycleCallback;

public class YourAppClass extends Application {
   @Override
   public void onCreate() {
       
        // Kontext Initialization
       ActivityLifecycleCallback.register(this);
      super.onCreate();
   }
}
```

### 4. Create a custom default notification icon

**4.1** By default, notifications will be shown with a bell icon in the notification shade. 

!!! warning "Troubleshooting"

```
If run into any issues please see our [Android troubleshooting guide](/android/troubleshoot), or our general Troubleshooting section.
```

### 5. Add Information to a User Profile

RECOMMENDED

A User Profile is automatically created in Kontext for each user launching your application.

Initially, the User Profile starts out as anonymous, which means the profile does not contain any identifiable information about the user. You can enrich the profile with pre-defined attributes from the Kontext data model, such as name and email. You can also add custom attributes that you define to extend the Kontext data model.

Sending user profile information to Kontext using our Android SDK requires two steps. First, you have to build a JSON Object with the profile properties. Second, you have to call the SDK's [sendUserAttributes](/android/reference#senduserattributes)) method and pass the object you created as a parameter.

```java
HashMap<String, Object> profileUpdate = new HashMap<String, Object>();
      profileUpdate.put("Name", "John Dow");                  // String
      profileUpdate.put("Email", "john@gmail.com");               // Email address of the user
      profileUpdate.put("Phone", "+222333444");                 // Phone (with the country code)
      profileUpdate.put("Gender", "M");                           // Can be either M or F
      profileUpdate.put("Employed", "Y");                         // Can be either Y or N
      profileUpdate.put("Education", "Graduate");                 // Can be either Graduate, College or School
      profileUpdate.put("Married", "Y");                          // Can be either Y or N
      profileUpdate.put("DOB", new Date());                       // Date of Birth. Set the Date object to the appropriate value first
      profileUpdate.put("Age", 28);                               // Not required if DOB is set
      profileUpdate.put("Tz", "Asia/Kolkata");                    
      profileUpdate.put("Photo", "www.foobar.com/image.jpeg");    // URL to the Image

      Kontext.setUserProfile(profileUpdate);
```

### 6. Track Screen Activity

RECOMMENDED

Once you integrate the Kontext SDK, we automatically start tracking events, such as App Launch and Notification Viewed. Kontext SDK offers screen tracking API to track screen activity of a user.

To send screen activity to Kontext, you will have to call the [sendScreen](/android/reference#sendScreen) method with the name of the screen.

```java
Kontext.sendScreen("Screen Name");	// String
```

### 7. Track Custom Events

RECOMMENDED

Once you integrate the Kontext SDK, we automatically start tracking events, such as App Launch and Notification Viewed. In addition, you can also track custom events.

To send screen activity to Kontext, you will have to call the [sendEvent](/android/reference#sendEvent) method with the name of the custom event you want to track.

```java
JSONObject payload = new JSONObject();
      payload.put("Product Added", "Applie iPhone");
      Kontext.sendEvent("Product", payload);
```



!!! success "You're Done!"

    Next up: Send your first push notification via the [Kontext Dashboard](https://app.kontext.in)
