Gyant iOS SDK
==================

![Logo](https://gyant.com/wp-content/uploads/2018/10/Gyant.Logotype.HorizontalLeft@2x-1.png)

# About

GYANT combines messaging, AI, and medical experts to radically improve the diagnosis and treatment of non-urgent conditions. GYANT makes treatment faster, more effective & more delightful. Our purpose is to transform healthcare from the outside in — to create a new care standard for everyone.

# Requirements
 - iOS 10+
 - Xcode 10.2.1+

# Setup using CocoaPods 

Add Gyant repo:

```
pod repo add gyant-podspecs git@github.com:GYANTINC/gyant-podspecs.git
```

Add Gyant Specs source to your Podfile in the following order:

```
source 'git@github.com:GYANTINC/gyant-podspecs.git'
source 'https://github.com/CocoaPods/Specs.git'
```

**Make sure gyant-podspecs source is the first one**

Add GyantChatSDK pod to your app target.

```
pod 'GyantChatSDK', '~> 1.0.6'
```

Install the pod.

```
pod install
```

## Disable Bitcode

GyantChatSDK does not offer bitcode compatibility for now.

Make sure to disable bitcode in your build settings:

![Disable Bitcode](images/bitcode_off.png)

## Add NSLocationWhenInUseUsageDescription

Adding the NSLocationWhenInUseUsageDescription key in Info.plist is required to enable the app to access the user location. The user location is required in some user flows like Find a Clinic, etc.

![Add NSLocationWhenInUseUsageDescription](images/location_plist.png)

## Getting Started with Swift

1. Import the GyantChatSDK framework in the application delegate.

    ```swift
    import GyantChatSDK
    ```

2. Start the SDK by adding the following code snippet in the `application:didFinishLaunchingWithOptions:` application delegate method.

    ```swift
    GyantChat.start(withClientID: "<YOUR-CLIENT-ID>", patientID: "<YOUR-PATIENT-ID-OPTIONAL>", isDev: true, theme: nil)
    ```
    
    **Note**: The andIsDev parameter must be changed to false before submitting the app to production. 
        
3. Present the chat view by adding the following code snipped in any view controller.

    ```swift
    let chatVC = GyantChat.createChatViewController()!
    self.present(chatVC, animated: true, completion: nil)
    ```

## Getting Started with Objective-C

1. Import the GyantChatSDK framework in the application delegate.

    ```objective-c
    #import <GyantChatSDK/GyantChatSDK.h>
    ```

2. Start the SDK by adding the following code snippet in the `application:didFinishLaunchingWithOptions:` application delegate method.

    ```objective-c
    [GyantChat startWithClientID:@"<YOUR-CLIENT-ID>" patientID:@"<YOUR-PATIENT-ID-OPTIONAL>" isDev:YES theme:@{}];
    ```
    
    **Note**: The andIsDev parameter must be changed to false before submitting the app to production.
    
3. Present the chat view by adding the following code snipped.

    ```objetive-c
    UIViewController *chatVC = [GyantChat createChatViewController];
    [self presentViewController:chatVC animated:true completion:nil];
    ```

## Include the SDK for iOS in an Existing Application

The [samples](https://github.com/GYANTINC/gyant-ios-sdk-samples) included with the SDK for iOS are standalone projects that are already set up for you. You can also integrate the SDK for iOS with your own existing project.

## Theme Configuration

To allow a more seamless integration into existing apps the SDK supports custom themes. For each theme the following RGBA colours could be customized:
| Name            | Description                                                                                                                                                                                           | bot       | provider  |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|-----------|
|  primaryColor1  | - Background color - Auto-complete matches highlight text color - Hyperlink text color                                                                                                                | ff4cb9f7  | ff1f5075  |
| primaryColor2   | - Clinic and Provider cards text color                                                                                                                                                                | ff3ea9f5  | ff3ea9f5  |
| primaryColor3   | n/a                                                                                                                                                                                                   |           |           |
| primaryColor4   | - QuickResponses bubble background color - Input box background color - User bubble background color                                                                                                  | ff79c7ff  | ff296a9c  |
| secondaryColor1 | - Auto-complete list background color - Connecting indicator background color - Scroll to bottom button icon color - Send button enabled icon color - Input box cursor color - Undo button icon color | ffffffff  | ffffffff  |
| secondaryColor2 | - Success notification background color                                                                                                                                                               | ff4cd964  | ff4cd964  |
| secondaryColor3 | - Error notification background color                                                                                                                                                                 | fff55040  | fff55040  |
| secondaryColor4 | - Provider bubble background color                                                                                                                                                                    | ffff79c7  |  ff62849e |
| extraColor1     | - Card title text color - Connecting indicator text color - Auto-complete non-matches text color                                                                                                      | ff13324a  | ff0f77c6  |
| extraColor2     | - Card subtitle text color                                                                                                                                                                            |  ff767676 | ff767676  |
| extraColor3     | - Send button disabled icon color                                                                                                                                                                     | ffaaaaaa  | ffaaaaaa  |
| extraColor4     | n/a                                                                                                                                                                                                   |           |           |
| extraColor5     | - Scroll to bottom button background color - Send button background color                                                                                                                             | ff13324a  | ff13324a  |


**Copyright © 2019 GYANT.com, Inc. All rights reserved.**
