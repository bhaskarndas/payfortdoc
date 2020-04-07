PayFort supports MasterPass, Visacheckout and ApplePay.

------

# MasterPass

------

As another move towards a cashless environment, PayFort provides **MasterPass**; a digital wallet that securely stores the buyer’s credit card details and shipping addresses and information, making shopping through thousands of online Merchants simple and convenient. This is fulfilled by enhancing and simplifying the buyer’s digital shopping experience.

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

2. The FORT returns a response to the Merchant.

3. The FORT inserts the response parameters into a JavaScript.

4. A lightbox appears to the buyer where he enters his credentials, selects the card type and the shipping address, and clicks “Finish Shopping”.

5. The FORT either proceeds to Authorize or Purchase the payment based on the value of the command parameter sent in the Merchant’s form.

6. The FORT returns a response to the Merchant.(Please refer to section MasterPass Service - Response for the Response Parameters).

   <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>In the Redirection work flow, the “Channel” will always be considered redirection and the “Default Operation” won’t be considered.</div>

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>If the Merchant sent the “payment_option” value in his request, the FORT will use the value found in the request, no matter what other options are supported by the Merchant. However, if this value wasn’t sent in the Merchant’s request, the FORT will retrieve all the payment options supported by the Merchant.</div>

------

### Parameters Submission Type

HTTPs Form Post Request.

------

### Service Request Example

Below is the sample html request.

```html
<form action="https://sbcheckout.payfort.com/FortAPI/paymentPage"method="post"id="simulatorForm">
<input type="hidden" name="digital_wallet" id="digital_wallet" value="MASTERPASS"/>
<input type="hidden" name="command"id="command" value="AUTHORIZATION"/>
<input type="hidden" name="access_code" id="access_code" value="zx0IPmPy5jp1vAz"/>
<input type="hidden" name="merchant_identifier" id="merchant_identifier" value="CycHZxVj"/>
<input type="hidden" name="merchant_reference" id="merchant_reference" value="XYZ9239-yu898"/>
<input type="hidden" name="amount" id="amount" value="10000"/>
<input type="hidden" name="currency" id="currency" value="AED"/>
<input type="hidden" name="language" id="language" value="en"/>
<input type="hidden" name="customer_email" id="customer_email" value="someone@email.com"/>
<input type="hidden" name="signature" id="signature" value="7cad05f0212ed933c9a5d5dffa31661acf2c827a"/>
<input type="hidden" name="payment_option"id="payment_option" value="VISA"/>
<input type="hidden" name="order_description" id="order_description" value="iPhone 6-S"/>
<input type="hidden" name="customer_ip" id="customer_ip" value="192.178.1.10"/>
<input type="hidden" name="customer_name" id="customer_name" value="John Smith"/>
<input type="hidden" name="cart_details" id="cart_details" value='{"sub_total":"900","cart_items":[{"item_description":"Xbox","item_image":"http://image.com","item_name":"Xbo x 360","item_price":"300","item_quantity":"2"},{"item_description":"Playstation 3","item_image":"http://image.com","item_name":"Playstation 3","item_price":"150","item_quantity":"2"}]}'/>
<input type="hidden" name="return_url" id="return_url" value="http://backtothemerchanturl.com"/>
<input value="Send" type="submit"> </form>
```

The following is an example for “cart_details” parameter:

```html
<input type=“hidden”
       name=“cart_details” 
       id=“cart_details” 
       value=
       ’{
       “sub_total”:“900”,
       “cart_items”:[{
       “item_description”:“Xbox”,
       “item_image”:“http://image.com”,
       “item_name”:“Xbox 360”,
       “item_price”:“300”,
       “item_quantity”:“2”},{
       “item_description”:“Playstation 3”,
       “item_image”:“http://image.com”,
       “item_name”:“Playstation 3”,
       “item_price”:“150”,
       “item_quantity”:“2”}]}’/> 
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

### MasterPass Hosted

------

Masterpass Hosted accepts digital wallet transactions without redirection to Masterpass pages and instead; it will be hosted on the Merchant website.



# VisaCheckout

------

**Visa Checkout** is a digital wallet that securely stores the buyer’s credit card details and shipping addresses and information, making shopping through thousands of online Merchants simple and convenient. This service enhances and simplifies the buyer’s online shopping experience. **Visa Checkout** can be offered through two different integrations:

- [Merchant Hosted Checkout Button.](#merchant-hosted-checkout-button)
- [PayFort Hosted Checkout Button.](#payfort-hosted-checkout-button)

------

### Merchant Hosted Checkout Button

#### Integration Flow

------

This integration allows the you to host Visa Checkout button on his website giving him maximum control over the look and feel and user experience. The following steps describe how this integration works:

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

Apple Pay provides an easy way for users to buy goods and services using iPhone, iPad and Apple Watch through mobile application or website. Checking out is as easy as selecting “Apple Pay” and placing a finger on the touch ID of an iPhone, iPad or simply double clicking the side button on the Apple Watch. It’s quick, easy and secure!

When using a credit or debit card with Apple Pay, the actual card numbers are not stored on the device, nor on Apple servers. Instead, a unique Device Account Number is assigned, encrypted and securely stored in the Secure Element on your device, where each transaction is authorized with a one-time unique dynamic security code.

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

## Setting Up Apple Pay

------

1. Kindly visit [developer.apple.com](http://developer.apple.com/) where you will Create a developer account, an Apple Pay Merchant ID and complete the Apple Pay certification (export the payment processing certificate in p12 file)
2. Integrate Apple Pay in your app/website using the Apple Pay documentation found at https://developer.apple.com/apple-pay
3. Submit the encrypted Apple Pay payload to PayFort’s API for decryption / processing. Please contact [integration@payfort.com](mailto:integration@payfort.com) for PayFort’s integration documentation

------

### Parameters Submission Type

REST POST request using JSON.

------

## The ApplePay Request

------

The sample JSON request

```http
{
"digital_wallet":"APPLE_PAY",
"command":"PURCHASE",
"access_code":"zx0IPmPy5jp1vAz8Kpg7",
"merchant_identifier":"CycHZxVj",
"merchant_reference":"XYZ9239yu898",
"amount": "10000",
"currency": "AED",
"language":"en",
"customer_email":"customer@domain.com",
"apple_data":“C0QcNob17qrbYmBX63UxsfLOp3iqNU7ieMz1fmSlAYEG8gbkXsukzymwy7E3cqFZHD4UCZRL5uX
cSfOIqT99c4xsqalQ3gIZgwhqcLZL6m/xqOuxqx1j9XQ9C54nmZJyAh6//zQWjeJhIeybGKS1zHlNRba
OScMp+hLMcvBnoL3EYkfbQiPJrxWUqXxGx/lxeo9G72Yp5Q
fsuQ74RW/mwBmKXtirFq7UsUt/Mh/KGgw”,
"apple_signature":"MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgEFADCABgkqhkiG9w0BBwEAAKCAMIID5jCC…",
"apple_header":{
“apple_transactionId”: “93eec76cbedaedca44648e3d5c314766906e4e78ce33cd3b8396f105a1c0daed”,
“apple_ephemeralPublicKey”: “MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEM9JqF04vDlGIHEzWsaDm4bGBlTJdCn3+DH8ptlA
mOSwVddD7/FN93A2o+l7i2U6Lmjb8WhKJcz6ZB+2MabcF4g==”,
“apple_publicKeyHash”: “bVTUiyTv0uCJgQz8SNYHBHOlHMD6sR1qDuCqTaETzkw=”
},
"apple_transactionId":"93eec76cbedaedca44648e3d5c314766906e4e78ce33cd3b8",
"apple_ephemeralPublicKey":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEM9JqF04vD",
"apple_publicKeyHash":"bVTUiyTv0uCJgQz8SNYHBHOlHMD6sR1qDuCqTaETzkw=",
"apple_paymentMethod": " {
“apple_displayName”: “Visa 0492”,
“apple_network”: “Visa”,
“apple_type”: “debit”
}",
"apple_applicationData":"5173d4e05f2e07dc4e7ea9669bda185712ffffe1d6
cfce2d4e854d7661e70d67…",
"eci":"MOTO",
"signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
"order_description":"iPhone6-S",
"customer_ip":"192.178.1.10",
"customer_name":"John Smith",
"phone_number":"00962797219966",
"settlement_reference":"XYZ9239-yu898",
"merchant_extra":"JohnSmith",
"merchant_extra1":"JohnSmith",
"merchant_extra2":"JohnSmith",
"merchant_extra3":"JohnSmith",
"merchant_extra4":"JohnSmith",
"merchant_extra5":"JohnSmith",
"return_url":"http://www.merchant.com"
}
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

------

## The ApplePay Response

Here is the sample response

```json
{
 "digital_wallet":"APPLE_PAY",
 "command":"PURCHASE",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239yu898",
 "amount":"10000",
 "currency":"AED",
 "language":"en",
 "customer_email":"customer@domain.com",
 "eci":"MOTO",
 "token_name":"Op9Vmp",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "order_description":"iPhone6-S",
 "fort_id":"149295435400084008",
 "payment_option":"MASTERCARD",
 "customer_ip":"192.178.1.10",
 "customer_name":"John Smith",
 "authorization_code":"P1000000000000372136",
 "response_message":"Success",
 "response_code":"20064",
 "status":"04",
 "expiry_date":"2105",
 "card_number":"400555******0001",
 "phone_number":"00962797219966",
 "settlement_reference":"XYZ9239-yu898",
 "merchant_extra":"JohnSmith",
 "merchant_extra1":"JohnSmith",
 "merchant_extra2":"JohnSmith",
 "merchant_extra3":"JohnSmith",
 "merchant_extra4":"JohnSmith",
 "merchant_extra5":"JohnSmith",
 "return_url":"http://www.merchant.com"
}
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

## Apple Pay SDK Service

------

Apple Pay is a digital wallet that allows Merchant’s customers to make payments using different Apple devices through FORT iOS SDK. The Customer authenticate his identity with Touch ID fingerprint verification to complete the payment.

### Requirements

Before you start Apple Pay SDK integration; you need to check the following points:
• You will need to have one of these iOS devices (iPhone 6, iPhone 6s, iPhone 6 Plus, iPhone 6s Plus, iPhone 7, iPhone 7 Plus, iPhone SE, iPad Air 2, iPad mini 3, iPad mini 4, and iPad Pro models) running iOS 8.1 or later.

• You will need a Mac with Xcode 6.1 or newer installed. You can install or upgrade Xcode in the [Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835).

• You will also need an apple developer account and a membership in the iOS Developer Program. You can create a one from [here](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=891bd3417a7776362562d2197f89480a8547b108fd934911bcbea0110d07f757&path=%2Fregister%2Fagree%2F&rv=1).

• You will need to download the FORT iOS Mobile SDK, click [here](https://docs.payfort.com/docs/mobile-sdk/build/lib/PayFortSDK2.1.zip).

### Get Started

Before you start Apple Pay integration with PayFort please refer to the following URL [here](https://developer.apple.com/apple-pay/get-started/) to complete the following steps:

1. Setup your Apple Pay account.

2. Complete the integration with Apple Pay SDK.

3. After completing the integration with Apple Pay, check that you have got the following:
     • Apple merchantID.
     • Merchant certificate.
     • Payment processing certificate.
   Then copy the following sample code to complete integration with FORT Mobile SDK:

   **Object-C code**

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



**Swift Code**

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
{
"digital_wallet":"APPLE_PAY",
"command":"PURCHASE",
"access_code":"zx0IPmPy5jp1vAz8Kpg7",
"merchant_identifier":"CycHZxVj",
"merchant_reference":"XYZ9239yu898",
"amount": "10000",
"currency": "AED",
"language":"en",
"customer_email":"customer@domain.com",
"sdk_token":"Dwp78q3",
"payment_option":"MASTERCARD",
"eci":"ECOMMERCE",
"signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
"order_description":"iPhone6-S",
"customer_ip":"192.178.1.10",
"customer_name":"John Smith",
"phone_number":"00962797219966",
"token_name":"Op9Vmp",
"settlement_reference":"XYZ9239-yu898",
"merchant_extra":"JohnSmith",
"merchant_extra1":"JohnSmith",
"merchant_extra2":"JohnSmith",
"merchant_extra3":"JohnSmith",
"merchant_extra4":"JohnSmith",
"merchant_extra5":"JohnSmith",
"return_url":"http://www.merchant.com"
}
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

------

### Apple Pay SDK Authorization/ Purchase - Response

```json
{
 "digital_wallet":"APPLE_PAY",
 "command":"PURCHASE",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239yu898",
 "amount":"10000",
 "currency":"AED",
 "language":"en",
 "customer_email":"customer@domain.com",
 "eci":"ECOMMERCE",
 "token_name":"Op9Vmp",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "order_description":"iPhone6-S",
 "fort_id":"149295435400084008",
 "sdk_token": "Dwp78q3",
 "payment_option":"MASTERCARD",
 "customer_ip":"192.178.1.10",
 "customer_name":"John Smith",
 "authorization_code":"P1000000000000372136",
 "response_message":"Success",
 "response_code":"20064",
 "status":"04",
 "expiry_date":"2105",
 "card_number":"400555******0001",
 "phone_number":"00962797219966",
 "settlement_reference":"XYZ9239-yu898",
 "merchant_extra":"JohnSmith",
 "merchant_extra1":"JohnSmith",
 "merchant_extra2":"JohnSmith",
 "merchant_extra3":"JohnSmith",
 "merchant_extra4":"JohnSmith",
 "merchant_extra5":"JohnSmith",
 "return_url":"http://www.merchant.com"
}
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

