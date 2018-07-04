

# iOS Native SDK

Kontext iOS Native SDK Reference

!!! info "Just starting with Android?"

    Check out our Android SDK Setup guide.

!!! tip "Upgrade to 2.5.1+"

     A number the methods and classes below were recently added in our 3.5.1 SDK. Make sure you have updated to this version.

For Developers

| Calls                                                        | Type     | Description        |
| ------------------------------------------------------------ | -------- | ------------------ |
| Initialization                                               |          |                    |
| [initWithLaunchOptions](https://documentation.kontext.in/docs/ios-native-sdk#section--initwithlaunchoptions-) | Method   | Initialize Kontext |
|                                                              |          |                    |
| Privacy                                                      |          |                    |
| [setRequiresUserPrivacyConsent](https://documentation.kontext.in/docs/ios-native-sdk#section--setrequiresuserprivacyconsent-) | Mothod   |                    |
| [consentGranted](https://documentation.kontext.in/docs/ios-native-sdk#section--consentgranted-) | Mothod   |                    |
| [requiresUserPrivacyConsent](https://documentation.kontext.in/docs/ios-native-sdk#section--requiresuserprivacyconsent-) | boolean  |                    |
|                                                              |          |                    |
| Settings                                                     |          |                    |
| [KontextSettingsKeyAutoPrompt](https://documentation.kontext.in/docs/ios-native-sdk#section--kossettingskeyautoprompt-) | key      |                    |
| [KontextSettingsKeyInAppLaunchURL](https://documentation.kontext.in/docs/ios-native-sdk#section--kossettingskeyinapplaunchurl-) | key      |                    |
| [inFocusDisplayType](https://documentation.kontext.in/docs/ios-native-sdk#section--infocusdisplaytype-) | Property |                    |
|                                                              |          |                    |
| Prompting                                                    |          |                    |
| [promptForPushNotificationsWithUserResponse](https://documentation.kontext.in/docs/ios-native-sdk#section--promptforpushnotificationswithuserresponse-) | Method   |                    |
|                                                              |          |                    |
| Status                                                       |          |                    |
| [getPermissionSubscriptionState](https://documentation.kontext.in/docs/ios-native-sdk#section--getpermissionsubscriptionstate-) | Method   |                    |
| [addPermissionObserver](https://documentation.kontext.in/docs/ios-native-sdk#section--addpermissionobserver-) | Method   |                    |
| [addSubscriptionObserver](https://documentation.kontext.in/docs/ios-native-sdk#section--addsubscriptionobserver-) | Method   |                    |
|                                                              |          |                    |
| Events                                                       |          |                    |
| [sendEvent](https://documentation.kontext.in/docs/ios-native-sdk#section--sendtag-) | Method   |                    |
| [sendEvents](https://documentation.kontext.in/docs/ios-native-sdk#section--sendtag-) | Method   |                    |
| [sendScreen](https://documentation.kontext.in/docs/ios-native-sdk#section--sendtag-) | Method   |                    |
| [sendUserAttributes](https://documentation.kontext.in/docs/ios-native-sdk#section--sendtag-) | Method   |                    |
|                                                              |          |                    |
| Data                                                         |          |                    |
| [setLocationShared](https://documentation.kontext.in/docs/ios-native-sdk#section--setLocationShared-) | Method   |                    |
| [promptLocation](https://documentation.kontext.in/docs/ios-native-sdk#section--promptlocation-) | Method   |                    |
|                                                              |          |                    |
| Sending Notifications                                        |          |                    |
| [postNotification](https://documentation.kontext.in/docs/ios-native-sdk#section--postnotification-) | Method   |                    |
| [clearKontextNotifications](https://documentation.kontext.in/docs/ios-native-sdk#section--clearkontextnotifications-) | Method   |                    |
| [setSubscription](https://documentation.kontext.in/docs/ios-native-sdk#section--setsubscription-) | Method   |                    |
|                                                              |          |                    |
| Email                                                        |          |                    |
| [setEmail](https://documentation.kontext.in/docs/ios-native-sdk#section--setemail-) | Method   |                    |
| [logoutEmail](https://documentation.kontext.in/docs/ios-native-sdk#section--logoutemail-) | Method   |                    |
| [addEmailSubscriptionObserver](https://documentation.kontext.in/docs/ios-native-sdk#section--addemailsubscriptionobserver-) | Method   |                    |
|                                                              |          |                    |
| Notification Events                                          |          |                    |
| [handleNotificationReceived](https://documentation.kontext.in/docs/ios-native-sdk#section--oshandlenotificationreceivedblock-) | Method   |                    |
| [handleNotificationAction](https://documentation.kontext.in/docs/ios-native-sdk#section--oshandlenotificationactionblock-) | Method   |                    |
|                                                              |          |                    |
| Objects                                                      |          |                    |
| [KontextNotificationOpenedResult](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationopenedresult-) | Object   |                    |
| [KontextNotification](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotification-) | Object   |                    |
| [KontextNotificationAction](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationaction-) | Object   |                    |
| [KontextNotificationActionType](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationactiontype-) | Object   |                    |
| [KontextNotificationDisplayType](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationdisplaytype-) | Object   |                    |
| [KontextNotificationPayload](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationpayload-) | Object   |                    |
|                                                              |          |                    |
| Debug                                                        |          |                    |
| [setLogLevel](https://documentation.kontext.in/docs/ios-native-sdk#section--setloglevel-) | Mothod   |                    |



## Initialization

### `initWithLaunchOptions`

METHOD

Must be called from `didFinishLaunchingWithOptions` in `AppDelegate.m`.

| Parameter        | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| ` launchOptions` | NSDictionary*                                                | REQUIRED launchOptions that you received from `didFinishLaunchingWithOptions` |
| `appId`          | NSString*                                                    | REQUIRED Your Kontext app id, available in [Keys & IDs](https://documentation.kontext.in/docs/accounts-and-keys#section-keys-ids) |
| `callback`       | [KontextHandleNotificationReceivedBlock](https://documentation.kontext.in/docs/ios-native-sdk#section--oshandlenotificationreceivedblock-) | Function to be called when a notification is received        |
| `callback`       | [KontextHandleNotificationActionBlock](https://documentation.kontext.in/docs/ios-native-sdk#section--oshandlenotificationactionblock-) | Function to be called when a user reacts to a notification received |
| `settings`       | NSDictionary*                                                | Customization settings to change Kontext's default behavior  |

!!! info "iOS 8+ Notes"

    1. `application:didRegisterForRemoteNotificationsWithDeviceToken:` will still fire even if KontextSettingsKeyAutoPrompt is set to false.
    
    2. Replace any of your `isRegisteredForRemoteNotifications` calls with `currentUserNotificationSettings` or getPermissionSubscriptionState.

### iOS 8+ Notes

- `application:didRegisterForRemoteNotificationsWithDeviceToken:` will still fire even if `KontextSettingsKeyAutoPrompt` is set to `false`.
- Replace any of your `isRegisteredForRemoteNotifications` calls with `currentUserNotificationSettings` or [getPermissionSubscriptionState](https://documentation.kontext.in/docs/ios-native-sdk#section--getpermissionsubscriptionstate-).

``` swift tab="Swift"
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {

   let notificationReceivedBlock: OSHandleNotificationReceivedBlock = { notification in

      print("Received Notification: \(notification!.payload.notificationID)")
   }

   let notificationOpenedBlock: OSHandleNotificationActionBlock = { result in
      // This block gets called when the user reacts to a notification received
      let payload: OSNotificationPayload = result!.notification.payload

      var fullMessage = payload.body
      print("Message = \(fullMessage)")

      if payload.additionalData != nil {
         if payload.title != nil {
            let messageTitle = payload.title
               print("Message Title = \(messageTitle!)")
         }

         let additionalData = payload.additionalData
         if additionalData?["actionSelected"] != nil {
            fullMessage = fullMessage! + "\nPressed ButtonID: \(additionalData!["actionSelected"])"
         }
      }
   }

   let onesignalInitSettings = [kOSSettingsKeyAutoPrompt: false,
      kOSSettingsKeyInAppLaunchURL: true]

   Kontext.initWithLaunchOptions(launchOptions, 
      appId: "YOUR_KONTEXT_APP_ID", 
      handleNotificationReceived: notificationReceivedBlock, 
      handleNotificationAction: notificationOpenedBlock, 
      settings: onesignalInitSettings)

   Kontext.inFocusDisplayType = OSNotificationDisplayType.notification

   return true
}
```

``` objective-c tab="Objective-C"
- (BOOL)application:(UIApplication*)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
 
  id notificationReceiverBlock = ^(OSNotification *notification) {
    NSLog(@"Received Notification - %@", notification.payload.notificationID);
  };
  
  id notificationOpenedBlock = ^(OSNotificationOpenedResult *result) {
        // This block gets called when the user reacts to a notification received
        OSNotificationPayload* payload = result.notification.payload;
        
        NSString* messageTitle = @"Kontext Example";
        NSString* fullMessage = [payload.body copy];
        
        if (payload.additionalData) {
            
            if(payload.title)
                messageTitle = payload.title;
            
            NSDictionary* additionalData = payload.additionalData;
            
            if (additionalData[@"actionSelected"])
                fullMessage = [fullMessage stringByAppendingString:[NSString stringWithFormat:@"\nPressed ButtonId:%@", additionalData[@"actionSelected"]]];
        }
        
        UIAlertView* alertView = [[UIAlertView alloc] initWithTitle:messageTitle
                                                            message:fullMessage
                                                           delegate:self
                                                  cancelButtonTitle:@"Close"
                                                  otherButtonTitles:nil, nil];
        [alertView show];

   };
  
   id onesignalInitSettings = @{kOSSettingsKeyAutoPrompt : @YES};
  
   [Kontext initWithLaunchOptions:launchOptions
                              appId:@"YOUR_KONTEXT_APP_ID"
         handleNotificationReceived:notificationReceiverBlock
           handleNotificationAction:notificationOpenedBlock
                           settings:onesignalInitSettings];
  
}
```



### `setRequiresUserPrivacyConsent`

METHOD

For GDPR users, your application should call this method *before* initialization of the SDK. If you pass in `true`, your application will need to call `provideConsent(true)` before the Kontext SDK gets fully initialized. Until this happens, you can continue to call methods (such as `sendEvents()`), but nothing will happen.

```swift tab="Swift"
//to require the user's consent before the SDK initializes
Kontext.setRequiresUserPrivacyConsent(true);

Kontext.initWithLaunchOptions(launchOptions, appId: "YOUR_KONTEXT_APP_ID");
```

```objective-c tab="Objective-C"
//to require the user's consent before the SDK initializes
[Kontext setRequiresUserPrivacyConsent:true];

[Kontext initWithLaunchOptions:launchOptions appId:@"YOUR_KONTEXT_APP_ID"];
```



### `consentGranted`

METHOD

If you set the SDK to require the user's privacy consent, your application can use this method once the user does or doesn't provide privacy consent to use the Kontext SDK.

```swift tab="Swift"
@IBAction func userTappedProvideConsentButton(_ sender : UIButton) {
  //this will complete the initialization of the SDK
	Kontext.provideConsent(true); 
}
```

```objective-c tab="Objective-C"
- (IBAction)setEmailButtonPressed:(UIButton *)sender {
  //this will complete the initialization of the SDK
  [Kontext provideConsent:true];
}
```



### `requiresUserPrivacyConsent`

BOOLEAN

You can use this property to check if the Kontext SDK is waiting for the user to provide privacy consent.

`true` - Indicates that the Kontext SDK hasn't received the user's privacy consent yet
`false` - Either the user has already provided consent, or your app isn't set to require consent.



### `kontextSettingsKeyAutoPrompt`

KEY

`true` (DEFAULT) - automatically prompts for notifications permissions.
`false` - disables auto prompt.



### `KontextSettingsKeyInAppLaunchURL`

KEY

`true` (DEFAULT) - Open all URLs with a in-app WebView window.
`false` - Launches Safari with the URL OR other app (if deep linked or custom URL scheme passed).



### `inFocusDisplayType`

PROPERTY

Setting to control how Kontext notifications will be shown when one is received while your app is in focus, for apps targeting.

`KontextNotificationDisplayTypeNotification` - Native notification display
`KontextNotificationDisplayTypeInAppAlert` (DEFAULT) - Alert dialog display.
`KontextNotificationDisplayTypeNone` - Notification is silent and not shown

**Swift format:**
`KontextNotificationDisplayType.notification`
`KontextNotificationDisplayType.inAppAlert`
`KontextNotificationDisplayType.none`

```swift tab="Swift"
Kontext.inFocusDisplayType = OSNotificationDisplayType.notification
```

```objective-c tab="Objective-C"
Kontext.inFocusDisplayType = OSNotificationDisplayTypeNotification;
```

!!! warning "iOS 9 and below"

    The Notification setting will fall back to InAppAlert .



## Registering Push

### `promptForPushNotificationsWithUserResponse`

METHOD

Prompt the user for notification permissions. Callback fires as soon as the user accepts or declines notifications.

#### Requirements

Must set `kontextSettingsKeyAutoPrompt` to `false` when calling [initWithLaunchOptions](https://documentation.kontext.in/docs/ios-native-sdk#section--initwithlaunchoptions-).

#### Recommendations

You can only prompt once so it is recommend to explain what benefits notifications will give the user.

#### Example

```swift tab="Swift"
// Call when you want to prompt the user to accept push notifications. 
// Only call once and only if you set kOSSettingsKeyAutoPrompt in AppDelegate to false.
Kontext.promptForPushNotifications(userResponse: { accepted in
   print("User accepted notifications: \(accepted)")
})
```

```objective-c tab="Objective-C"
[Kontext promptForPushNotificationsWithUserResponse:^(BOOL accepted) {
  NSLog(@"Accepted Notifications?: %d", accepted);
}];
```



### `getPermissionSubscriptionState`

METHOD

Get the current notification and permission state. Returns a `KontextPermissionSubscriptionState` type described below.



#### KontextPermissionSubscriptionState

| Parameter             | Type                      | Description                             |
| --------------------- | ------------------------- | --------------------------------------- |
| ` permissionStatus`   | KontextPermissionState*   | iKontext Notification Permissions state |
| ` subscriptionStatus` | KontextSubscriptionState* | Apple and Kontext subscription state    |

```swift tab="Swift"
let status: OSPermissionSubscriptionState = Kontext.getPermissionSubscriptionState()

let hasPrompted = status.permissionStatus.hasPrompted
print("hasPrompted = \(hasPrompted)")
let userStatus = status.permissionStatus.status
print("userStatus = \(userStatus)")

let isSubscribed = status.subscriptionStatus.subscribed
print("isSubscribed = \(isSubscribed)")
let userSubscriptionSetting = status.subscriptionStatus.userSubscriptionSetting
print("userSubscriptionSetting = \(userSubscriptionSetting)")
let userID = status.subscriptionStatus.userId
print("userID = \(userID)")
let pushToken = status.subscriptionStatus.pushToken
print("pushToken = \(pushToken)")
```

```objective-c tab="Objective-C"
OSPermissionSubscriptionState* status = [Kontext getPermissionSubscriptionState];
status.permissionStatus.hasPrompted;
status.permissionStatus.status;
    
status.subscriptionStatus.subscribed;
status.subscriptionStatus.userSubscriptionSetting;
status.subscriptionStatus.userId;
status.subscriptionStatus.pushToken;
```



### `addPermissionObserver`

METHOD

The `onKontextPermissionChanged` method will be fired on the passed in object when a notification permission setting changes.
This includes the following events: 

- Notification permission prompt shown
- The user accepting or declining the permission prompt
- Enabling/disabling notifications for your app in the iKontext Settings after returning to your app.

#### Example

Example of setting up with your AppDelegate.
Output is showings the user accepting the notification permission prompt.

```swift tab="Swift"
// AppDelegate.swift
// Add OSPermissionObserver after UIApplicationDelegate
class AppDelegate: UIResponder, UIApplicationDelegate, OSPermissionObserver {

   func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
      // Add your AppDelegate as an obsserver
      Kontext.add(self as OSPermissionObserver)
   }

   // Add this new method
   func onOSPermissionChanged(_ stateChanges: OSPermissionStateChanges!) {
      // Example of detecting answering the permission prompt
      if stateChanges.from.status == OSNotificationPermission.notDetermined {
         if stateChanges.to.status == OSNotificationPermission.authorized {
            print("Thanks for accepting notifications!")
         } else if stateChanges.to.status == OSNotificationPermission.denied {
            print("Notifications not accepted. You can turn them on later under your iOS settings.")
         }
      }
      // prints out all properties
      print("PermissionStateChanges: \n\(stateChanges)")
   }

   // Output:
   /*
   Thanks for accepting notifications!
   PermissionStateChanges:
   Optional(<OSSubscriptionStateChanges:
   from: <OSPermissionState: hasPrompted: 0, status: NotDetermined>,
   to:   <OSPermissionState: hasPrompted: 1, status: Authorized>
   >
   */
}
```

```objective-c tab="Objective-C"
// AppDelegate.h
// Add OSPermissionObserver after UIApplicationDelegate
@interface AppDelegate : UIResponder <UIApplicationDelegate, OSPermissionObserver>
@end

// AppDelegate.m
@implementation AppDelegate
  
- (BOOL)application:(UIApplication*)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  // Add your AppDelegate as an obsserver
  [Kontext addPermissionObserver:self];
}

// Add this new method
- (void)onOSPermissionChanged:(OSPermissionStateChanges*)stateChanges {
  
    // Example of detecting anwsering the permission prompt
    if (stateChanges.from.status == OSNotificationPermissionNotDetermined) {
      if (stateChanges.to.status == OSNotificationPermissionAuthorized)
         NSLog(@"Thanks for accepting notifications!");
      else if (stateChanges.to.status == OSNotificationPermissionDenied)
         NSLog(@"Notifications not accepted. You can turn them on later under your iOS settings.");
    }
    
   // prints out all properties 
   NSLog(@"PermissionStateChanges:\n%@", stateChanges);
}

// Output:
/*
Thanks for accepting notifications!
PermissionStateChanges:
<OSSubscriptionStateChanges:
from: <OSPermissionState: hasPrompted: 1, status: NotDetermined>,
to:   <OSPermissionState: hasPrompted: 1, status: Authorized>
>
*/

@end
```



### `addSubscriptionObserver`

METHOD

The `onKontextSubscriptionChanged` method will be fired on the passed in object when a notification subscription property changes.

This includes the following events:

- Getting a push token from Apple
- Getting a player / user id from Kontext
- `Kontext.setSubscription` is called
- User disables or enables notifications

#### Example

Example of setting up with your AppDelegate. Output is showing the capture the device subscribing to Kontext.

```swift tab="Swift"
// AppDelegate.swift
// Add OSSubscriptionObserver after UIApplicationDelegate
class AppDelegate: UIResponder, UIApplicationDelegate, OSSubscriptionObserver {

   func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
      // Add your AppDelegate as an obsserver
      Kontext.add(self as OSSubscriptionObserver)
   }

   // Add this new method
   func onOSSubscriptionChanged(_ stateChanges: OSSubscriptionStateChanges!) {
      if !stateChanges.from.subscribed && stateChanges.to.subscribed {
         print("Subscribed for Kontext push notifications!")
         // get player ID
         stateChanges.to.userId
      }
      print("SubscriptionStateChange: \n\(stateChanges)")
   }

   // Output:
   /*
   Subscribed for Kontext push notifications!
   PermissionStateChanges:
   Optional(<OSSubscriptionStateChanges:
   from: <OSSubscriptionState: userId: (null), pushToken: 0000000000000000000000000000000000000000000000000000000000000000 userSubscriptionSetting: 1, subscribed: 0>,
   to:   <OSSubscriptionState: userId: 11111111-222-333-444-555555555555, pushToken: 0000000000000000000000000000000000000000000000000000000000000000, userSubscriptionSetting: 1, subscribed: 1>
   >
   */
}
```

```objective-c tab="Objective-C"
// AppDelegate.h
// Add OSSubscriptionObserver after UIApplicationDelegate
@interface AppDelegate : UIResponder <UIApplicationDelegate, OSSubscriptionObserver>
@end

// AppDelegate.m
@implementation AppDelegate
  
- (BOOL)application:(UIApplication*)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  // Add your AppDelegate as an obsserver
  [Kontext addSubscriptionObserver:self];
}

// Add this new method
- (void)onOSSubscriptionChanged:(OSSubscriptionStateChanges*)stateChanges {
  
    // Example of detecting subscribing to Kontext
    if (!stateChanges.from.subscribed && stateChanges.to.subscribed) {
      NSLog(@"Subscribed for Kontext push notifications!");
      // get player ID
      stateChanges.to.userId;
    }
    
   // prints out all properties
   NSLog(@"SubscriptionStateChanges:\n%@", stateChanges);
}

// Output:
/*
Subscribed for Kontext push notifications!
PermissionStateChanges:
<OSSubscriptionStateChanges:
from: <OSSubscriptionState: userId: (null), pushToken: 0000000000000000000000000000000000000000000000000000000000000000 userSubscriptionSetting: 1, subscribed: 0>,
to:   <OSSubscriptionState: userId: 11111111-222-333-444-555555555555, pushToken: 0000000000000000000000000000000000000000000000000000000000000000, userSubscriptionSetting: 1, subscribed: 1>
>
*/

@end
```



#### Advanced Observer Details

Any object implementing the `KontextPermissionObserver` and/or the `KontextSubscriptionObserver` protocols can be added as an observer. You can call `removePermissionObserver` to remove any existing listeners.
Kontext uses a weak reference to the observer to prevent leaks.



### `sendEvent`

METHOD

Tag a user based on an app event of your choosing so later you can create segments on [kontext.in](https://kontext.in/) to target these users. Recommend using sendEvents over sendEvent if you need to set more than one tag on a user at a time.

| Parameter              | Type                        | Description                                  |
| ---------------------- | --------------------------- | -------------------------------------------- |
| `key`                  | NSString*                   | Key of your choosing to create or update     |
| `value`                | NSString*                   | Value to set on the key.                     |
| ` onSuccess(Optional)` | KontextResultSuccessBlock | Call if there were no errors sending the tag |
| ` onFailure(Optional)` | KontextFailureBlock       | Called if there was an error                 |

```swift tab="Swift"
Kontext.sendEvent("key", value: "value")
```

```objective-c tab="Objective-C"
[Kontext sendEvent:@"key" value:@"value"];
```



### `sendEvents`

METHOD

Tag a user based on an app event of your choosing so later you can create segments on [kontext.in](https://kontext.in/) to target these users.

| Parameter              | Type                        | Description                                           |
| ---------------------- | --------------------------- | ----------------------------------------------------- |
| `keyValues`            | NSDictionary*               | Key value pairs of your choosing to create or update. |
| ` onSuccess(Optional)` | KontextResultSuccessBlock | Call if there were no errors sending the tag          |
| ` onFailure(Optional)` | KontextFailureBlock       | Called if there was an error                          |

```swift tab="Swift"
Kontext.sendEvents(["key1": "value1", "key2": "value2"])
```

```objective-c tab="Objective-C"
[Kontext sendEvents:@{@"key1" : @"value1", @"key2" : @"value2"}];
```



### `sendScreen`

METHOD

Tag a user based on an app event of your choosing so later you can create segments on [kontext.in](https://kontext.in/) to target these users. Recommend using sendEvents over sendEvent if you need to set more than one tag on a user at a time.

| Parameter              | Type                        | Description                                  |
| ---------------------- | --------------------------- | -------------------------------------------- |
| `value`                | NSString*                   | Value to screen.                             |
| ` onSuccess(Optional)` | KontextResultSuccessBlock | Call if there were no errors sending the tag |
| ` onFailure(Optional)` | KontextFailureBlock       | Called if there was an error                 |

```swift tab="Swift"
Kontext.sendScreen("ScreenName")
```

```objective-c tab="Objective-C"
[Kontext sendScreen:@"ScreenName"];
```



### `sendUserAttributes`

METHOD

Tag a user based on an app event of your choosing so later you can create segments on [kontext.in](https://kontext.in/) to target these users.

| Parameter              | Type                        | Description                                           |
| ---------------------- | --------------------------- | ----------------------------------------------------- |
| `keyValues`            | NSDictionary*               | Key value pairs of your choosing to create or update. |
| ` onSuccess(Optional)` | KontextResultSuccessBlock | Call if there were no errors sending the tag          |
| ` onFailure(Optional)` | KontextFailureBlock       | Called if there was an error                          |

```swift tab="Swift"
Kontext.sendEvents(["name": "Jhon Doe", "age": 24, "gender": "M", "city": "Pune"])
```

```objective-c tab="Objective-C"
[Kontext sendEvents:@{@"name": @"Jhon Doe", @"age": @24, @"gender": @"M", @"city": @"Pune"}];
```



## Data

### `setLocationShared`

METHOD

Allows you to enable or disable Kontext SDK location collection. Due to Apple's [App Store Guidelines](https://developer.apple.com/app-store/review/guidelines/#location), it is required in iKontext applications to get the user's consent before collecting location. 

### `promptLocation`

METHOD

Prompts the user for location permissions to allow geotagging from the Kontext dashboard. This lets you send notifications based on the device's location.

Note: Requires the follow entries in your .plist file.

- `NSLocationUsageDescription` (For iKontext 7 and later)
- `NSLocationWhenInUseUsageDescription`
  Optional:
- `NSLocationAlwaysAndWhenInUseUsageDescription` and `NSLocationAlwaysUsageDescription` along with `UIBackgroundModes -> location`
  Example plist image: <https://i.imgur.com/OZDQpyQ.png>

```swift tab="Swift"
Kontext.promptLocation()
```

```objective-c tab="Objective-C"
[Kontext promptLocation];
```



## Sending Notifications

### `postNotification`

METHOD

Allows you to send notifications from user to user or schedule ones in the future to be delivered to the current device.

See the [Create notification](https://documentation.kontext.in/reference#create-notification) REST API POST call for a list of all possible options. Note: You can only use `include_player_ids` as a targeting parameter from your app. Other target options such as `tags` and `included_segments` require your Kontext App REST API key which can only be used from your server.

| Parameter              | Type                        | Description                                             |
| ---------------------- | --------------------------- | ------------------------------------------------------- |
| ` parameters`          | NSDictionary*               | Dictionary of notification options                      |
| ` onSuccess(Optional)` | KontextResultSuccessBlock | Called if there were no errors sending the notification |
| ` onFailure(Optional)` | KontextFailureBlock       | Called if there was an error                            |

```swift tab="Swift"
Kontext.postNotification(["contents": ["en": "Test Message"], "include_player_ids": ["3009e210-3166-11e5-bc1b-db44eb02b120"]])
```

```objective-c tab="Objective-C"
[Kontext postNotification:@{
   @"contents" : @{@"en": @"Test Message"},
   @"include_player_ids": @[@"3009e210-3166-11e5-bc1b-db44eb02b120"]
}];
```



### `ClearKontextNotifications`

METHOD

iOS provides a standard way to clear notifications by clearing badge count, thus there is no specific Kontext API call for clearing notifications.

### `setSubscription`

METHOD

You can call this method with false to opt users out of receiving all notifications through Kontext. You can pass true later to opt users back into notifications.

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `enable`  | BOOL |             |

```swift tab="Swift"
Kontext.setSubscription(false)
```

```objective-c tab="Objective-C"
[Kontext setSubscription:false];
```



## Email

### `setEmail`

METHOD

`setEmail` allows you to set the user's email address with the Kontext SDK. We offer several overloaded versions of this method.

```swift tab="Swift"
Kontext.setEmail("example@domain.com");
```

```objective-c tab="Objective-C"
[Kontext setEmail:@"example@domain.com"];
```



### `logoutEmail`

METHOD

If your app implements logout functionality, you can call `logoutEmail` to dissociate the email from the device:

```swift tab="Swift"
Kontext.logoutEmail();
```

```objective-c tab="Objective-C"
[Kontext logoutEmail];
```



### `addEmailSubscriptionObserver`

METHOD

We have also added a new email subscription observer to track changes to email subscriptions (ie. the user sets their email or logs out). In order to subscribe to email subscription changes you can implement the following:

```swift tab="Swift"
Kontext.add(self as OSEmailSubscriptionObserver)
```

```objective-c tab="Objective-C"
[Kontext addEmailSubscriptionObserver:self];
```

Now, whenever the email subscription changes, this method will be called:

```swift tab="Swift"
func onOSEmailSubscriptionChanged(_ stateChanges: OSEmailSubscriptionStateChanges!) { 
    
}
```

```objective-c tab="Objective-C"
-(void)onOSEmailSubscriptionChanged:(OSEmailSubscriptionStateChanges *)stateChanges {
    
}
```



## Receiving Notifications

### `KontextHandleNotificationReceivedBlock`

CALLBACK

Called when the app receives a notification while in focus only. *Note: If you need this to be called when your app is in the background, set content_available to true when you create your notification. The "force-quit" state (i.e app was swiped away) is not currently supported.*

| Parameter      | Type                                                         | Description |
| -------------- | ------------------------------------------------------------ | ----------- |
| `notification` | [KontextNotification](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotification-) |             |

```swift tab="Swift"
{ notification in
	print("Received Notification - \(notification.payload.notificationID) - \(notification.payload.title)")
}
```

```objective-c tab="Objective-C"
^(OSNotification *notification) {
	NSLog(@"Received Notification - %@ - %@", notification.payload.notificationID, notification.payload.title);
}
```



### `KontextHandleNotificationActionBlock`

CALLBACK

Called when the user opens or taps an action on a notification.

| Parameter | Type                                                         | Description |
| --------- | ------------------------------------------------------------ | ----------- |
| `result`  | [KontextNotificationOpenedResult](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationopenedresult-) |             |

```swift tab="Swift"
{ result in
                
	// This block gets called when the user reacts to a notification received
	let payload: OSNotificationPayload = result!.notification.payload
	var fullMessage = payload.body
                
	//Try to fetch the action selected
	if let additionalData = payload.additionalData, actionSelected = additionalData["actionSelected"] as? String {
		fullMessage =  fullMessage + "\nPressed ButtonId:\(actionSelected)"
	}
	print("fullMessage = \(fullMessage)")
}
```

```objective-c tab="Objective-C"
^(KontextNotificationOpenedResult *result) {
        
   // This block gets called when the user opens or taps an action on a notification
   KontextNotificationPayload* payload = result.notification.payload;
        
   NSString* messageTitle = @"Kontext Example";
   NSString* fullMessage = [payload.body copy];
        
   if (payload.additionalData) {
      if (payload.title)
         messageTitle = payload.title;
            
      NSDictionary* additionalData = payload.additionalData;
            
      if (additionalData[@"actionSelected"])
         fullMessage = [fullMessage stringByAppendingString:[NSString stringWithFormat:@"\nPressed ButtonId:%@", additionalData[@"actionSelected"]]];
   }
  
   UIAlertView* alertView = [[UIAlertView alloc]
                               initWithTitle:messageTitle
                                     message:fullMessage
                                    delegate:self
                           cancelButtonTitle:@"Close"
                          otherButtonTitles:nil, nil];
   [alertView show];
}
```



### `KontextNotificationOpenedResult`

INTERFACE ELEMENT

The information returned from a notification the user received. Resulting class passed to [KontextHandleNotificationActionBlock](https://documentation.kontext.in/docs/ios-native-sdk#section--oshandlenotificationactionblock-).

| Class Properties                                             |      |
| ------------------------------------------------------------ | ---- |
| `notification`([KontextNotification](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotification-)); |      |
| `action`([KontextNotificationAction](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationaction-));\| |      |



### `KontextNotification`

INTERFACE ELEMENT

The notification the user received.

| Class Properties                                             |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `payload`([KontextNotificationPayload](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationpayload-)); |                                                              |
| `displayType`([KontextNotificationDisplayType](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationdisplaytype-)); |                                                              |
| `shown`(*BOOL*);                                             | True when the user was able to see the notification. False when app is in focus and in-app alerts are disabled, or the remote notification is silent. |
| `silentNotification`(*BOOL*);                                | True when the received notification is silent. Silent means there is no alert, sound, or badge payload in the APS dictionary. Requires remote-notification within UIBackgroundModes array of the Info.plist |



### `KontextNotificationAction`

INTERFACE ELEMENT

The action the user took on the notification.

| Class Properties                                             |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `actionID`(*NSString*);                                      | The ID associated with the button tapped. NULL when the actionType is NotificationTapped or InAppAlertClosed. |
| `type`([KontextNotificationActionType](https://documentation.kontext.in/docs/ios-native-sdk#section--osnotificationactiontype-)); | The type of the notification action.                         |



### `KontextNotificationActionType`

INTERFACE ELEMENT

The action type (*NSUInteger Enum*) associated to an KontextNotificationAction object.

| NSUInteger Enum Properties |      |
| -------------------------- | ---- |
| `opened`                   |      |
| ` ActionTaken`             |      |



### `KontextNotificationDisplayType`

INTERFACE ELEMENT

The way in which a notification was displayed to the user (*NSUInteger Enum*).

| NSUInteger Enum Properties | Raw Value |                                                              |
| -------------------------- | --------- | ------------------------------------------------------------ |
| ` Notification`            | 2         | iOS native notification display.                             |
| ` InAppAlert`              | 1         | Default UIAlertView display.                                 |
| `None`                     | 0         | Notification is silent, or app is in focus but InAppAlertNotifications are disabled. |



### `KontextNotificationPayload`

INTERFACE ELEMENT

Contents and settings of the notification the user received.

| Class Properties    | Type        | Description                                                  |
| ------------------- | ----------- | ------------------------------------------------------------ |
| `notificationID`    | NSString    | Kontext notification UUID                                    |
| ` contentAvailable` | BOOL        | Provide this key with a value of 1 to indicate that new content is available. Including this key and value means that when your app is launched in the background or resumed `application:didReceiveRemoteNotification:fetchCompletionHandler:` is called. |
| `badge`             | NSInteger   | The badge number assigned to the application icon            |
| `sound`             | NSString    | The sound parameter passed to the notification. By default set to `UILocalNotificationDefaultSoundName`. [Read more about custom sounds](https://documentation.kontext.in/docs/customize-notification-sounds) |
| `title`             | NSString    | Title text of the notification                               |
| `body`              | NSString    | Body text of the notification                                |
| `subtitle`          | NSString    | iOS 10+ - subtitle text of the notification                  |
| `launchUrl`         | NSString    | Web address to launch within the app via a `UIWebView`       |
| `additionalData`    | NSDictonary | Additional Data add to the notification by you               |
| `attachments`       | NSDictonary | iOS 10+ - Attachments sent as part of the rich notification  |
| `actionButtons`     | NSArray     | Action buttons set on the notification                       |
| `rawPayload`        | NSDictonary | Holds the raw APS payload received                           |



## Debug

### `setLogLevel`

METHOD

Enable logging to help debug if you run into an issue setting up Kontext. This selector is static so you can call it before Kontext init. The following options are available with increasingly more information; `ONE_S_LL_NONE`, `ONE_S_LL_FATAL`, `ONE_S_LL_ERROR`, `ONE_S_LL_WARN`, `ONE_S_LL_INFO`, `ONE_S_LL_DEBUG`, `ONE_S_LL_VERBOSE`.

| Parameter     | Type      | Description                                      |
| ------------- | --------- | ------------------------------------------------ |
| `logLevel`    | LOG_LEVEL | Sets the logging level to print to the Xcode log |
| `visualLevel` | LOG_LEVEL | Sets the logging level to show as alert dialogs. |

```swift tab="Swift"
Kontext.setLogLevel(.LL_DEBUG, visualLevel: .LL_DEBUG)
```

```objective-c tab="Objective-C"
[Kontext setLogLevel:ONE_S_LL_DEBUG visualLevel:ONE_S_LL_DEBUG];
```