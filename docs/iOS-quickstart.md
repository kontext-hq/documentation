

# iOS SDK Setup

!!! tip "Upgrade to 2.5.1+"

     A number the methods and classes below were recently added in our 3.5.1 SDK. Make sure you have updated to this version.

### Required For Setup

- [A Kontext Account](https://app.kontext.in/) if you do not already have one
- Your Kontext App ID and secret provided by Kontext team.
- An iOS Push Certificate. [Generate one here](/iOS/push-certificate).
- An iOS device (iPhone, iPad, iPod Touch) to test on. The Xcode simulator doesn't support push notifications so you must test on a real device.
- A Mac with a new version of Xcode



### 1. Download the SDK

[Click Here to download the SDK](https://github.com/kontext-hq/documentation/blob/master/docs/sdk/Kontext.framework.zip?raw=true)

### 2. Import Kontext into your Xcode project

**2.1** Add Kontext.framework file in Linked binaries.

![Screenshot](/assets/images/ios-13.png)

### 3. Add Required Capabilities

**3.1** Select the root project and Under Capabilities Enable "Push Notifications".

**3.2** Next Enable "Background Modes" and check "Remote notifications".

![Screenshot]()

![Screenshot](/assets/images/ios-12.png)

### 5. Add Required Code

Add following Kontext initialization code to your `AppDelegate`.

```swift tab="swift"
import Kontext

func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {

   let kontextInitSettings = [kontextSettingsKeyAutoPrompt: false]
        
   // Replace 'YOUR_APP_ID' with your Kontext App ID.
   Kontext.initWithLaunchOptions(launchOptions,
       appId: "YOUR_APP_ID",
       appSecret: "YOUR_APP_SECRET",
       handleNotificationAction: nil,
       settings: kontextInitSettings)
   
   Kontext.inFocusDisplayType = KontextNotificationDisplayType.notification;
   
   // Recommend moving the below line to prompt for push after informing the user about
   //   how your app will use them.
   Kontext.promptForPushNotifications(userResponse: { accepted in
      print("User accepted notifications: \(accepted)")
   })
      
   return true
}
```

```objective-c tab="objective-c"
#import <Kontext/Kontext.h>

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    
   [Kontext initWithLaunchOptions:launchOptions
                              appId:@"YOUR_APP_ID" appSecret: @"YOUR_APP_SECRET" handleNotificationAction:nil
                            settings:@{kontextSettingsKeyAutoPrompt: @false}];
   Kontext.inFocusDisplayType = KontextNotificationDisplayTypeNotification;
   
   // Recommend moving the below line to prompt for push after informing the user about
   //   how your app will use them.
   [Kontext promptForPushNotificationsWithUserResponse:^(BOOL accepted) {
        NSLog(@"User accepted notifications: %d", accepted);
   }];
    
   return YES;
}
```

!!! info "Note"

    Kontext `initWithLaunchOptions` must be called from your `didFinishLaunchingWithOptions`, as in the example above.

!!! Warning "Troubleshooting"

    If run into any issues please see our [iOS troubleshooting guide](/iOS/troubleshoot).

### 6. Add Email

RECOMMENDED

Next, if you collect emails from users, you can set a user's email with the `setEmail` method. This enables Kontext Email Messaging, which allows you to send emails in addition to push.

```swift tab="swift"
Kontext.setEmail("example@domain.com");
```

```objective-c tab="objective-c"
[Kontext setEmail:@"example@domain.com"];
```



### 7. Add Notification Service Extension

**7.1** In Xcode Select `File` > `New` > `Target...`

**7.2** Select `Notification Service Extension` then press `Next`.

![Screenshot](/assets/images/ios-14.png)

**7.3** Enter the product name as `KontextNotificationServiceExtension` and press `Finish`.

![Screenshot](/assets/images/ios-15.png)

**7.4** Press Cancel on the Activate scheme prompt.

![Screenshot](/assets/images/ios-16.jpg)

By cancelling, you are keeping Xcode debugging your app, instead of just the extension. If you activate by accident, you can always switch back to debug your app within Xcode (next to the play button).

**7.5** Open the Xcode project settings and select the `KontextNotificationServiceExtension` target. Unless you have a specific reason not to, you should set the `Deployment Target` to be iOS 10.

![Screenshot](/assets/images/ios-17.jpg)

**7.6** Open `NotificationService.m` or `NotificationService.swift` and replace the whole file contents with the below code.swift 



```swift tab="swift"
import UserNotifications

import Kontext

class NotificationService: UNNotificationServiceExtension {
    
    var contentHandler: ((UNNotificationContent) -> Void)?
    var receivedRequest: UNNotificationRequest!
    var bestAttemptContent: UNMutableNotificationContent?
    
    override func didReceive(_ request: UNNotificationRequest, withContentHandler contentHandler: @escaping (UNNotificationContent) -> Void) {
        self.receivedRequest = request;
        self.contentHandler = contentHandler
        bestAttemptContent = (request.content.mutableCopy() as? UNMutableNotificationContent)
        
        if let bestAttemptContent = bestAttemptContent {
            Kontext.didReceiveNotificationExtensionRequest(self.receivedRequest, with: self.bestAttemptContent)
            contentHandler(bestAttemptContent)
        }
    }
    
    override func serviceExtensionTimeWillExpire() {
        // Called just before the extension will be terminated by the system.
        // Use this as an opportunity to deliver your "best attempt" at modified content, otherwise the original push payload will be used.
        if let contentHandler = contentHandler, let bestAttemptContent =  bestAttemptContent {
            Kontext.serviceExtensionTimeWillExpireRequest(self.receivedRequest, with: self.bestAttemptContent)
            contentHandler(bestAttemptContent)
        }
    }
    
}
```

```objective-c tab="objective-c"
#import <Kontext/Kontext.h>

#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNNotificationRequest *receivedRequest;
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    self.receivedRequest = request;
    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];
    
    [Kontext didReceiveNotificationExtensionRequest:self.receivedRequest withMutableNotificationContent:self.bestAttemptContent];
    
    // DEBUGGING: Uncomment the 2 lines below and comment out the one above to ensure this extension is excuting
    //            Note, this extension only runs when mutable-content is set
    //            Setting an attachment or action buttons automatically adds this
    // NSLog(@"Running NotificationServiceExtension");
    // self.bestAttemptContent.body = [@"[Modified] " stringByAppendingString:self.bestAttemptContent.body];
    
    self.contentHandler(self.bestAttemptContent);
}

- (void)serviceExtensionTimeWillExpire {
    // Called just before the extension will be terminated by the system.
    // Use this as an opportunity to deliver your "best attempt" at modified content, otherwise the original push payload will be used.
    
    [Kontext serviceExtensionTimeWillExpireRequest:self.receivedRequest withMutableNotificationContent:self.bestAttemptContent];
    
    self.contentHandler(self.bestAttemptContent);
}

@end
```

*Ignore any build errors at this point, step 2 will import Kontext which will resolve any errors.*

### 8. Add App Groups (Optional but Recommended)

In order for your application to be able to let push notifications increment/decrement the badge count, you need to set up an **App Group** for your application.

### Callbacks

[KontextHandleNotificationReceivedBlock](/iOS/reference/#kontexthandlenotificationreceivedblock) - Called when a notification is received while your app is in focus only.
[KontextHandleNotificationActionBlock](/iOS/reference/#kontexthandlenotificationactionblock) - This will be called when a notification is tapped on.
See our [initWithLaunchOptions](/iOS/reference/#initwithlaunchoptions) documentation to add these.

!!! success "You're Done!"

    Next up: Send your first push notification via the [Kontext Dashboard](https://app.kontext.in)
