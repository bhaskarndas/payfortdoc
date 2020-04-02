## Integrate iOS SDK

------

To process a transaction using the FORT Mobile SDK, create a Mobile SDK Token and proceed through the following sections.



### About the Software

------



#### Supported Platforms

IOS 8+

#### Localization

The FORT Mobile SDK supports both English and Arabic languages.

#### Screen Orientation

Portrait is the only orientation supported within the FORT Mobile SDK.

#### Supported Payment Methods

Through the first version of the FORT Mobile SDK, the Merchant has the ability to process a **CREDIT CARD** transactions only.

#### Supported Payment Options

The supported credit card payment options are **VISA**, **MASTERCARD**, **American Express (AMEX)**, **MADA** and **MEEZA**.

### Include the SDK to your Xcode Project

------



1. [Download](https://docs.payfort.com/docs/api/build/lib/PayFortSDK2.1.zip) and extract sdk.
2. Drag the PayFortSDK.framework & PayFortSDK.bundle to Frameworks in Project Navigator.
3. Create a new group Frameworks if it does not exist:
   - Choose Create groups for any added folders.
   - Make Sure to select Copy files if needed.
4. Set -ObjC in the Other Linker Flags in the Target → Build Settings Tab.
5. For Swift Projects Don’t forget to add the **#import** to the **Bridging-Header.h**

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>
    Ensure linked once in the Linked Framework and Libraries or just drag the PayFortSDK.framework to Embedded Binaries in the general tab in the project settings.
</div>



<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>In Xcode, secondary-click your project’s .plist file and select Open As → Source Code. Insert the following XML snippet into the body of your file just before the final, same as below:</div>

```xml
</dict>element
<key>NSAppTransportSecurity</key>
<dict>
<key>NSAllowsArbitraryLoads</key><true/>
</dict>
```



<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>To make the application not disconnected when go to background make sure to add this code:</div>

 

**Objective C**

```objective-c
(void)applicationDidEnterBackground:(UIApplication *)application {
__block UIBackgroundTaskIdentifier backgroundTask; backgroundTask =
[application beginBackgroundTaskWithExpirationHandler: ^ {
[application endBackgroundTask:backgroundTask];
backgroundTask = UIBackgroundTaskInvalid; }];
```





**Swift**



```swift
func applicationDidEnterBackground(_ application: UIApplication) {
var bgTask: UIBackgroundTaskIdentifier = 0
bgTask = application.beginBackgroundTask(expirationHandler: {
application.endBackgroundTask(bgTask)
bgTask = UIBackgroundTaskInvalid
})
}
```



### Installation

1. Import the PayFort Library.

   `#import <PayFortSDK/PayFortSDK.h>`

   

2. Initialize PayFortConrtoller with targeted environment, You set the target environment by setting one the two ENUM *KPayFortEnviromentSandBox* or *KPayFortEnviromentProduction*.

  **Objective C**
```objective-c
PayFortController *payFort = [[PayFortControlleralloc]initWithEnviroment:KPayFortEnviromentSandBox];
```


**Swift**
```swift
let payFort = PayFortController.init(enviroment: KPayFortEnviromentSandBox)
```

   

3. Set Dictionary contain all keys and values for SDK.

   **Objective C**

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

4. Call PayFort and Response callback

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
### SDK - Response

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



### Hidden PayFort loading

There is an option to hide loading view when SDK initialize the connection request. By disable the following option:

**Objective C**

```objective-c
PayFort.HideLoading = YES;
```



**Swift**

```swift
PayFort.HideLoading = true;
```



### Custom Payment Designing

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

