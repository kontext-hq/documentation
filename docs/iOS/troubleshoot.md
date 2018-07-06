

# Troubleshooting iOS

## Notification Display Issues

### Notifications are not shown at all when Action Buttons or Media Attachments are added

**The below 9 troubleshooting steps only applies to pre-2.4.0 versions of the iOS SDK or if the device is running iOS 8 or 9.**
In order for notifications with buttons to display the following must be true:

**1.** You can not force close the app by double tapping the home button and swiping away your app.

- This includes stopping your app from Xcode or disconnecting the device from your Mac after deploying. If you do this you must reopen your app then press the home button to background it.
- If this is the case you will see an entry in the device log in Xcode like the following.
- `apsd[83] <Warning>: Low Priority Push: com.kontext.example - App killed`

**2.** Go to `Settings` > `General` > `"Background App Refresh"` and make sure it is enable for both the device and your app.

**3.** Make sure "Remote notifications" are checked under Capabilities>Background Modes shown in [step 2. Add Required Capabilities](/iOS/quickstart). Note: This is automatic for some plugins like Cordova and Corona.

**4.** Remove any other push notifications SDKs from your app.

**5.** Development build - After disconnecting your device from your system after deploying the app directly from Xcode you will need to reopen your app so it isn't stuck in the forced close state.

**6.** The APNs send priority is lower on these types of notifications. Please allow a few minutes for these to be received.

**7.** If you continue to see delivery issues try sending a notification without these options set to confirm there are no networking issues with your iOS device.

**8.** If even if the above is ok there can still be a stuck network connect so we recommend toggling your network connection off then back on again.

**9.** If all else fails try uninstalling your app and rebooting the device.

### Notification is shown but media attachments are not displayed

**1.** Open your attachment URL in a web browser. Make sure it is a direct link to the image, it can't be part of an HTML page. Also redirects are not supported.

**2.** Make sure your URL is HTTPS. HTTP urls will not work unless you set `NSAppTransportSecurity` to `NSAllowsArbitraryLoads` in your Xcode `.plist`.

**3.** Make sure your url ends with the correct file extension. If the URL doesn't contain a file extension you can add it as a parameter by adding `?filetype=file.jpg` for example to the end of your URL.

**4.** If you are using our 2.4.0 native SDK please double check you have correctly added the NotificationServiceExtension noted in step 1 of the [iOS Setup guide](/iOS/quickstart).

**5.** If you correctly added the Kontext Notification Service Extension and rich push notifications (images, buttons) still don't appear, make sure that the **Deployment Target** in the Extension service matches the deployment target of your application.

### Notification is shown but action buttons are not displaying

**1.** If you are using our 2.4.0 native SDK please double check you have correctly added the NotificationServiceExtension noted in step 1 of the [iOS Setup guide](/iOS/quickstart).

## Debug the Notification Service Extension

**1.** Double check that you followed all setup instructions first, please see the SDK docs your are using for more on this.

**2.** The 2 debugging lines in the .m source we provide are 2 ways to confirm the notification service extension is running.

`self.bestAttemptContent.body = [@"[Modified] " stringByAppendingString:self.bestAttemptContent.body];`

This line will add "[Modified] " to the beginning of all your notification bodies. You should see this on all notifications on your device.

`NSLog(@"Running NotificationServiceExtension");`

This will add an entry to the device log when the extension is run. You can view this in Xcode under Window > "Devices and Simulators". Select your device on the left and open the log up arrow at the bottom.

We recommend clearing the log before sending a notification to test as it can grow quickly. Copy the log and search for the debug entry "Running NotificationServiceExtension".

We don't recommend trying to attach to the extension process with the debugger in Xcode through the Debug menu. Doing so can create issues with it launch so we recommend restarting your device if you have tried doing so.

Lastly the Notification Service Extension will only run if you have set our Action Buttons, a Media Attachment, or have set mutable content on the notification so make sure your test notification have one of these set.

------

## Swift : No such module 'Kontext'

**CocoaPods:** Pods written in Swift should be imported with the `use_frameworks!`, and CocoaPods will complain if you don't do this and try to import the pods in Swift code.

**Manual Import:** One way to solve your issue is to go into your build settings and defining the **Framework Search Paths** to a folder which contains the frameworks in question. If the Kontext framework is placed in your project directory, simply set the framework search path to $(SRCROOT) and set it to recursive.

------

## How to get a crash log from an iOS device

**NOTE:** For your crash to show in the following steps the crash must happen when your device is not connected to your Mac. Connect it after you reproduce the crash.

**1.** In Xcode go to `Window` > `Devices`.

**2.** Select your device on the left and press the "View Device Logs" button.

**3.** Sort by `Date/Time` to find your log.

**4.** Right click on the entry and select `Export Log`.

**5.** Send it to Kontext support along with details on reproducing the crash.

------

## Resetting the iOS Notification Permission Prompt

### iOS 9+

Permission is reset when the app is uninstalled.

### Pre-iOS 9

iOS prompts the user to allow displaying of notifications with a system prompt. Our SDK's default setting is to request permissions as soon as your app is opened. However, we recommend you delay the prompt by disabling `autoRegister` and calling register at a later point. *(See the SDK API that applies to your app for details)*

Delaying the prompt can get your app better opt-in rates if you prompt after they compete your tutorial. Since iOS remembers the answer to the notification permissions question even after a full reinstall it can be tricky to reset the prompt to test it again so we have written the following instructions below.

**Clear Notification Permission Answer**

1. Uninstall your app.
2. Reboot the device.
3. Set your system clock ahead 1 day.
   *(Do no set your clock over 1 week ahead as you may no longer receive pushes)*
4. Reboot the device again.
5. Reinstall your app and it will prompt you again.

**Quick way to test displaying of the prompt**

1. When you see the notification permission DO NOT answer it.
2. Power the device off.
3. After the device powers back on, fully uninstall then reinstall your app.

------

## Previous Push Notifications Disappear

### iOS 7+

Previous push notifications disappear when the user opens the app.

The Kontext SDK will automatically clear previously received push notifications when the app is opened under two conditions:

- The badge number is > 0
- The application was opened from a push notification

This behavior is caused by our system to clear the badge number. Most app developers want this behavior, however some do not. In order to prevent this from occurring, you can add `Kontext_disable_badge_clearing` = `false` in your application's `Info.plist`.



!!! info "Still facing issues? We'are happy to help"

```
We answer most support queries in under 4 hours during the week, and under 24 hours on weekends. Simply email us at [support@kontext.in](mailto:support@kontext.in)
	1. Version of our SDK
	2. Device OS version
	3. Xcode crash lock or stack trace of the app 		starting and the problem point
	4. Any other libraries or plugins in your app
	5. Details on reproducing your problem.
```