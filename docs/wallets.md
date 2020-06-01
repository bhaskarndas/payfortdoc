PayFort supports MasterPass, Visacheckout and ApplePay.

------

# MasterPass

------

As another move towards a cashless environment, PayFort provides **MasterPass**. It is a digital wallet that securely stores your buyer’s credit card details and shipping addresses, making shopping through thousands of online Merchants simple and convenient. This is fulfilled by enhancing and simplifying the buyer’s digital shopping experience.

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>PAYFORT now supports MasterPass Redirect v7 in addition to v6.</div>

------

## Service Endpoints

------

**Sandbox**

```http
POST  https://sbcheckout.payfort.com/FortAPI/paymentPage
```

**Live**

```http
POST  https://checkout.payfort.com/FortAPI/paymentPage
```

------

## Redirection

------



### Integration Flow

------

1. You submit a form that includes all the parameters and call the following url to be redirected to PayFort as mentioned in the service endpoints[&nbsp;&nbsp;<i class="fa fa-anchor"></i>](#service-endpoints)

2. The PayFORT returns a response to the request which you sent in step 1.

3. The payFORT inserts the response parameters into a JavaScript.

4. A lightbox appears to the buyer where he enters his credentials, selects the card type and the shipping address, and clicks “Finish Shopping”.

5. The payFORT either proceeds to Authorize or Purchase the payment based on the value of the command parameter sent in your request form.

6. The payFORT returns a response to the request sent to it in step5.(Please refer to section MasterPass Service - Response for the Response Parameters).

   <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>In the Redirection work flow, the “Channel” will always be considered redirection and the “Default Operation” won’t be considered.</div>

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>If you sent the “payment_option” value in your request, the payFORT will use the value found in the request, no matter what other options are supported by the Merchant. However, if this value wasn’t sent in the request, the payFORT will retrieve all the payment options supported by the Merchant.</div>

------

### Parameters Submission Type

HTTPs Form Post Request.

------

### Service Request Example

Below is the sample html request.

```html
placeholder: add code for request
```

The following is an example for “cart_details” parameter:

```html
placeholder: add code for card_details parameter
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

### MasterPass Hosted

------

Masterpass Hosted accepts digital wallet transactions without redirection to Masterpass pages, instead it will be hosted on the Merchant website.



# VisaCheckout

------

**Visa Checkout** is a digital wallet that securely stores the customer's credit card details and shipping addresses and information, making shopping through thousands of online Merchants simple and convenient. This service enhances and simplifies the buyer’s online shopping experience. **Visa Checkout** can be offered through two different integrations:

- [Merchant Hosted Checkout Button.](#merchant-hosted-checkout-button)
- [PayFort Hosted Checkout Button.](#payfort-hosted-checkout-button)

------

### Merchant Hosted Checkout Button

#### Integration Flow

------

This integration allows the you to host Visa Checkout button on your website giving you maximum control over the look and feel and user experience. The following steps describe how this integration works:

- You should include the following JavaScript in the HTML header of its checkout page. This JavaScript loads the Visa Checkout library and defines handlers to initialization and payment events.

```html
<head>
<script type="text/javascript">
function onVisaCheckoutReady() {
V.init({
apikey : “#API_KEY#”, // This will be provided by PayFort
		externalProfileId : “#PROFILE_NAME#”, // This will be provided by PayFort
		settings : {
		locale : “en_AE”,
		countryCode : “AE”, // depends on ISO-3166-1 alpha-2 standard codes
		review : {
		message : “Merchant defined message”, //
		buttonAction : “Continue” // The button label
		},
		threeDSSetup : {
		threeDSActive : “false” // true to enable the 3ds false to disable it
		}
		},
		paymentRequest : {
		currencyCode : “USD”, //depends on ISO 4217 standard alpha-3 code values
		subtotal : “10.00”, // Subtotal of the payment.
		}
		});
		V.on(“payment.success”, function(payment) {
		document.write(JSON.stringify(payment)); //response when received success operation
		});
		V.on(“payment.cancel”, function(payment) {
		document.write(JSON.stringify(payment)); //response when cancel operation
		});
		V.on(“payment.error”, function(payment, error) {
		document.write(JSON.stringify(payment));//response when received error operation
		document.write(error);
		});
		}
		</script>
		</head>
```



- You should use the following class to render Visa Checkout button that a consumer clicks to initiate a payment.

```html
<body>
<img alt=“Visa Checkout” class=“v-button” role=“button”
src=“https://sandbox.secure.checkout.visa.com/wallet-services-web/xo/button.png?cardBrands=VISA,MASTERCARD” />
</body>
```

##### Endpoints

------

**Sandbox**

```http
https://sandbox.secure.checkout.visa.com/wallet-services-web/xo/button.png
```

**Live**

```http
https://secure.checkout.visa.com/wallet-services-web/xo/button.png
```



- You should use the following JavaScript to control the operation on Visa Checkout on the website.

```html
  <body>
  <script type=“text/javascript”
  src=“https://sandbox-assets.secure.checkout.visa.com/checkout-widget/resources/js/integration/v1/sdk.js”>
  </script>
  </body>
```

  

- After completing the previous steps, the consumer clicks on Visa Checkout button, Visa Checkout light box appears and the user complete the checkout process.
- You will receive a successful response. The response associated with the payment success event returns list of parameters. The Merchant has to collect the value of “call_id” parameter to be used in the following step.
- You submit Purchase request to the FORT adding 2 extra parameters: digital-wallet, call_id. Please refer to Merchant Hosted Visa Checkout - Request for more details.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Merchants Page should be activated to accept Purchase and Authorization transactions</div>
- The Merchant system receives the FORT’s purchase request and then uses Visa Checkout update image pixel. Below you can find an example of how to use Visa Checkout update image pixel. Please refer to “Visa checkout PayFort documentation” for more details.

```html
  <img src=“https://sandbox.secure.checkout.visa.com/wallet-services-web/payment/updatepaymentinfo.gif?apikey=…&callId=…&currencyCode=USD&total=11.00&subtotal=11.00” />
```

The following example shows an HTML web page that loads the Visa Checkout library, defines handlers for initialization and payment events, and creates a Visa Checkout button:
```html
<html>

<head>
<script type=“text/javascript”>
function onVisaCheckoutReady() {
V.init({
apikey : “#API_KEY#”, // This will be provided by PayFort
externalProfileId : “#PROFILE_NAME#”, // This will be provided by PayFort
settings : {
locale : “en_AE”,
countryCode : “AE”, // depends on ISO-3166-1 alpha-2 standard codes
review : {
message : “Merchant defined message”, //
buttonAction : “Continue” // The button label
},
threeDSSetup : {
threeDSActive : “false” // true to enable the 3ds false to disable it
}
},
paymentRequest : {
currencyCode : “USD”, //depends on ISO 4217 standard alpha-3 code values
subtotal : “10.00”, // Subtotal of the payment.
}
});
V.on(“payment.success”, function(payment) {
document.write(JSON.stringify(payment)); // response when received success operation
});
V.on(“payment.cancel”, function(payment) {
document.write(JSON.stringify(payment)); // response when cancel operation
});
V.on(“payment.error”, function(payment, error) {
document.write(JSON.stringify(payment));// response when received error operation
document.write(error);
});
}
</script>
</head>

<body>
<img alt=“Visa Checkout” class=“v-button” role=“button"src="https://sandbox.secure.checkout.visa.com/wallet-services-web/xo/button.png?cardBrands=VISA,MASTERCARD,DISCOVER,AMEX” />

<script type=“text/javascript” src=“https://sandbox-assets.secure.checkout.visa.com/checkout-widget/resources/js/integration/v1/sdk.js”>
</script>

</body>
</html>


```

------

# Apple Pay

------

Start seamlessly accepting credit card payments from your customers via Touch ID and Face ID, eliminating the need for them to manually type in their card and shipping details.

When using a credit or debit card with Apple Pay, the actual card numbers are not stored on the device, or on Apple servers. Instead, a unique Device Account Number is assigned, encrypted and securely stored in the Secure Element on your device, where each transaction is authorized with a one-time unique dynamic security code.



------

### SUPPORTED DEVICES

Refer to Apple’s [compatibility documentation](https://support.apple.com/en-us/KM207105) to learn which devices support Apple Pay.

PayFort users can accept [Apple Pay](https://stripe.com/apple-pay) in iOS applications in iOS 8.1 and above. There are no additional fees to process Apple Pay payments, and the [pricing](https://www.payfort.com/pricing/) is the same as other card transactions.

Apple Pay is compatible with most PayFort products and features, allowing you to use it in place of a traditional payment form whenever possible. Use it to accept payments for physical or digital goods, donations, subscriptions, and more.

Apple Pay is available to cardholders at participating banks in supported countries. Refer to Apple’s [participating banks](https://support.apple.com/en-us/ht204916) documentation to learn which banks and countries are supported.

------

## Endpoints

**Sandbox**

```http
POST  https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

**Live**

```http
POST  https://paymentservices.payfort.com/FortAPI/paymentApi
```

------

#  Before you start

Before you get started with Apple Pay, you will need the following:

- An Apple Developer account. [Sign up for one here](https://developer.apple.com/programs/enroll/) and complete the Apple Pay certification (export the payment processing certificate in p12 file)
- A domain with a valid SSL certificate (meaning your domain should start with `https`).
- Access to a Secure Shell (SSH) terminal.
- Access to your server's files, so you can upload files to your server.
- Integrate Apple Pay in your app/website using the Apple Pay documentation found at https://developer.apple.com/apple-pay
- Submit the encrypted Apple Pay payload to PayFort’s API for decryption / processing. Please contact [integration@payfort.com](mailto:integration@payfort.com) for PayFort’s integration documentation





## Configure Apple Pay

------

1. Create your merchant IDs in your Apple Pay Developer account

   Placeholder: Sample video showing how to create merchant Ids in Apple Pay Developer account.

   <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>We recommend that you create separate merchant IDs for your test environment and for your live/production environment.</div>

2. Integrate Apple Pay in your app/website using the Apple Pay documentation found at https://developer.apple.com/apple-pay

3. Submit the encrypted Apple Pay payload to PayFort’s API for decryption / processing. Please contact [integration@payfort.com](mailto:integration@payfort.com) for PayFort’s integration documentation

------

### Parameters Submission Type

REST POST request using JSON.

------

## The ApplePay Request

------

Placeholder: Insert sample request code for apple pay



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>
------

## The ApplePay Response

Here is the sample response

Placeholder: Please insert sample response for Apple Pay Service as sent by PayFORT server.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

## Apple Pay SDK Service

------

Apple Pay is a digital wallet that allows your customers to make payments using different Apple devices via FORT iOS SDK. The Customer authenticate his identity with Touch ID fingerprint verification to complete the payment.

------



### Before You Start

------

• You will need one of these iOS devices (iPhone 6, iPhone 6s, iPhone 6 Plus, iPhone 6s Plus, iPhone 7, iPhone 7 Plus, iPhone SE, iPad Air 2, iPad mini 3, iPad mini 4, and iPad Pro models) running iOS 8.1 or later.

• You will need a Mac with Xcode 6.1 or newer installed. You can install or upgrade Xcode in the [Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835).

• You will also need an apple developer account and a membership in the iOS Developer Program. You can create a one from [here](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=891bd3417a7776362562d2197f89480a8547b108fd934911bcbea0110d07f757&path=%2Fregister%2Fagree%2F&rv=1).

• You will need to download the FORT iOS Mobile SDK, click [here](https://docs.payfort.com/docs/mobile-sdk/build/lib/PayFortSDK2.1.zip).

------



### Get Started

Before you start Apple Pay integration with PayFort please refer to the following URL [here](https://developer.apple.com/apple-pay/get-started/) to complete the following steps:

1. Setup your Apple Pay account.

2. Complete the integration with Apple Pay SDK.

3. After completing the integration with Apple Pay, check that you have got the following:
     • Apple merchantID.
     • Merchant certificate.
     • Payment processing certificate.
   Then copy the following sample code to complete integration with FORT Mobile SDK:

   **Object-C code for Integration with PayFORT iOS SDK**

   ```objective-c
   #pragma mark - PKPaymentAuthorizationViewControllerDelegate
   
   (void)paymentAuthorizationViewController:
   (PKPaymentAuthorizationViewController *)controller
   didAuthorizePayment:(PKPayment *)payment
   completion:(void (^)(PKPaymentAuthorizationStatus status))completion
   {
   BOOL asyncSuccessful = payment.token.paymentData.length != 0;
   
   if(asyncSuccessful) {
   
   PayFortController *payFort = [[PayFortController alloc]initWithEnviroment:(KPayFortEnviroment)_enviromentSegment.selectedSegmentIndex];
   
   NSMutableDictionary *request = [[NSMutableDictionary alloc]init];
   [request setValue:@“10000” forKey:@“amount”];
   [request setValue:@“AUTHORIZATION” forKey:@“command”];
   [request setValue:@“USD” forKey:@“currency”];
   [request setValue:@“email@domain.com” forKey:@“customer_email”];
   [request setValue:@“en” forKey:@“language”];
   [request setValue:@“merchant” forKey:@“merchant_reference”];
   [request setValue:@“” forKey:@“sdk_token”];
   [request setValue:@“APPLE_PAY” forKey:@“digital_wallet”];
   
   [payFort callPayFortForApplePayWithRequest:request
   applePayPayment:payment
   currentViewController:self
   Success:^(NSDictionary *requestDic, NSDictionary *responeDic) {
   completion(PKPaymentAuthorizationStatusSuccess);
   
   }
   Faild:^(NSDictionary *requestDic, NSDictionary *responeDic, NSString *message) {
   completion(PKPaymentAuthorizationStatusFailure);
   
   }];
   } else {
   completion(PKPaymentAuthorizationStatusFailure);
   }
   }
   ```



**Swift Code for Integration with PayFORT iOS SDK**

```swift
func paymentAuthorizationController(_ controller: PKPaymentAuthorizationController,
didAuthorizePayment payment: PKPayment, completion: @escaping (PKPaymentAuthorizationStatus) -> Void) {

//Perform some very basic validation on the provided contact information
let asyncSuccessful = payment.token.paymentData.count != 0

if asyncSuccessful {
let payFort = PayFortController.init(enviroment: KPayFortEnviromentSandBox)
let request = NSMutableDictionary.init()
request.setValue(“100100000”, forKey: “amount”)
request.setValue(“AUTHORIZATION”, forKey: “command”)
request.setValue(“USD”, forKey: “currency”)
request.setValue(“email@domain.com”, forKey: “customer_email”)
request.setValue(“en”, forKey: “language”)
request.setValue(“merchant”, forKey: “merchant_reference”)
request.setValue(“gr66zzwW9” , forKey: “sdk_token”)
request.setValue(“APPLE_PAY” , forKey: “digital_wallet”)

payFort?.callPayFortForApplePay(withRequest: request,
applePay: payment,
currentViewController: self
, success: { (requestDic, responeDic) in
completion(.success)
}, faild:{ (requestDic, responeDic, message) in
completion(.failure)
})
}else {
completion(.failure)
}
}
```

------

### Apple Pay SDK Authorization/ Purchase - Request

```json
Placeholder: Sample code for Apple Pay SDK Authorization/Purchase - Request
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>
------

### Apple Pay SDK Authorization/ Purchase - Response

```json
Placeholder: Sample code for Apple Pay SDK authorization/Purchase Response in JSON format
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response - even the optional ones.</div>

------



## Test Your Wallet Integration

------

You can checkout this [link](testing.md) for testing your wallet integration

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

