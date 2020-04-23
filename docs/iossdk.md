![PayFort SDK Integration with Swift](img\Payfort iOS integration with Swift Project.png)

image source : [medium.com](https://medium.com/@yoloabdo/payfort-ios-sdk-integration-with-swift-afe04f83330)

## Integrate iOS SDK

------

The PayFort iOS SDK makes it faster and easy to build a perfect payment experience in your iOS app. PayFort offers powerful and customizable UI screens and elements that can be used out-of-the-box to collect your users’ payment details. We also expose the low-level APIs that power those UIs so that you can build fully custom experiences.

### About the Software

------

#### Supported Platforms

PayFort iOS SDK is supported on all the apple devices running iOS 8 and above.

#### Localization

The FORT Mobile SDK supports both English and Arabic languages.

#### Screen Orientation

Portrait is the only orientation supported within the FORT Mobile SDK.

#### Supported Payment Methods

Through the first version of the FORT Mobile SDK, the Merchant has the ability to process a **CREDIT CARD** transactions only.

#### Supported Payment Options

The supported credit card payment options are **VISA**, **MASTERCARD**, **American Express (AMEX)**, **MADA** and **MEEZA**.

------

## MobileSDK integration workflow

------

![PayFort SDK integration workflow](https://miro.medium.com/max/1400/1*OG4TDHhIhARVIP_lQmGSUw.png)

image source : [medium.com](https://medium.com/@yoloabdo/payfort-ios-sdk-integration-with-swift-afe04f83330)

### Include the SDK to your Xcode Project

------

- Download the sdk from this [link](https://docs.payfort.com/docs/api/build/lib/PayFortSDK2.1.zip) and extract it.
- Drag the PayFortSDK.framework & PayFortSDK.bundle to Frameworks in Project Navigator.
- Create a new group Frameworks if it does not exist:
  - Choose Create groups for any added folders.
  - Make Sure to select Copy files if needed.

![PayFORT iOS sdk project setup](img\iosdk1.JPG)

- Set -ObjC in the Other Linker Flags in the Target → Build Settings Tab.

- For Swift Projects add the following code In your Bridge-Header.h:

```swift
  #import <PayFortSDK/PayFortSDK.h>
```

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>
    Ensure the option 'Link With Standard Libraries' is set to Yes or just drag the PayFortSDK to Embedded Binaries in the general tab in the project settings.
</div>
<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>In Xcode, click your project’s .plist file and select Open As → Source Code. Insert the following XML snippet into the body of your file just before the final:



```xml
</dict>element
<key>NSAppTransportSecurity</key>
<dict>
<key>NSAllowsArbitraryLoads</key><true/>
</dict>
```

</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>To ensure that the application is not disconnected go to background make sure to add this code:
Objective C


```
(void)applicationDidEnterBackground:(UIApplication *)application {
__block UIBackgroundTaskIdentifier backgroundTask; backgroundTask =
[application beginBackgroundTaskWithExpirationHandler: ^ {
[application endBackgroundTask:backgroundTask];
backgroundTask = UIBackgroundTaskInvalid; }];
```

Swift

```swift
func applicationDidEnterBackground(_ application: UIApplication) {
var bgTask: UIBackgroundTaskIdentifier = 0
bgTask = application.beginBackgroundTask(expirationHandler: {
application.endBackgroundTask(bgTask)
bgTask = UIBackgroundTaskInvalid
})
}
```

</div>

------

### Installation

When you register for Payfort, you will receive separate keys for testing and production environment. 

- Import the PayFort Library. `#import <PayFortSDK/PayFortSDK.h>`

- Initialize PayFortController with targeted environment, You set the target environment by setting one the two ENUM *KPayFortEnviromentSandBox* or *KPayFortEnviromentProduction*.

    - **Objective C**

    

         - ```
         PayFortController *payFort =      [[PayFortControlleralloc]initWithEnviroment:KPayFortEnviromentSandBox];
    ```
    
    
    
    
    - **Swift**

        - ```
        let payFort = PayFortController.init(enviroment: KPayFortEnviromentSandBox)
    ```
    

   

- Set Dictionary contain all keys and values for SDK.
- **Objective C**

```objective-c
NSMutableDictionary *request = [[NSMutableDictionary alloc]init];
[request setValue:@“10000” forKey:@“amount”];
[request setValue:@“AUTHORIZATION” forKey:@“command”];
[request setValue:@“USD” forKey:@“currency”];
[request setValue:@ “email@domain.com” forKey:@“customer_email”];
[request setValue:@“en” forKey:@“language”];
[request setValue:@“112233682686” forKey:@“merchant_reference”];
[request setValue:`SDK TOKEN GOES HERE` forKey:@“sdk_token”];
[request setValue:@“” forKey:@“payment_option”];
[request setValue:@“gr66zzwW9” forKey:@“token_name"];
```

**Swift**

```swift
let request = NSMutableDictionary.init()
request.setValue(“1000”, forKey: “amount”)
request.setValue(“AUTHORIZATION”, forKey: “command”)
request.setValue(“USD”, forKey: “currency”)
request.setValue(“email@domain.com”, forKey: “customer_email”)
request.setValue(“en”, forKey: “language”)
request.setValue(“112233682686”, forKey: “merchant_reference”)
request.setValue(“token” , forKey: “sdk_token”)
```

- Call PayFort and Response callback

**Objective C**

```objective-c
[payFort callPayFortWithRequest:request currentViewController:self
Success:^(NSDictionary *requestDic, NSDictionary *responeDic) {
NSLog(@“Success”);
NSLog(@“responeDic=%@”,responeDic);
}
Canceled:^(NSDictionary *requestDic, NSDictionary *responeDic) {
NSLog(@“Canceled”);
NSLog(@“responeDic=%@”,responeDic);
}
Faild:^(NSDictionary *requestDic, NSDictionary *responeDic, NSString *message) {
NSLog(@“Faild”);
NSLog(@“responeDic=%@”,responeDic);
}];
```

**Swift**

```swift
PayFort.callPayFort(withRequest: request, currentViewController: self,
success: { (requestDic, responeDic) in
print(“success”)
},
canceled: { (requestDic, responeDic) in
print(“canceled”)
},
faild: { (requestDic, responeDic, message) in
print(“faild”)
})
```

------

### SDK - Response

------

By default the response will be dictionary to show the sent data in addition to the status, response message and response code.
The response will be ready in the registered call back handler with success, failed and cancelled. You can view the response by log the result as the followings:

**Objective C**

```objective-c
[payFort callPayFortWithRequest:request currentViewController:self
Success:^(NSDictionary *requestDic, NSDictionary *responeDic) {
NSLog(@“Success”);
NSLog(@“requestDic=%@”,requestDic);
NSLog(@“responeDic=%@”,responeDic);
}
Canceled:^(NSDictionary *requestDic, NSDictionary *responeDic) {
NSLog(@“Canceled”);
NSLog(@“requestDic=%@”,requestDic);
NSLog(@“responeDic=%@”,responeDic);

}
Faild:^(NSDictionary *requestDic, NSDictionary *responeDic, NSString *message) {
NSLog(@“Faild”);
NSLog(@“requestDic=%@”,requestDic);
NSLog(@“responeDic=%@”,responeDic);
NSLog(@“message=%@”,message);

}];
```



**Swift**

```swift
PayFort.callPayFort(withRequest: request, currentViewController: self,
success: { (requestDic, responeDic) in
print(“success”)
print(“responeDic=(responeDic)”)
print(“responeDic=(responeDic)”)
},
canceled: { (requestDic, responeDic) in
print(“canceled”)
print(“requestDic=(requestDic)”)
print(“responeDic=(responeDic)”)
},
faild: { (requestDic, responeDic, message) in
print(“faild”)
print(“requestDic=(requestDic)”)
print(“responeDic=(responeDic)”)
print(“message=(message)”)
})
```



Also there is an option to show response view directly in elegant view that show response results either its success or failed. By activating the following option:

**Objective C**

```objective-c
PayFort.IsShowResponsePage = YES;
```



**Swift**

```swift
PayFort.IsShowResponsePage = true;
```

------



### Hidden PayFort loading

------

There is an option to hide loading view when SDK initialize the connection request. By disable the following option:

**Objective C**

```objective-c
PayFort.HideLoading = YES;
```



**Swift**

```swift
PayFort.HideLoading = true;
```

------



### Custom Payment Designing

------

You have the option to provide your custom UI theme for the payment view by the followings:

- Create your nibFile .xib and set the name of Arabic xib same name with English one with suffix -ar.
- Link the xib with PayFortView and bind all the IBOutlets in interface section

```
IBOutlet UILabel *titleLbl;
IBOutlet UIButton *BackBtn;
IBOutlet UILabel *PriceLbl;
IBOutlet JVFloatLabeledTextField *CardNameTxt;
IBOutlet JVFloatLabeledTextField *CardNumberTxt;
IBOutlet JVFloatLabeledTextField *CVCNumberTxt;
IBOutlet JVFloatLabeledTextField *ExpDateTxt;
IBOutlet UILabel *cardNumberErrorlbl;
IBOutlet UILabel *cVCNumberErrorlbl;
IBOutlet UILabel *expDateErrorlbl;
IBOutlet UISwitch *savedCardSwitch;
IBOutlet UIButton *paymentBtn;
IBOutlet UILabel *saveCardLbl;
IBOutlet UIImageView *imageCard;
```



- Assign new created xib file to PayFort Controller.

  ```
  [payFort setPayFortCustomViewNib:@“PayFortView2”];
  ```

  

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>If you call Arabic view and the Arabic view not existed the application will crash.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Don’t forget to set the custom view field in the identity inspector.</div>

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

