PayFort supports MasterPass, Visacheckout and ApplePay

------

## MasterPass

As another move towards a cashless environment, PayFort provides **MasterPass**; a digital wallet that securely stores the buyer’s credit card details and shipping addresses and information, making shopping through thousands of online Merchants simple and convenient. This is fulfilled by enhancing and simplifying the buyer’s digital shopping experience.

<div class="alert alert-info" role="alert"><i class="fa fa-info ">&nbsp;&nbsp;</i>PAYFORT now supports MasterPass Redirect v7 in addition to v6.</div>

### Service Endpoints

------

#### Sandbox

```html
POST https://sbcheckout.payfort.com/FortAPI/paymentPage
```

#### Live

```html
POST https://checkout.payfort.com/FortAPI/paymentPage
```

### Redirection

------

#### Integration Flow

1. The Merchant submits a form that includes all the parameters.

   

   The Merchant calls the following URL to be redirected to the FORT:   
```html
   https://checkout.payfort.com/FortAPI/paymentPage
```

   

2.   The FORT returns a response to the Merchant.

3. The FORT inserts the response parameters into a JavaScript.

4. A lightbox appears to the buyer where he enters his credentials, selects the card type and the shipping address, and clicks “Finish Shopping”.

5. The FORT either proceeds to Authorize or Purchase the payment based on the value of the command parameter sent in the Merchant’s form.

   <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>If the Merchant sent the “payment_option” value in his request, the FORT will use the value found in the request, no matter what other options are supported by the Merchant. However, if this value wasn’t sent in the Merchant’s request, the FORT will retrieve all the payment options supported by the Merchant.</div>

6. The FORT returns a response to the Merchant.(Please refer to section MasterPass Service - Response for the Response Parameters).

 

<div class="alert alert-info" role="alert><i class="fa fa-info">&nbsp;&nbsp;</i>In the Redirection work flow, the “Channel” will always be considered redirection and the “Default Operation” won’t be considered.</div>

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



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp; </i>The following is an example for “cart_details” parameter:</div>

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





## VisaCheckout

------

**Visa Checkout** is a digital wallet that securely stores the buyer’s credit card details and shipping addresses and information, making shopping through thousands of online Merchants simple and convenient. This service enhances and simplifies the buyer’s online shopping experience. **Visa Checkout** can be offered through two different integrations:

- [Merchant Hosted Checkout Button.](#merchant-hosted-checkout-button)
- [PayFort Hosted Checkout Button.](#payfort-hosted-checkout-button)

------

### Merchant Hosted Checkout Button

#### Integration Flow

------

This integration allows the you to host Visa Checkout button on his website giving him maximum control over the look and feel and user experience. The following steps describe how this integration works:

1. You should include the following JavaScript in the HTML header of its checkout page. This JavaScript loads the Visa Checkout library and defines handlers to initialization and payment events.

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
```

2.  You should use the following class to render Visa Checkout button that a consumer clicks to initiate a payment.

```html
   <body>
   <img alt=“Visa Checkout” class=“v-button” role=“button”
   src=“https://sandbox.secure.checkout.visa.com/wallet-services-web/xo/button.png?cardBrands=VISA,MASTERCARD” />
   </body>
```

   #### Endpoints

------

   **Sandbox**

```http
   https://sandbox.secure.checkout.visa.com/wallet-services-web/xo/button.png
```

   **Live**

```http
   https://secure.checkout.visa.com/wallet-services-web/xo/button.png
```

   

3. You should use the following JavaScript to control the operation on Visa Checkout on the website.

```html
   <body>
   <script type=“text/javascript”
   src=“https://sandbox-assets.secure.checkout.visa.com/checkout-widget/resources/js/integration/v1/sdk.js”>
   </script>
   </body>
```

   #### Endpoints

------

   **Sandbox**

```http
https://sandbox-assets.secure.checkout.visa.com/checkout-widget/resources/js/integration/v1/sdk.js
```

   **Live**

```http
https://assets.secure.checkout.visa.com/checkout-widget/resources/js/integration/v1/sdk.js
```

   

4. After completing the previous steps, the consumer clicks on Visa Checkout button, Visa Checkout light box appears and the user complete the checkout process.

5. You will receive a successful response. The response associated with the payment success event returns list of parameters. The Merchant has to collect the value of “call_id” parameter to be used in the following step.

6. You submit Purchase request to the FORT adding 2 extra parameters: digital-wallet, call_id. Please refer to Merchant Hosted Visa Checkout - Request for more details.

   <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Merchants Page should be activated to accept Purchase and Authorization transactions</div>

7. The Merchant system receives the FORT’s purchase request and then uses Visa Checkout update image pixel. Below you can find an example of how to use Visa Checkout update image pixel. Please refer to “Visa checkout PayFort documentation” for more details.

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

   

   







## Apple Pay

Apple Pay provides an easy way for users to buy goods and services using iPhone, iPad and Apple Watch through mobile application or website. Checking out is as easy as selecting “Apple Pay” and placing a finger on the touch ID of an iPhone, iPad or simply double clicking the side button on the Apple Watch. It’s quick, easy and secure!

When using a credit or debit card with Apple Pay, the actual card numbers are not stored on the device, nor on Apple servers. Instead, a unique Device Account Number is assigned, encrypted and securely stored in the Secure Element on your device, where each transaction is authorized with a one-time unique dynamic security code.

### Setting Up Apple Pay

------

1. Kindly visit [developer.apple.com](http://developer.apple.com/) where you will Create a developer account, an Apple Pay Merchant ID and complete the Apple Pay certification (export the payment processing certificate in p12 file)
2. Integrate Apple Pay in your app/website using the Apple Pay documentation found at https://developer.apple.com/apple-pay
3. Submit the encrypted Apple Pay payload to PayFort’s API for decryption / processing. Please contact [integration@payfort.com](mailto:integration@payfort.com) for PayFort’s integration documentation

------

## Test Your Wallet Integration

------

You can checkout this [link](testing.md) for testing your wallet integration

------

## Go to Full API

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

------

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).