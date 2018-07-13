# Generate an iOS Push Certificate

Required for all iOS apps.

The goals of this section are to provision your app with Apple and grant Kontext access to manage your notifications.

### Required For Setup

- [A Kontext Account](https://kontext.in/) if you do not already have one
- Your Kontext App Auth Key, available in [Keys & IDs](https://documentation.kontext.in/docs/accounts-and-keys#section-keys-ids)
- A Mac with Xcode 8+. 

### 1. Create Certificate Request Manually

**1.1** Open Keychain Access on your Mac OS X system. It may be located in "Applications" > "Utilities" > "Keychain Access"

**1.2** Select "Keychain Access">"Certificate Assistant">"Request a Certificate From a Certificate Authority..."

![Screenshot](/assets/images/ios-1.png)

**1.3** Select the "Save to disk" option and enter your information in the required fields. This creates a certification request file that will be used later.

![Screenshot](/assets/images/ios-2.png)

### 2. Enable Push Notifications and apply the Certification Request to generate Certificate

**2.1** Select your app from the [Apple's Developer site](https://developer.apple.com/account/ios/identifier/bundle) and press "Edit"

![Screenshot](/assets/images/ios-3.png)

**2.2** Scroll down to the bottom and enable Push Notifications. Press Done, but do not configure either Production or Development certificate.

Instead, go to [Add iOS Certificate](https://developer.apple.com/account/ios/certificate/create) and select "**Apple Push Notification service SSL (Sandbox & Production)**" and click Continue.

This certificate will be applicable to both Sandbox and Production environments, so you do not need a separate key for each one.

![Screenshot](/assets/images/ios-4.png)

**2.3** Choose an App ID from the App ID pop-up menu, and click Continue.

**2.4** Press Continue

**2.5** Press "Choose File..", select the "certSigningRequest" file you saved in step 1, press open, and then press "Generate".

![Screenshot](/assets/images/ios-5.png)

**2.6** Press Download to save your certificate

![Screenshot](/assets/images/ios-6.png)

### 3. Creating a Private Key

**3.1** Open the .cer file you downloaded in the last step by double clicking on it in Finder.

![Screenshot](/assets/images/ios-7.png)

**3.2** After a few seconds the "Keychain Access" program should pop up. Select Login > My Certificates then right click on your key in the list and select "Export"

![Screenshot](/assets/images/ios-8.png)

**3.3** Give the file a unique name using the `.p12` extension, and press save. You will have an option to protect the file with a password. If you add a password, you need to enter this same password on Kontext.

### 4. Upload Your Push Certificate to Kontext

If you haven't already, you should [set up your Kontext account](https://kontext.in/).

**4.1** Select your app from the All Apps page in Kontext, then go to "App Settings" and press Configure to the right of the Apple iOS Settings.

![Screenshot](/assets/images/ios-9.png)

**4.2** Select the .p12 you exported along with a password if you added one and press Save.

![Screenshot](/assets/images/ios-10.png)



!!! warning "Troubleshooting"

    If you are running into any issues you can try troubleshooting them with our [iOS Troubleshooting](/iOS/troubleshoot)

