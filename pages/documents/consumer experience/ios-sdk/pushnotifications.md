---
title: Notifications
Keywords:
level1: Documents
level2: Consumer Experience
level3: In-App Messaging SDK for iOS

order: 15
permalink: consumer-experience-ios-sdk-pushnotifications.html

indicator: messaging
---

Push and local notifications are a key factor that make the experience better for consumers - they never have to stay in your app or keep the window open as they will get a proactive notification as soon as a reply or notice is available.

Note: In order to enable push notifications, you must also configure them within the LiveEngage UI.  See instructions.

1. `public func handlePush(userInfo: [NSObject : AnyObject])`
2. `public func registerPushNotifications(token token: NSData, notificationDelegate: LPMessagingSDKNotificationDelegate? = nil, alternateBundleID: String? = nil)`  
3. `<LPMessagingSDKNotificationDelegate> optional func LPMessagingSDKNotification`
4. `(didReceivePushNotification notification: LPNotification)`
5. `<LPMessagingSDKNotificationDelegate>  optional func LPMessagingSDKNotification(shouldShowPushNotification notification: LPNotification) -> Bool`
6. `<LPMessagingSDKNotificationDelegate>   optional func LPMessagingSDKNotification(customLocalPushNotificationView notification: LPNotification) -> UIView`
7. `<LPMessagingSDKNotificationDelegate>   optional func LPMessagingSDKNotification(notificationTapped notification: LPNotification)`

### Configuring Push Notifications

Follow the instructions below to set up your certificate and key file to enable push notifications.

*Note: Before you begin the setup, you must ensure your LiveEngage account is configured and connected to the SDK.*

1. Enter your LiveEngage account through this [Login URL](https://authentication.liveperson.net/login.html?lpservice=liveEngage&servicepath=a%2F~~accountid~~%2F%23%2C~~ssokey~~){:target="_blank"}.

	You will need the following info from your LivePerson account team:

	* LiveEngage account number

	* User ID (must be an administrator user)

	* Password

2. Within LiveEngage, navigate to **Campaigns**, and click **Data Sources**.

![campaigns](img/campaigns.png)

{:start="3"}
3. Then select **Manage** under **Mobile App management**.

![app](img/mobieAppManagement.png)

{:start="4"}
4. Click **Add new** to associate your app with the LiveEngage account.

![keymanagement](img/keymanagement.png)

{:start="5"}
5. Select your platform as iOS, enter your app’s name, and then click **Create app**. Then, upload your app certificate and key file in the appropriate locations. For more information on your app certificate, please [click here](consumer-experience-ios-sdk-createcertificate.html){:target="_blank"}.

*Note: If you are using a development certificate you should uncheck the Production checkbox and add DEV postfix to the Mobile app name.For example, if your app Bundle ID is AppId, your mobile app name should be "AppId-Dev". If you are using a production certificate you should leave the production checkbox checked and insert to the Mobile App name your App Bundle ID as it is.*

*Note: there is a 50 character limit for your Bundle ID*

![newapp](img/newapp.png)

{:start="6"}
6. Click **Close** to complete the process.
