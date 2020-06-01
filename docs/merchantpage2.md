# What is Merchant Page 2 integration?

------

You can also build your own custom payment form without using default payment template provided by PayFoRT and collect customer's payment details and send it to PayFORT server for further processing.



![custom-payment](img\custom-payment-form.png)

Figure 1

------

### How it works?

------

1. You develop your own custom payment details form that collects the card details (credit card number, expiry date, CVV).

2. Customer fills his/her payment details in the custom payment checkout page. 

3. PayFORT server receives the payment details and validates the same.

4. PayFORT then sends a confirmation to your checkout page to complete the transaction which includes Token.

5. You use the token to complete the [Authorization or Purchase operation](https://docs.payfort.com/docs/api/build/index.html#operations-request).

   <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>You should develop a form that does not send data to your website but directly submits the form to PayFORT.</div>

------

### Integration Flow

![image-20200213230424907](img/image-20200213230424907.png)

Figure 2

Here is the Integration flow description

<div><ol>
    <li>The customer begins the checkout process on your website.</li>
    <li>Your website displays the custom payment form to collect the card’s details. Then the Customer enters the card’s details on the payment page.</li>
    <li>PayFORT checks the card details.</li>
    <li>PayFORT creates a token for the Customer transaction and sends it to the payment page.</li>
    <li>The merchant site sends a payment request along with the Token to PayFORT</li>
    <li>In case your page receives from PayFORT server a 3-D Secure URL <mark>3ds_url</mark>, and response indicating that a 3ds check is required then:<br><div class="alert alert-info"><ol><li>Your payment page redirects the Customer to the ACS to check his card enrollment.</li><li>The Customer enters authentication data on the ACS platform.</li><li>The ACS performs authentication of the Customer’s data and sends the authentication results to PayFORT.</li><ol></ol></ol></div></li>
<li>PayFORT completes the operation based on the 3-D Secure response and returns the response to your payment page.</li>
<li>PayFORT sends the payment results to your site.</li>
</ol></div>


<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>In case of 3ds secure check, PayFort returns status <mark>20: On hold</mark>and message <mark>064: 3-D Secure check requested</mark>message.For example, PayFort is waiting for your payment page to authenticate the Customer.</div>

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>If the Token is sent by the payment page, it will be generated with the same name sent by the website.</div>

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Payment processing page, payment form and payment details form all refer to payment page on your site where customer will enter card details.</div>

For more details on Tokens and Tokenization process visit the [link](tokenization.md)

------

##    Give It a Try

Use one of our [test cards](testing.md) and corresponding CVV to try out for yourself. 

You can use any expiry date (`mm/yy`), as long as it's in the future.

------

## Endpoints

------

Endpoints for Merchant Page is also applicable for Merchant 2 Integration. You can check the Endpoints by visiting this [link](merchantpage1.md)

------

## Before you start

Make sure you have your `access_code`. Refer figure 3. You can find it in the [backoffice](https://fort.payfort.com/account/MerchantManagement/EntitySecurity), under Integration Settings <mark>Security Settings > Access Code</mark>. If you don't have an account with us yet, you can create a test account by visiting the [link]("https://www.payfort.com/test-account/"). You can also get started with an active account by visiting this [link](https://www.payfort.com/get-started/)

------

![](img/paymentintegration settings.png)

Figure 3 : Uploading custom template

The Payment Page Template available in the backoffice provides you the feature to create a custom payment processing page. Refer to the figure 4. Once you upload your custom payment page our support team will validate the same.



![](img/integrationsettings2.png)

Figure 4:  Generating Access Code.

------

## Sample Code

The following code snippet shown here is an example of the start of the payment process. You can refer to this example, replacing the supplied `acccess_code` with your own. The card token will be posted via the URL specified in the form's `action` attribute.

```HTML

<form method="post" action="https://sbcheckout.payfort.com/FortAPI/paymentPage" id=form1 name=form1>
<input type="hidden" NAME="service_command" value="TOKENIZATION">

<input type="submit" value="" id="submit2" name="">

```

------

The above code snippet is an HTML based form that will post a request to PayFORT server. The request parameters are also added in the input tag of the code. However, If you are not familiar with HTML tags and forms then you can checkout this [site](https://www.w3schools.com/).

The form action tag consists of the endpoints. This will come handy whenever submit action is performed on the page. Once the form is submitted the parameters provided in the form would be sent to the PayFORT server and Endpoints will serve as communication link between your page and PayFORT server.



## Request Parameters

------

<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info">&nbsp;&nbsp;</i>The parameters are mandatory and are required by PayFORT server to validate, authenticate and provide the tokens for processing of payment</div>

Please refer to the section [Merchant Page 2 Request Parameters](merchantpageparameters.md) for request parameters.

## Response Parameters

The PayFORT server will return the response in JSON format. Here is the sample response along with the parameters returned by PayFORT server.

```json
[{
"service_command": "TOKENIZATION",
"access_code": "zx0IPmPy5jp1vAz8Kpg7",
"merchant_identifier": "CycHZxVj",
"merchant_reference": "XYZ9239-yu898",
"language": "en",
"signature": "7cad05f0212ed933c9a5d5dffa31661acf2c827a",
"token_name": "Op9Vmp",
"expiry_date": "2105",
"card_number": "400555*****0001",
"response_message": "012",
"response_code": "11012",
"status": "11",
"card_bin": "478773",
"card_holder_name": "John Smith",
"remember_me": "No",
"return_url": "http://www.merchant.com"
}]
```

Please refer to the section [Merchant Page 2 Response](merchantpageparameters.md) for reponse parameters.

------

## Payment Page Customization

When you begin designing your own custom payment page you will also need to style your custom payment page so that it is in line with the look and feel of your website. Inorder to style your custom payment page you will require CSS files and within those files you need use the css classes. If you are new to HTML and CSS don't worry you can visit this [link](https://www.w3schools.com/css/default.asp) to learn about HTML/CSS.

This is a list with all customizable CSS classes on the basic payment page:

- **The `Wrapper` class**

  It is responsible for the total width of the form container and the background.

- **The `Container` class**

  It is responsible for the form’s shape and width.

- **The `Popover` class**

  It is responsible for the error messages.

- **The `Half-container` class**

  It is used to merge the date and CVV fields into one block if needed.

- **The `Input` class**

  It is the container of each single input field.

- **The `Pay` class**

  It is responsible for the submit button.

- **The `Visa/ MasterCard` classes**

  It is used to change the color of the Visa/ MasterCard colors.

  <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>You can always create multiple theme files that will enable you to switch freely and easily between them when necessary.Theme files offer you the flexibility to change the look and feel of your page.</div>

  <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i><mark>Theme</mark> files can be uploaded from the back-office using the Payment Page template screen.</div>

 

------

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

To learn more about Tokens and Tokenization process visit this [link](tokenization.md)

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).