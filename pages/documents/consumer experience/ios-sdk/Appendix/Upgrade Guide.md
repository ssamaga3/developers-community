---
title: Upgrade Guide - iOS
Keywords:
level1: Documents
level2: Consumer Experience
level3: In-App Messaging SDK for iOS
level4: Appendix
order: 247
permalink: consumer-experience-ios-sdk-upgrade-guide.html
indicator: messaging
---

### Upgrading LPMessagingSDK to 3.0

This document contains guides on how to upgrade from various previous versions of the SDK to 3.0. Please review [this repository](https://github.com/LivePersonInc/Upgrade_examples_to_SDK3.0) for in depth sample app examples of these upgrades.

**IMPORTANT**: Upgrading to LPMessagingSDK 3.0, requiresswift 4.0.2 and Xcode 9.2

### Updating from 2.3 to 3.0

#### Step 1: Update Podfile

* Update LPMessagingSDK Pod

```ruby
target '<YourApplicatioName>' do
# Update change LPMessagingSDK Pod from:
	pod 'LPMessagingSDK','~> 2.3.0'
# To:
	  	pod 'LPMessagingSDK','~> 3.0.0'
end
```

#### Step 2: Update Pod

* Update Podfile

```sh
    $ pod update
```

#### Step 3: Clean Xcode Project

* Clean the app with `cmd + shift + k` and build the app with `cmd + b` .


#### Step 4: Replace Deprecated Methods

* **showConversation** method needs to be replaced:

Previous implementation:

```swift
LPMessagingSDK.instance.showConversation(self.conversationQuery!,
                                              authenticationCode: nil,
                                              containerViewController: nil)
```

New implementation for WindowMode:

```swift
// Create ConversationViewParams
let conversationViewParams = LPConversationViewParams(conversationQuery: self.conversationQuery!, containerViewController: nil, isViewOnly: false)
// Create AuthenticationParams
let authenticationParams = LPAuthenticationParams()
// Show Conversation
LPMessagingSDK.instance.showConversation(conversationViewParams, authenticationParams: authenticationParams)
```

New implementation for custom ViewController:

```swift
// Create ConversationViewParams
let conversationViewParams = LPConversationViewParams(conversationQuery: self.conversationQuery!, containerViewController: viewController, isViewOnly: false)
// Create AuthenticationParams
let authenticationParams = LPAuthenticationParams()
// Show Conversation
LPMessagingSDK.instance.showConversation(conversationViewParams, authenticationParams: authenticationParams)
```

* **reconnect** method needs to be replaced:

Previous implementation:

```swift
LPMessagingSDK.instance.reconnect(conversationQuery!, authenticationCode: "")
```

New implementation:

```swift
// Create Authentication Params
let authParams = LPAuthenticationParams()
// Show Conversation
LPMessagingSDK.instance.reconnect(self.conversationQuery!, authenticationParams: authParams
```  	

* **logout** method needs to be replaced:

Previous implementation:

```swift
LPMessagingSDK.instance.logout()
```

New implementation:

```swift
LPMessagingSDK.instance.logout(completion: {
	// Log - Success
	print("User:: logged out")
  	}) { (error) in
	// Log - Error
	print("User:: \(error.localizedDescription)")
}
```

##### New Configurations
* Structured Content:

```swift
// Enable Structured Content
config.enableStrucutredContent = true
// Set Structured Content Border Color
config.structuredContentBubbleBorderColor = UIColor.black
// Set Structured Content Bubble Border Width in Pixels
config.structuredContentBubbleBorderWidth = 1.5
```


#### Step 4 (Optional): Custom ViewController

When implementing a Custom ViewController there are a few things to consider:

 * Remove Conversation from View if viewWillDisappear()

```swift
/// Event - View will disappear
override func viewWillDisappear(_ animated: Bool) {
    // Super Init
    super.viewWillDisappear(animated)
    // INFO: When using Custom View Controller Mode, Conversation must be remove when leaving the App, if the Conversation View is the current screen
    // Check if ConversationQuery has been set
    if self.conversationQuery != nil {
        // Remove Conversation
        LPMessagingSDK.instance.removeConversation(self.conversationQuery!)
    }
}
```

**Note**: if implementing a custom Back Button on the Navigation Bar, this needs to be considered too.



### Updating from 2.7 to 3.0

#### Step 1: Update Podfile

  * Update LPMessagingSDK Pod

```ruby
target '<YourApplicatioName>' do
	# Update change LPMessagingSDK Pod from:
	   	pod 'LPMessagingSDK','~> 2.7.0'
 	  	# To:
 	  	pod 'LPMessagingSDK','~> 3.0.0'
end
```

#### Step 2: Update Pod

* Update Podfile

```sh
$ pod update
```

#### Step 3: Clean Xcode Project

* Clean the app with `cmd + shift + k` and build the app with `cmd + b` .


#### Step 4: Replace Deprecated Methods

* **logout** method needs to be replaced:

Previous implementation:

```swift
LPMessagingSDK.instance.logout()
```

New implementation:

```swift
LPMessagingSDK.instance.logout(completion: {
	// Log - Success
	print("User:: logged out")
  	}) { (error) in
	// Log - Error
	print("User:: \(error.localizedDescription)")
}
```

#### Step 4 (Optional): Custom ViewController

When implementing a Custom ViewController there are a few things to consider:

 * Remove Conversation from View if viewWillDisappear()

```swift
/// Event - View will disappear
override func viewWillDisappear(_ animated: Bool) {
    // Super Init
    super.viewWillDisappear(animated)
    // INFO: When using Custom View Controller Mode, Conversation must be remove when leaving the App, if the Conversation View is the current screen
    // Check if ConversationQuery has been set
    if self.conversationQuery != nil {
        // Remove Conversation
        LPMessagingSDK.instance.removeConversation(self.conversationQuery!)
    }
}
```

**Note**: if implementing a custom Back Button on the Navigation Bar, this needs to be considered too.



### Updating from 2.8 to 3.0

#### Step 1: Update Podfile

  * Update LPMessagingSDK Pod

```ruby
target '<YourApplicatioName>' do
	# Update change LPMessagingSDK Pod from:
	pod 'LPMessagingSDK','~> 2.8.0'
	# To:
	pod 'LPMessagingSDK','~> 3.0.0'
end
```

#### Step 2: Update Pod

* Update Podfile

```sh
    $ pod update
```

#### Step 3: Clean Xcode Project

* Clean the app with `cmd + shift + k` and build the app with `cmd + b` .
