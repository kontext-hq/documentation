# Android SDK Setup

!!! tip "Upgrade to 3.5.1+"
     A number the methods and classes below were recently added in our 3.5.1 SDK. Make sure you have updated to this version.

### Required For Setup

- [A Kontext Account](https://app.kontext.in/), if you do not already have one
- Your Kontext App ID & Secret provided by Kontext team
- [A Google/Firebase Server API Key](/android/firebase/key)
- A device or emulator that has Google Play services installed and updated on it
- Android Studio 2.3.3 or newer

### 1. Download the SDK

[Click Here to download the SDK](https://github.com/kontext-hq/documentation/blob/master/docs/sdk/kontextSDK.aar?raw=true)

### 2. Gradle Setup

**2.1** Place Kontext SDK in your app's *libs* folder.

**2.2** Add the following to your `dependencies` section.

- *build.gradle*

```

dependencies {
    implementation(name:'kontextSdk', ext:'aar')
    implementation 'com.google.android.gms:play-services-nearby:12.0.1'
    implementation 'com.android.installreferrer:installreferrer:1.0'
}
```

!!! warning "Play Services Version"

    In order to get access to all Kontext SDK features update all your app play services version to 12.0.1 or above.

**2.3** Add the following in your `android` > `defaultConfig` section.

- Update `PUT YOUR KONTEXT APP ID HERE` with your Kontext app id

- *build.gradle*

```
android {
   defaultConfig {
      manifestPlaceholders = [
          kontext_app_id: 'PUT YOUR KONTEXT APP ID HERE',
          // Project number pulled from dashboard, local value is ignored.
          kontext_google_project_number: 'REMOTE'
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

### Sync Gradle

Make sure to press "Sync Now" on the banner that pops up after saving!

### 3. Add Required Code

**3.1** Add the following to the `onCreate` method in your `Application` class.

- *Don't have an Application class? Follow our creation guide!*

```java
import com.kontext.Kontext;

public class YourAppClass extends Application {
   @Override
   public void onCreate() {
      super.onCreate();
     
      // Kontext Initialization
      Kontext.startInit(this)
        .inFocusDisplaying(Kontext.OSInFocusDisplayOption.Notification)
        .unsubscribeWhenNotificationsAreDisabled(true)
        .init();
   }
}
```



### 4. Create a custom default notification icon

**4.1** By default, notifications will be shown with a bell icon in the notification shade. 

!!! warning "Troubleshooting"

    If run into any issues please see our [Android troubleshooting guide](/android/troubleshoot), or our general Troubleshooting section.

### 5. Add Information to a User Profile

RECOMMENDED

A User Profile is automatically created in Kontext for each user launching your application.

Initially, the User Profile starts out as anonymous, which means the profile does not contain any identifiable information about the user. You can enrich the profile with pre-defined attributes from the Kontext data model, such as name and email. You can also add custom attributes that you define to extend the Kontext data model.

Sending user profile information to Kontext using our Android SDK requires two steps. First, you have to build a JSON Object with the profile properties. Second, you have to call the SDK's [sendUserAttributes](/android/reference#senduserattributes)) method and pass the object you created as a parameter.

```java
JSONObject userProfile = new JSONObject();
      try {
         userProfile.put("Name", "Jhon Doe");
         userProfile.put("Email", "jack@gmail.com");
         userProfile.put("Phone", "+14155551234");
         userProfile.put("Gender", "M");
         userProfile.put("Employed", "Y");
         userProfile.put("Education", "Graduate");
         userProfile.put("Married","Y");
         userProfile.put("Age", 50);
         userProfile.put("Tz", "Asia/Kolkata");
         Kontext.setUserAttributes(userProfile);
      } catch (JSONException e) {
         e.printStackTrace();
      }
```

### 6. Track Screen Activity

RECOMMENDED

Once you integrate the Kontext SDK, we automatically start tracking events, such as App Launch and Notification Viewed. Kontext SDK offers screen tracking API to track screen activity of a user.

To send screen activity to Kontext, you will have to call the [sendScreen](/android/reference#sendScreen) method with the name of the screen.

```java
Kontext.sendScreen("Screen Name");
```

### 7. Track Custom Events

RECOMMENDED

Once you integrate the Kontext SDK, we automatically start tracking events, such as App Launch and Notification Viewed. In addition, you can also track custom events.

To send screen activity to Kontext, you will have to call the [sendEvent](/android/reference#sendEvent) method with the name of the custom event you want to track.

```java
Kontext.sendEvent("Product Added", "Applie iPhone");
```



!!! success "You're Done!"

    Next up: Send your first push notification via the [Kontext Dashboard](https://app.kontext.in)
