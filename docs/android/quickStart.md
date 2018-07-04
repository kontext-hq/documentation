# Android SDK Setup

!!! info "Just starting with Android?"
    Check out our [Android SDK Setup](https://kontext.in) guide.

!!! tip "Upgrade to 3.5.1+"
     A number the methods and classes below were recently added in our 3.5.1 SDK. Make sure you have updated to this version.

### Required For Setup

- [A Kontext Account](https://kontext.in/), if you do not already have one
- Your Kontext App ID, available in [Keys & IDs](https://documentation.kontext.in/docs/accounts-and-keys#section-app-id)
- [A Google/Firebase Server API Key](https://documentation.kontext.in/docs/generate-a-google-server-api-key)
- A device or emulator that has Google Play services installed and updated on it
- Android Studio 2.3.3 or newer

### 1. Gradle Setup

**1.1** Open your `app/build.gradle` (Module: app) file, add the following to the very top.

- [build.gradle](https://documentation.kontext.in/docs/android-sdk-setup)

```
buildscript {
    repositories {
        maven { url 'https://plugins.gradle.org/m2/'}
    }
    dependencies {
        classpath 'gradle.plugin.com.kontext:kontext-gradle-plugin:[0.11.0, 0.99.99]'
    }
}
apply plugin: 'com.kontext.androidsdk.kontext-gradle-plugin'

repositories {
    maven { url 'https://maven.google.com' }
}
```

**1.2** Add the following to your `dependencies` section.

- [build.gradle](https://documentation.kontext.in/docs/android-sdk-setup)

```
dependencies {
    implementation 'com.kontext:Kontext:[3.9.1, 3.99.99]'
}
```

**1.3** Add the following in your `android` > `defaultConfig` section.

- Update `PUT YOUR KONTEXT APP ID HERE` with your Kontext app id

- [build.gradle](https://documentation.kontext.in/docs/android-sdk-setup)

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
### Sync Gradle

Make sure to press "Sync Now" on the banner that pops up after saving!



### 2. Add Required Code

**2.1** Add the following to the `onCreate` method in your `Application` class.

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



### 3. Create a custom default notification icon

**3.1** By default, notifications will be shown with a bell icon in the notification shade. Follow the [Customize Notification Icons](https://documentation.kontext.in/docs/customize-notification-icons) guide to create a your own small notification icon for your app.

### 4. Add Email

RECOMMENDED

Next, if you collect emails from users, you can set a user's email with the `setEmail` method. This enables [Kontext Email Messaging](https://documentation.kontext.in/docs/email-overview), which allows you to send emails in addition to push.

```java
Kontext.setEmail("example@domain.com");
```

If you have a backend server, we strongly recommend using [Identity Verification](https://documentation.kontext.in/docs/identity-verification) with your users. Your backend can generate an **email authentication token** and send it to your app or website. The following code also includes callbacks:

```java
String email = "example@domain.com";
String emailAuthHash = "..."; // Email auth hash generated from your server
Kontext.setEmail(email, emailAuthHash, new Kontext.EmailUpdateHandler() {
  @Override
  public void onSuccess() {
    // Email successfully synced with Kontext
  }

  @Override
  public void onFailure(Kontext.EmailUpdateError error) {
    // Error syncing email, check error.getType() and error.getMessage() for details
  }
});
```

Additional email methods are available in the [Android Native SDK](https://documentation.kontext.in/docs/android-native-sdk#section-email)

### You're Done!

Next up: [Send your first push notification](https://documentation.kontext.in/docs/testing-mobile-push-notifications) via the Kontext Dashboard

 