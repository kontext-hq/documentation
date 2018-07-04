Android Native SDK

Kontext ANDROID Native API Reference

!!! info "Just starting with Android?"
    Check out our [Android SDK Setup](https://kontext.in) guide.

!!! tip "Upgrade to 3.5.1+"
     A number the methods and classes below were recently added in our 3.5.1 SDK. Make sure you have updated to this version.



| Calls                                                        | Type              | Description                                                  |
| ------------------------------------------------------------ | ----------------- | ------------------------------------------------------------ |
| Initialization                                               |                   |                                                              |
| [init](https://documentation.kontext.in/docs#section--init-) | Builder Method    | Initialize Kontext                                           |
| [startInit](https://documentation.kontext.in/docs#section--startinit-) | Builder Method    |                                                              |
| [setNotificationReceivedHandler](https://documentation.kontext.in/docs#section--setnotificationreceivedhandler-) | Builder Method    |                                                              |
| [setNotificationOpenedHandler](https://documentation.kontext.in/docs#section--setnotificationopenedhandler-) | Builder Method    |                                                              |
| [autoPromptLocation](https://documentation.kontext.in/docs#section--autopromptlocation-) | Builder Method    | Automatically Prompt Users for Location                      |
| [disableGmsMissingPrompt](https://documentation.kontext.in/docs#section--disablegmsmissingprompt-) | Builder Method    | Automatically Prompt User to update Google Play if out of date |
| [unsubscribeWhenNotificationsAreDisabled](https://documentation.kontext.in/docs#section--unsubscribewhennotificationsaredisabled-) | Builder Method    | If notifications are disabled for your app unsubscribe them from Kontext. |
| [filterOtherGCMReceivers](https://documentation.kontext.in/docs#section--filterothergcmreceivers-) | Builder Method    | Enable to prevent other broadcast receivers from receiving Kontext FCM / GCM payloads. |
| [setInFocusDisplaying](https://documentation.kontext.in/docs#section--setinfocusdisplaying-) | Method            | Change how the notification is displayed when your app is actively being used. |
|                                                              |                   |                                                              |
| Privacy                                                      |                   |                                                              |
| [setRequiresUserPrivacyConsent](https://documentation.kontext.in/docs#section--setrequiresuserprivacyconsent-) | Method            | Delays initialization of the SDK until the user provides privacy consent |
| [provideUserConsent](https://documentation.kontext.in/docs#section--provideuserconsent-) | Method            | Tells the SDK that the user has provided privacy consent (if required) |
| [userProvidedPrivacyConsent](https://documentation.kontext.in/docs#section--userprovidedprivacyconsent-) | Method            | Returns a boolean indicating if the SDK is waiting for user privacy consent |
|                                                              |                   |                                                              |
| Events                                                       |                   |                                                              |
| [sendEvent](https://documentation.kontext.in/docs#section--sendtag-) | Method            | Send a single user event to Kontext                          |
| [sendEvents](https://documentation.kontext.in/docs#section--sendtags-) | Method            | Batch and send multiple events to Kontext                    |
| [sendScreen](https://documentation.kontext.in/docs#section--sendtags-) | Method            | Send screen view activity to Kontext                         |
| [sendUserAttributes](https://documentation.kontext.in/docs#section--sendtags-) | Method            | Send user properties to Kontext                              |
|                                                              |                   |                                                              |
| Data                                                         |                   |                                                              |
| [promptLocation](https://documentation.kontext.in/docs#section--promptlocation-) | Method            | Prompt Users for Location                                    |
| [setLocationShared](https://documentation.kontext.in/docs#section--setlocationshared-) | Method            | Disable or enable location collection (Defaults to enabled) if your app has location permission |
|                                                              |                   |                                                              |
| Receiving Notifications                                      |                   |                                                              |
| [postNotification](https://documentation.kontext.in/docs#section--postnotification-) | Method            | Send or schedule a notification to a user                    |
| [cancelNotification](https://documentation.kontext.in/docs#section--cancelnotification-) | Method            | Delete a single app notification                             |
| [clearKontextNotifications](https://documentation.kontext.in/docs#section--clearkontextnotifications-) | Method            | Delete all app notifications                                 |
| [setSubscription](https://documentation.kontext.in/docs#section--setsubscription-) | Method            | Opt users in or out of receiving notifications               |
| [NotificationExtenderService](https://documentation.kontext.in/docs#section--notificationextenderservice-) | Method + Manifest | Add custom data to a notification, or override notification options |
|                                                              |                   |                                                              |
| Email                                                        |                   |                                                              |
| [setEmail](https://documentation.kontext.in/docs#section--setemail-) | Method            | Set user's email                                             |
| [logoutEmail](https://documentation.kontext.in/docs#section--logoutemail-) | Method            | Log user out to dissociate email from device                 |
| [addEmailSubscriptionObserver](https://documentation.kontext.in/docs#section--addemailsubscriptionobserver-) | Method            | Observer for subscription changes to email                   |
|                                                              |                   |                                                              |
| Notification Events                                          |                   |                                                              |
| [NotificationReceivedHandler](https://documentation.kontext.in/docs#section--notificationreceivedhandler-) | Handler           | When a notification is received by a device                  |
| [NotificationOpenedHandler](https://documentation.kontext.in/docs#section--notificationopenedhandler-) | Handler           | When a user takes an action on a notification                |
| [Opened Action](https://documentation.kontext.in/docs#section-opened-action) | Android Manifes   | Disable resuming launcher activity when notification is opened |
|                                                              |                   |                                                              |
| Objects                                                      |                   |                                                              |
| [OSNotificationOpenResult](https://documentation.kontext.in/docs#section--osnotificationopenresult-) | Object            | Information returned from a notification the user received   |
| [OSNotification](https://documentation.kontext.in/docs#section--osnotification-) | Object            | Notification the user received                               |
| [OSNotificationAction](https://documentation.kontext.in/docs#section--osnotificationaction-) |                   | Action the user took on the notification                     |
| [OSNotificationPayload](https://documentation.kontext.in/docs#section--osnotificationpayload-) |                   | Contents and settings of the notification the user received  |
|                                                              |                   |                                                              |
| Appearance                                                   |                   |                                                              |
| [setInFocusDisplaying](https://documentation.kontext.in/docs#section--setinfocusdisplaying-) | Method            | Change how the notification is displayed when your app is actively being used. |
| [enableVibrate](https://documentation.kontext.in/docs#section--enablevibrate-) | Method            | When user receives notification, vibrate device less         |
| [enableSound](https://documentation.kontext.in/docs#section--enablesound-) | Method            | When user receives notification, do not play a sound         |
| [Disable Badges](https://documentation.kontext.in/docs#section-disable-badges) | Android Manifest  | Disable badge counts in your app                             |
|                                                              |                   |                                                              |
| Debug                                                        |                   |                                                              |
| [setLogLevel](https://documentation.kontext.in/docs#section--setloglevel-) | Method            | Enable logging to help debug Kontext implementation          |



## Initialization

### `init`

BUILDER METHOD

Initializes Kontext to register the device for push notifications. Should be called in the `onCreate` method of your Application class.

```Java
Kontext.startInit(this).init();
```



### `startInit`

METHOD

Initializes Kontext to register the device for push notifications. Should be call in the `onCreate` of your Application class.

| Parameter | Type    | Description               |
| --------- | ------- | ------------------------- |
| `context` | Context | Your Application Kontext. |

#### Returns

`Kontext.Builder` - See below for a list of methods available.

```Java
public class YourAppClass extends Application {
   @Override
   public void onCreate() {
      super.onCreate();
      Kontext.startInit(this).init();
   }
}
```



### `autoPromptLocation`

BUILDER METHOD

Prompts the user for location permissions. This allows for geotagging so you can send notifications to users based on location. See [promptLocation](https://documentation.kontext.in/docs#section--promptlocation-) for more details.

| Parameter | Type    | Description                                                  |
| --------- | ------- | ------------------------------------------------------------ |
| `prompt`  | boolean | `false`  (DEFAULT) - do not prompt<br />`true`  -  prompt users for location permissions when your app starts. |

```Java
Kontext.startInit(this)
  .autoPromptLocation(true)
  .init();
```



### `setNotificationReceivedHandler`

BUILDER METHOD

Sets a notification received handler that will fire when a notification is received. It will be fired when your app is in focus or in the background.

| Parameter | Type                                                         | Description                                         |
| --------- | ------------------------------------------------------------ | --------------------------------------------------- |
| `handler` | [NotificationReceivedHandler](https://documentation.kontext.in/docs#section--notificationreceivedhandler-) | Instance to a class implementing this interference. |

```Java
Kontext.startInit(this)   
   .setNotificationReceivedHandler(new ExampleNotificationReceivedHandler())
   .init();
```



### `setNotificationOpenedHandler`

BUILDER METHOD

Sets a notification opened handler. The instance will be called when a notification is tapped on from the notification shade or when closing an Alert notification shown in the app.

| Parameter | Type                                                         | Description                                         |
| --------- | ------------------------------------------------------------ | --------------------------------------------------- |
| `hndler`  | [NotificationOpenedHandler](https://documentation.kontext.in/docs#section--notificationopenedhandler-) | Instance to a class implementing this interference. |

```Java
Kontext.startInit(this)   
   .setNotificationOpenedHandler(new ExampleNotificationOpenedHandler())
   .init();
```



### `setInFocusDisplaying`

METHOD

Setting to control how Kontext notifications will be shown when one is received while your app is in focus.

`Notification` - native notification display while user has app in focus (can be distracting).
`InAppAlert` (DEFAULT) - native alert dialog display, which can be helpful during development.
`None` - notification is silent.

```Java
Kontext.setInFocusDisplaying(Kontext.OSInFocusDisplayOption.Notification);
```



### `setRequiresUserPrivacyConsent`

METHOD

Lets your app require the user's privacy consent before it will initialize. If you call this method and pass in `true`, the SDK will delay initialization until your application calls `provideUserConsent(true).

If the SDK is waiting for the user's consent, calling any Kontext SDK methods will do nothing but print a warning. The user will not be registered for push notifications until this happens.

```Java
// the SDK will delay initialization and won't collect data.
Kontext.setRequiresUserPrivacyConsent(true);
```



### `provideUserConsent`

If your application is set to require the user's privacy consent, you can provide this consent using this method. Until you call `provideUserConsent(true)`, the SDK will not fully initialize and will not send any data to Kontext.

```Java
public void onUserTappedProvidePrivacyConsent(View v) {
  //will initialize the Kontext SDK and enable push notifications
  Kontext.provideUserConsent(true);
}
```



### `userProvidedPrivacyConsent`

METHOD

Returns a boolean indicating if the user has provided privacy consent. 



### `disableGmsMissingPrompt`

BUILDER METHOD

Prompts the user to update/enable Google Play services if it's disabled on the device.

| Parameter | Type    | Description                                                  |
| --------- | ------- | ------------------------------------------------------------ |
| `prompt`  | boolean | `false` (DEFAULT) - prompt users<br /> `true` to never show the out of date prompt. |

```Java
Kontext.startInit(this)
  .disableGmsMissingPrompt(true)
  .init();
```



### `unsubscribeWhenNotificationsAreDisabled`

BUILDER METHOD

If notifications are disabled for your app, unsubscribe the user from Kontext. This will happen when your users go to Settings > Apps and turn off notifications, or if they long press one of your notifications and select "block notifications".
This is `false` by default.

| Parameter | Type    | Description                                                  |
| --------- | ------- | ------------------------------------------------------------ |
| `prompt`  | boolean | `false` (DEFAULT) - prompt users<br /> `true` to never show the out of date prompt. |

```Java
Kontext.startInit(this)
  .disableGmsMissingPrompt(true)
  .init();
```



### `unsubscribeWhenNotificationsAreDisabled`

BUILDER METHOD

If notifications are disabled for your app, unsubscribe the user from Kontext. This will happen when your users go to Settings > Apps and turn off notifications, or if they long press one of your notifications and select "block notifications".
This is `false` by default.

| Parameter | Type    | Description                                                  |
| --------- | ------- | ------------------------------------------------------------ |
| `prompt`  | boolean | `false` (DEFAULT) - don't unsubscribe users<br /> `true` - unsubscribe users when notifications are disabled |

```Java
Kontext.startInit(this)
  .unsubscribeWhenNotificationsAreDisabled(true)
  .init();
```



## Status methods

The following methods provide details on the permission and subscribed state of the device. Use `getPermissionSubscriptionState` to get the current immediate state and use `addPermissionObserver` and / or `addSubscriptionObserver` to react to changes.



### Status Recommendations

[getPermissionSubscriptionState](https://documentation.kontext.in/docs#section--getpermissionsubscriptionstate-) - Use to load your UI to the correct state. Such as showing a toggle button to enable notifications.

[addSubscriptionObserver](https://documentation.kontext.in/docs#section--addsubscriptionobserver-) - Use to update your server when the user becomes subscribed or unsubscribed and to get the Kontext player / user id.
Example if you need to store the Kontext player / user id on your backend you can make a REST API call directly from the observer's callback. The Kontext observer ONLY fires when there is a change, including NOT firing even if the app has been restarted. This helps ensure your not making unnecessary network calls to your backend on each app restart if nothing changed.



### `getPermissionSubscriptionState`

METHOD

Get the current notification and permission state. Returns a `OSPermissionSubscriptionState` type described below.

| Parameter                  | Type                                                         | Description                            |
| -------------------------- | ------------------------------------------------------------ | -------------------------------------- |
| ` getPermissionStatus()`   | [OSPermissionState](https://documentation.kontext.in/docs#section--ospermissionstate-) | Android Notification Permissions state |
| ` getSubscriptionStatus()` | [OSSubscriptionState](https://documentation.kontext.in/docs#section--ossubscriptionstate-) | Google and  Kontext subscription state |

```Java
OSPermissionSubscriptionState status = Kontext.getPermissionSubscriptionState();
status.getPermissionStatus().getEnabled();
    
status.getSubscriptionStatus().getSubscribed();
status.getSubscriptionStatus().getUserSubscriptionSetting();
status.getSubscriptionStatus().getUserId();
status.getSubscriptionStatus().getPushToken();
```



### `OSPermissionState`

CLASS

The Notification permission status of your app. Contains enabled value to know if the user has turned off notifications for your app.

| Parameter       | Type    | Description                                                  |
| --------------- | ------- | ------------------------------------------------------------ |
| ` getEnabled()` | boolean | `true` if notifications are enabled.<br /> Will only be `false` if the user disables notifications for your app from the system settings |



### `OSSubscriptionState`

CLASS

Provides subscription state details of subscribed to push as well as the Kontext player / user id and the devices push token.

| Parameter         | Type    | Description                                                  |
| ----------------- | ------- | ------------------------------------------------------------ |
| `getSubscribed()` | boolean | `true` if the device can receive push notifications from  Kontext.<br /> `false` if the device has disabled push notifications or not successfully registered yet with either  Kontext or FCM with a valid push token. |
| `getUserId()`     | String  | The  Kontext player / user id for the device. `null` if the device hasn't registered with  Kontext's server yet. |
| `getPushToken()`  | String  | The GCM / FCM push token for the device. `null` if the device hasn't registered with Google's server yet. |



### `addPermissionObserver`

HANDLER

The `onOSPermissionChanged` method will be fired on the passed-in object when a notification permission setting changes. This happens when the user enables or disables notifications for your app from the system settings outside of your app. Disable detection is supported on Android 4.4+.

```Java
public class MainActivity extends Activity implements OSPermissionObserver {
  protected void onCreate(Bundle savedInstanceState) {
    Kontext.addPermissionObserver(this);
  }
  
  public void onOSPermissionChanged(OSPermissionStateChanges stateChanges) {
    if (stateChanges.getFrom().getEnabled() &&
        !stateChanges.getTo().getEnabled()) {
         new AlertDialog.Builder(this)
             .setMessage("Notifications Disabled!")
             .show();
      }
   
      Log.i("Debug", "onOSPermissionChanged: " + stateChanges);
  }
}

// Example Logcat entry - User disabling notifications then returning to your app.
// onOSPermissionChanged{"from":{"enabled":true},"to":{"enabled":false}}
```

!!! warning "Keep a Reference"
    Make sure to hold a reference to your observable at the class level, otherwise it my not fire.

!!! success "Leak Safe"
    Kontext holds a weak reference to your observer so it's guaranteed not to leak your `Activity`.



### `OSPermissionStateChanges`

CLASS

Instance is given to your `onOSPermissionChanged` method which provides what the value was (**"from"**) and what the value is now (**"to"**).

| Parameter   | Type                                                         | Description           |
| ----------- | ------------------------------------------------------------ | --------------------- |
| `getFrom()` | [OSSubscriptionState](https://documentation.kontext.in/docs#section--ossubscriptionstate-) | What the state was    |
| `getTo()`   | [OSSubscriptionState](https://documentation.kontext.in/docs#section--ossubscriptionstate-) | What the state is now |



### `addSubscriptionObserver`

METHOD

The `onOSSubscriptionChanged` method will be fired on the passed-in object when a notification subscription property changes.

This includes the following events:

- Getting a Registration Id (push token) from Google
- Getting a player / user id from Kontext
- `Kontext.setSubscription` is called
- User disables or enables notifications

```Java
public class MainActivity extends Activity implements OSSubscriptionObserver {
  protected void onCreate(Bundle savedInstanceState) {
    Kontext.addSubscriptionObserver(this);
  }
  
  public void onOSSubscriptionChanged(OSSubscriptionStateChanges stateChanges) {
    if (!stateChanges.getFrom().getSubscribed() &&
        stateChanges.getTo().getSubscribed()) {
         new AlertDialog.Builder(this)
             .setMessage("You've successfully subscribed to push notifications!")
             .show();
        // get player ID
        stateChanges.getTo().getUserId();
      }
   
      Log.i("Debug", "onOSPermissionChanged: " + stateChanges);
  }
}

/*
Example Logcat entry - User disabling notifications then returning to your app.
onOSSubscriptionChanged:
{"from":{"pushToken":"APA91bG9cmZ262s5gJhr8jvbg1q7aiviEC6lcOCgAQliEzHKO3eOdX5cm7IQqMSWfy8Od7Ol3jSjFfvCfeO2UYUpanJCURJ8RdhgEuV8grYxOCwPNJr5GoqcWTQOaL9u-qE2PQcFlv4K","userSubscriptionSetting":true,"subscribed":false},
 "to":  {"userId":"22712a53-9b5c-4eab-a828-f18f81167fef","pushToken":"APA91bG9cmZ262s5gJhr8jvbg1q7aiviEC6lcOCgAQliEzHKO3eOdX5cm7IQqMSWfy8Od7Ol3jSjFfvCfeO2UYUpanJCURJ8RdhgEuV8grYxOCwPNJr5GoqcWTQOaL9u-qE2PQcFlv4K","userSubscriptionSetting":true,"subscribed":true}}
```

!!! warning "Keep a Reference"
    Make sure to hold a reference to your observable at the class level, otherwise it my not fire.

!!! success "Leak Safe"
    Kontext holds a weak reference to your observer so it's guaranteed not to leak your `Activity`.



### `OSSubscriptionStateChanges`

CLASS

Instance is given to your `onOSSubscriptionChanged` method which provides what the value was (**"from"**) and what the value is now (**"to"**).

| Parameter | Type                                                         | Description               |
| --------- | ------------------------------------------------------------ | ------------------------- |
| getFrom() | [OSPermissionState](https://documentation.kontext.in/docs#section--ospermissionstate-) | What the state was (past) |
| getTo()   | [OSPermissionState](https://documentation.kontext.in/docs#section--ospermissionstate-) | What the state is now     |



## Events

### `sendEvent`

METHOD

Tag a user based on an app event of your choosing so later you can create segments in [Segments](https://documentation.kontext.in/segmentation) to target these users. Use `sendTags` if you need to set more than one tag on a user at a time.

| Parameter | Type   | Description                               |
| --------- | ------ | ----------------------------------------- |
| `key`     | String | Key of your choosing to create or update. |
| `value`   | String | Value to set on the key.                  |

```java
Kontext.sendEvents("key", "value");
```



### `sendEvents`

METHOD

Tag a user based on an app event of your choosing so later you can create segments in [Segments](https://documentation.kontext.in/segmentation) to target these users.

| Parameter   | Type       | Description                                           |
| ----------- | ---------- | ----------------------------------------------------- |
| `keyValues` | JSONObject | Key value pairs of your choosing to create or update. |

```Java
JSONObject events = new JSONObject();
	events.put("key1", "value1");
	eventss.put("key2", "value2");
	Kontext.sendEvents(events);
```



### `sendScreen`

METHOD

Tag a user based on an screen view event of your choosing so later you can create segments in [Segments](https://documentation.kontext.in/segmentation) to target these users.

| Parameter   | Type       | Description                                           |
| ----------- | ---------- | ----------------------------------------------------- |
| `keyValues` | JSONObject | Key value pairs of your choosing to create or update. |

```Java
Kontext.sendEvents("screen Name");
```



### `sendUserAttribute`

METHOD

Tag a user based on their properties like name, age, gender, location, etc.

| Parameter   | Type       | Description                                           |
| ----------- | ---------- | ----------------------------------------------------- |
| `keyValues` | JSONObject | Key value pairs of your choosing to create or update. |

```Java
JSONObject events = new JSONObject();
	events.put("name", "Jhon Doe");
	eventss.put("age", 24);
	eventss.put("gender", "M");
	eventss.put("city", "Pune");
	Kontext.sendUserAttributes(events);
```



## Data

### `promptLocation`

METHOD

Prompts the user for location permissions. This allows for geotagging so you can send notifications to users based on location.

```Java
Kontext.promptLocation();
```

Make sure you have one of the following permissions in your `AndroidManifest.xml` as well.

```XML
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
```



### `setLocationShared`

METHOD

```Java
Kontext.setLocationShared(false);
```

Disable or enable location collection (defaults to enabled if your app has location permission).



## Sending Notifications

### `postNotification`

METHOD

Allows you to send notifications from user to user or schedule ones in the future to be delivered to the current device.

| Parameter   | Type       | Description                   |
| ----------- | ---------- | ----------------------------- |
| `paramters` | JSONObject | Contains notification options |



### `cancelNotification`

METHOD

Cancels a single Kontext notification based on its Android notification integer id. Use instead of Android's `NotificationManager.cancel(id);` otherwise the notification will be restored when your app is restarted.

```Java
int id = 1234;
Kontext.cancelNotification(id);
```



### `clearKontextNotifications`

METHOD

Removes all Kontext notifications from the Notification Shade. If you just use `NotificationManager.cancelAll();`Kontext notifications will be restored your app is restarted.

```Java
Kontext.clearKontextNotifications();
```



### `setSubscription`

METHOD

You can call this method with false to opt users out of receiving all notifications through Kontext. You can pass true later to opt users back into notifications.

| Parameter | Type    |
| --------- | ------- |
| `enable`  | boolean |

```Java
Kontext.setSubscription(false);
```



### `NotificationExtenderService`

METHOD

Kontext supports sending additional data along with a notification as key value pairs. You can read this additional data when a notification is opened by adding a [NotificationOpenedHandler](https://documentation.kontext.in/docs#section--notificationopenedhandler-) instead.

However if you want to do one of the following continue with the instructions below.

- Receive data in the background with or without displaying a notification.
- Override specific notification settings depending on client side app logic such as custom accent color, vibration pattern, or other any other `NotificationCompat` options available.

**1.** Create a class that extents `NotificationExtenderService` and implement the `onNotificationProcessing` method.

```Java
import com.kontext.OSNotificationPayload;
import com.kontext.NotificationExtenderService;

public class NotificationExtenderBareBonesExample extends NotificationExtenderService {
   @Override
   protected boolean onNotificationProcessing(OSNotificationReceivedResult receivedResult) {
     	// Read properties from result.
     
      // Return true to stop the notification from displaying.
      return false;
   }
}
```

**2.** Add the following to your `AndroidManifest.xml`.
*Replace 'YOUR_CLASS_NAME' with the class name you used above.*

```XML
<service
   android:name=".YOUR_CLASS_NAME"
   android:permission="android.permission.BIND_JOB_SERVICE"
   android:exported="false">
   <intent-filter>
      <action android:name="com.kontext.NotificationExtender" />
   </intent-filter>
</service>
```

**3.** To override or extend specific notification properties call `displayNotification` with `OverrideSettings`.

```Java
import android.support.v4.app.NotificationCompat;

import com.kontext.OSNotificationPayload;
import com.kontext.NotificationExtenderService;

import java.math.BigInteger;

public class NotificationExtenderExample extends NotificationExtenderService {
   @Override
   protected boolean onNotificationProcessing(OSNotificationReceivedResult receivedResult) {
      OverrideSettings overrideSettings = new OverrideSettings();
      overrideSettings.extender = new NotificationCompat.Extender() {
         @Override
         public NotificationCompat.Builder extend(NotificationCompat.Builder builder) {
            // Sets the background notification color to Green on Android 5.0+ devices.
            return builder.setColor(new BigInteger("FF00FF00", 16).intValue());
         }
      };

      OSNotificationDisplayedResult displayedResult = displayNotification(overrideSettings);
			Log.d("KontextExample", "Notification displayed with id: " + displayedResult.androidNotificationId);

      return true;
   }
}
```

**Additional Notes**
`NotificationExtenderService` is an Android `IntentService` so please do all your work synchronously. A wake lock is obtained so the device will not sleep while you're processing the payload. 



## Email

### `setEmail`

METHOD

`setEmail` allows you to set the user's email address with the Kontext SDK. We offer several overloaded versions of this method.

```Java
Kontext.setEmail("example@domain.com");
```

If you have a backend server, we strongly recommend using [Identity Verification](https://documentation.kontext.in/docs/identity-verification) with your users. Your backend can generate an **email authentication token** and send it to your app. The following code also includes callbacks:

```Java
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



### `logoutEmail`

METHOD

If your app implements logout functionality, you can call `logoutEmail` to dissociate the email from the device:

```Java
Kontext.logoutEmail();
```



### `addEmailSubscriptionObserver`

METHOD

We have also added a new email subscription observer to track changes to email subscriptions (ie. the user sets their email or logs out). In order to subscribe to email subscription changes you can implement the following:

```Java
Kontext.addEmailSubscriptionObserver(subscriptionObserver);
```

Now, whenever the email subscription changes, this method will be called:

```Java
OSEmailSubscriptionObserver subscriptionObserver = new OSEmailSubscriptionObserver() {
   @Override
   public void onOSEmailSubscriptionChanged(OSEmailSubscriptionStateChanges stateChanges) {
   }
};
```



## Receiving Notifications

### `NotificationReceivedHandler`

HANDLER

Fires when a notification is received. It will be fired when your app is in focus or in the background.

| Parameter      | Type                                                         | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `notification` | [OSNotification](https://documentation.kontext.in/docs#section--osnotification-) | Contains user's response and properties of the notification. |

```Java
class ExampleNotificationReceivedHandler implements Kontext.NotificationReceivedHandler {
  @Override
  public void notificationReceived(OSNotification notification) {
    JSONObject data = notification.payload.additionalData;
    String customKey;

    if (data != null) {
      customKey = data.optString("customkey", null);
      if (customKey != null)
        Log.i("KontxtExample", "customkey set with value: " + customKey);
    }
  }
}
```

!!! warning "Important Behavior Note"
    If you will be displaying your own in app message when a notification is received make sure to call inFocusDisplaying with None to disable Kontext's in app AlertBox.



### `NotificationOpenedHandler`

HANDLER

Use to process a Kontext notification the user just tapped on.

| Parameter | Type                                                         | Description                                                  |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `result`  | [OSNotificationOpenResult](https://documentation.kontext.in/docs#section--osnotificationopenresult-) | Contains user's response and properties of the notification. |

```Java
class ExampleNotificationOpenedHandler implements Kontext.NotificationOpenedHandler {
  // This fires when a notification is opened by tapping on it.
  @Override
  public void notificationOpened(OSNotificationOpenResult result) {
    OSNotificationAction.ActionType actionType = result.action.type;
    JSONObject data = result.notification.payload.additionalData;
    String customKey;

    if (data != null) {
      customKey = data.optString("customkey", null);
      if (customKey != null)
        Log.i("KontextExample", "customkey set with value: " + customKey);
    }

    if (actionType == OSNotificationAction.ActionType.ActionTaken)
      Log.i("KontextExample", "Button pressed with id: " + result.action.actionID);

    // The following can be used to open an Activity of your choice.
    // Replace - getApplicationContext() - with any Android Context.
    // Intent intent = new Intent(getApplicationContext(), YourActivity.class);
    // intent.setFlags(Intent.FLAG_ACTIVITY_REORDER_TO_FRONT | Intent.FLAG_ACTIVITY_NEW_TASK);
    // startActivity(intent);

     // Add the following to your AndroidManifest.xml to prevent the launching of your main Activity
     //   if you are calling startActivity above.
     /* 
        <application ...>
          <meta-data android:name="com.kontext.NotificationOpened.DEFAULT" android:value="DISABLE" />
        </application>
     */
  }
}
```



### `OSNotificationOpenResult`

CLASS

The information returned from a notification the user received.

| Parameter      | Type                                                         | Description                                   |
| -------------- | ------------------------------------------------------------ | --------------------------------------------- |
| `notification` | [OSNotification](https://documentation.kontext.in/docs#section--osnotification-) | Notification the user received.               |
| `action`       | [OSNotificationAction](https://documentation.kontext.in/docs#section--osnotificationaction-) | The action the user took on the notification. |



### `OSNotification`

CLASS

The notification the user received.

| Parameter               | Type                                                         | Description                                                  |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `isAppInFocus`          | boolean                                                      | Was app in focus.                                            |
| `shown`                 | boolean                                                      | Was notification shown to the user. Will be false for silent notifications. |
| `androidNotificationId` | int                                                          | Android Notification assigned to the notification. Can be used to cancel or replace the notification. |
| `payload`               | [OSNotificationPayload](https://documentation.kontext.in/docs#section--osnotificationpayload-) | Payload received from Kontext.                               |
| `displayType`           | [DisplayType](https://documentation.kontext.in/docs#section--displaytype-) | How the notification was displayed to the user. Can be set to `Notification`, `InAppAlert`, or `None` if it was not displayed. |
| ` groupedNotifications` | List<OSNotificationPayloaod>                                 | Notification is a summary notification for a group this will contain all notification payloads it was created from. |



#### `DisplayType`

How the notification was displayed to the user. Part of [OSNotification](https://documentation.kontext.in/docs#section--osnotification-). See [inFocusDisplaying](https://documentation.kontext.in/docs#section--infocusdisplaying-) for more information on how this is used. 

`Notification` - native notification display.
`InAppAlert` (DEFAULT) - native alert dialog display.
`None` - notification is silent, or [inFocusDisplaying](https://documentation.kontext.in/docs#section--infocusdisplaying-) is disabled.



### `OSNotificationAction`

CLASS

The action the user took on the notification.

| Parameter  | Type       | Description                                                  |
| ---------- | ---------- | ------------------------------------------------------------ |
| `type`     | ActionType | Was the notification opened normally (`Opened`) or was a button pressed on the notification (`ActionTaken`). |
| `actionId` | String     | If `type` == `ActionTaken` then this will contain the id of the button pressed. |



### `OSNotificationPayload`

CLASS

Contents and settings of the notification the user received.

| Parameter                | Type                                                         | Description                                                  |
| ------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ` notificationID`        | String                                                       | Kontext notification UUID.                                   |
| `title`                  | String                                                       | Title of the notification.                                   |
| `body`                   | String                                                       | Body of the notification.                                    |
| ` additionalData`        | JSONObject                                                   | Custom additional data that was sent with the notification.  |
| `smallIcon`              | String                                                       | Small icon resource name set on the notification.            |
| `largeIcon`              | String                                                       | Large icon set on the notification.                          |
| `bigPicture`             | String                                                       | Big picture image set on the notification.                   |
| ` smallIconAccentColor`  | String                                                       | Accent color shown around small notification icon on Android 5+ devices. ARGB format. |
| `launchUrl`              | String                                                       | URL to open when opening the notification.                   |
| `sound`                  | String                                                       | Sound resource to play when the notification is shown.       |
| `ledColor`               | String                                                       | Devices that have a notification LED will blink in this color. ARGB format |
| ` lockScreenVisibility`  | int                                                          | Privacy setting for how the notification should be shown on the lockscreen of Android 5+ devices.<br /> `1` (DEFAULT) - Public (fully visible)<br /> `0` - Private (Contents are hidden)<br /> `-1` - Secret (not shown). |
| ` groupKey`              | String                                                       | Notifications with this same key will be grouped together as a single summary notification. |
| ` groupMessage`          | string                                                       | Summary text displayed in the summary notification.          |
| `actionButtons`          | List<ActionButton>                                           | List of action buttons on the notification.                  |
| ` fromProjectNumber`     | String                                                       | The Google project number the notification was sent under.   |
| ` backgroundImageLayout` | [BackgroundImageLayout](https://documentation.kontext.in/docs#section--backgroundimagelayout-) | If a background image was set this object will be available. |
| ` rawPayload`            | String                                                       | Raw JSON payload string received from  Kontext.              |



#### `ActionButton`

OBJECT

List of action buttons on the notification. Part of [OSNotificationPayload](https://documentation.kontext.in/docs#section--osnotificationpayload-).

| Parameter | Type   | Description                          |
| --------- | ------ | ------------------------------------ |
| `id`      | String | Id assigned to the button.           |
| `text`    | String | Text show on the button to the user. |
| `icon`    | String | Icon shown on the button.            |



#### `BackgroundImageLayout`

OBJECT

If a background image was set, this object will be available. Part of [OSNotificationPayload](https://documentation.kontextl.com/docs#section--osnotificationpayload-).

| Parameter         | Type   | Description                                               |
| ----------------- | ------ | --------------------------------------------------------- |
| `image`           | String | Image URL or name used as the background image.           |
| ` titleTextColor` | String | Text color of the title on the notification. ARGB Format. |
| ` bodyTextColor`  | String | Text color of the body on the notification. ARGB Format.  |



### Opened Action

ANDROID MANIFEST

By default Kontext will open or resume your launcher Activity when a notification is tapped on. You can disable this behavior by adding the meta-data tag `com.kontext.NotificationOpened.DEFAULT` set to `DISABLE` inside your application tag in your `AndroidManifest.xml`.

```XML
<application ...>
   <meta-data android:name="com.kontext.NotificationOpened.DEFAULT" android:value="DISABLE" />
</application>
```

Make sure you are initializing `Kontext` with [setNotificationOpenedHandler](https://documentation.kontext.in/docs#section--setnotificationopenedhandler-) in the `onCreate` method in your `Application` class. You will need to call `startActivity` from this callback.



## Appearance

### `enableVibrate`

METHOD

By default Kontext always vibrates the device when a notification is displayed unless the device is in a total silent mode. Passing false means that the device will only vibrate lightly when the device is in it's vibrate only mode.

*You can link this action to a UI button to give your user a vibration option for your notifications.*

```Jav
Kontext.enableVibrate(false);
```



### `enableSound`

METHOD

By default Kontext plays the system's default notification sound when the device's notification system volume is turned on. Passing false means that the device will only vibrate unless the device is set to a total silent mode.

*You can link this action to a UI button to give your user a different sound option for your notifications.*

```java
Kontext.enableSound(false);
```



### Disable Badges

ANDROID MANIFEST

The Kontext SDK automatically sets the badge count on your app to the number of notifications that are currently in the notification shade. If you want to disable this you can add the following to your `AndroidManifest.xml`.

```XML
<application ...>
   <meta-data android:name="com.onesignal.BadgeCount" android:value="DISABLE" />
</application>
```

You can remove the badge permissions with the following entries.

```XML
<uses-permission android:name="com.sec.android.provider.badge.permission.READ" tools:node="remove" />
<uses-permission android:name="com.sec.android.provider.badge.permission.WRITE" tools:node="remove" />
<uses-permission android:name="com.htc.launcher.permission.READ_SETTINGS" tools:node="remove" />
<uses-permission android:name="com.htc.launcher.permission.UPDATE_SHORTCUT" tools:node="remove" />
<uses-permission android:name="com.sonyericsson.home.permission.BROADCAST_BADGE" tools:node="remove" />
<uses-permission android:name="com.sonymobile.home.permission.PROVIDER_INSERT_BADGE" tools:node="remove" />
<uses-permission android:name="com.anddoes.launcher.permission.UPDATE_COUNT" tools:node="remove" />
<uses-permission android:name="com.majeur.launcher.permission.UPDATE_BADGE" tools:node="remove" />
<uses-permission android:name="com.huawei.android.launcher.permission.CHANGE_BADGE" tools:node="remove"/>
<uses-permission android:name="com.huawei.android.launcher.permission.READ_SETTINGS" tools:node="remove" />
<uses-permission android:name="com.huawei.android.launcher.permission.WRITE_SETTINGS" tools:node="remove" />
```



## Debug

### `setLogLevel`

METHOD

Enable logging to help debug if you run into an issue setting up Kontext. The following options are available with increasingly more information; `NONE`, `FATAL`, `ERROR`, `WARN`, `INFO`, `DEBUG`, `VERBOSE`

| Parameter      | Type      | Description                                                |
| -------------- | --------- | ---------------------------------------------------------- |
| `logLevel`     | LOG_LEVEL | Sets the logging level to print to the Android LogCat log. |
| ` visualLevel` | LOG_LEVEL | Sets the logging level to show as alert dialogs.           |

```java
Kontext.setLogLevel(Kontext.LOG_LEVEL.DEBUG, Kontext.LOG_LEVEL.DEBUG);
```