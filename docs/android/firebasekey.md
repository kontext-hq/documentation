

# Generate a Firebase Server Key

### Your **Firebase Server Key** and **Firebase Sender ID** are used to send push notifications to ANDROID devices.

To begin, we'll obtain a Firebase Server Key and Firebase Sender ID. These keys allow Kontext to use Google's web push services for your notifications.

## 1. Create a Firebase project

**1.1** Visit the [Firebase Console](https://firebase.google.com/) and sign in with your Google account.

![Screenshot](/assets/images/firebase-1.png)

**1.2** Press "CREATE NEW PROJECT" or select an existing one below.

![Screenshot](/assets/images/firebase-2.png)

**1.3** Enter a project name and press "CREATE PROJECT".

![Screenshot](/assets/images/firebase-3.png)

## 2. Getting your Firebase Cloud Messaging token and Sender ID

**2.1** Click the Gear icon in the top left and select "Project settings".

**2.2** Select the "CLOUD MESSAGING" tab.

**2.3** Save the two values listed:

- You'll need your **Server key** and **Sender ID**.

![Screenshot](/assets/images/firebase-4.png)

## 3. Configure your Kontext app's Android platform settings

**3.1** Go to Settings and paste your *Sender ID and FCM credentials*.

**3.2** Press Save to generate your app ID and key.

![Screenshot](/assets/images/firebase-5.png)

!!! success "Done!!!"

    You now have a key to send push notifications from your Android app.


