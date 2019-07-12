Gyant iOS SDK
==================

![Logo](https://gyant.com/wp-content/uploads/2018/10/Gyant.Logotype.HorizontalLeft@2x-1.png)

# About

GYANT combines messaging, AI, and medical experts to radically improve the diagnosis and treatment of non-urgent conditions. GYANT makes treatment faster, more effective & more delightful. Our purpose is to transform healthcare from the outside in — to create a new care standard for everyone.

# Requirements
 - iOS 10+
 - Xcode 10.2.1+

# Setup using CocoaPods 

Add Gyant Specs source to your Podfile in the following order:

```
source 'git@github.com:GYANTINC/gyant-podspecs.git'
source 'https://github.com/CocoaPods/Specs.git'
```

**Make sure gyant-podspecs source is the first one**

Add GyantChatSDK pod to your app target.

```
pod 'GyantChatSDK'
```

Install the pod.

```
pod install
```

**Note** GyantChatSDK is a device-only framework.

## Development Builds

GyantChatSDK is a device only framework. To enable developers to test their integration in the simulator a custom pod is available where x86_64 arch is included. Note that for production builds you should never use this version. The following Podfile changes will integrate the dev version only for the Debug configuration while keeping the production version for the Release configuration.

Add GyantChatSDK pod to your app target.

```
pod 'GyantChatSDK-dev', :configurations => ['Debug']
pod 'GyantChatSDK', :configurations => ['Release']
```

Install both pods.

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
    GyantChat.start(withClientID: "<YOUR-CLIENT-ID>", andPatientID: "<YOUR-PATIENT-ID-OPTIONAL>", andIsDev: true)
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
    [GyantChat startWithClientID:@"<YOUR-CLIENT-ID>" andPatientID:@"<YOUR-PATIENT-ID-OPTIONAL>" andIsDev:YES];
    ```
    
    **Note**: The andIsDev parameter must be changed to false before submitting the app to production.
    
3. Present the chat view by adding the following code snipped.

    ```objetive-c
    UIViewController *chatVC = [GyantChat createChatViewController];
    [self presentViewController:chatVC animated:true completion:nil];
    ```

## Include the SDK for iOS in an Existing Application

The [samples](https://github.com/GYANTINC/gyant-ios-sdk-samples) included with the SDK for iOS are standalone projects that are already set up for you. You can also integrate the SDK for iOS with your own existing project.


**Copyright © 2019 GYANT.com, Inc. All rights reserved.**
