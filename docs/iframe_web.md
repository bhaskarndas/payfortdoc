# iFrame For Web

You can setup payment form and start accepting payments within few minutes with the help of iFrame. PayFort provides easy to use iFrame which can be easily integrated with your payment form. It takes the look and feel of your merchant site and accepts payments from major credit cards including MADA, VISA, Mastercard, Diners etc. 



![Figure1](img/image-20200211222706973.png)



Figure 1 - Using PayFort iFrame for web

------

## How it Works

**1.** The payment details form will appear to your Customer encapsulated inside an iframe that has the same look and feel as that of your website.

**2.** PayFort then receives the payment details and sends you the confirmation to complete the transaction.

 ***Note*** - *You have the option to redirect the Customer directly to the payment details form.*

------

## Integration Flow

![Integration](img/image-20200212214741915.png)

Figure 2 : Integration Flow using iFrame

1. The customer begins the checkout process on your website.

2. The payment page encapsulated inside iFrame is displayed.  Then the Customer enters the card’s details on the payment page.

3. PayFort checks the card details.

4. PayFort creates a token for the Customer transaction and sends it to the payment page.

5. The Payment page then sends a [JSON request](https://docs.payfort.com/docs/api/build/index.html#merchant-page-operations) along with the token to PayFort.

6. In case your page receives from PayFort a 3-D Secure URL “3ds_url”, and response indicating that a 3Ds check is required:<br>
   **a.** Your payment page redirects the Customer to the ACS to check his card enrollment.<br>**b.** The Customer enters authentication data on the ACS platform.<br>**c.** The ACS performs authentication of the Customer’s data and sends the authentication results to PayFort.

7. PayFort completes the operation based on the 3-D Secure response and returns the response to your payment page.

8. PayFort sends the payment results to your site.


   ***Note*** -

   * In this case, PayFort returns* **status “20: On hold”** *and* **message “064: 3-D Secure check requested”**. *For example, PayFort is waiting for your payment page to authenticate the Customer.*
   * *If you include the “token_name” parameter in the request and this Token already has a successful Authorization, then the card number (masked) and expiry date will be displayed in their allocated fields.*
   * If the Token is sent by you, it will be generated with the same name as sent by your page.
   * Payment processing page, payment form and payment details form all refer to payment page on your site where customer will enter card details.

------

##    Give It a Try

Use one of our [test cards](testing.md) and corresponding CVV to try iFrames out for yourself. 

You can use any expiry date (`mm/yy`), as long as it's in the future.

Comment--Need to add dynamic code script block to accept test card and generate a test token here.

------

## Integrate iFrames to Payment Page

## Endpoints

### Live

```
POST https://checkout.payfort.com/FortAPI/paymentPage
```

### Sandbox 

```
POST https://sbcheckout.payfort.com/FortAPI/paymentPage
```

------

### Before you start

Make sure you have your `access_code`. Refer to Figure 2 [<i class="fa fa-link"></i>](#figure2). You can find it in the [backoffice](https://fort.payfort.com/account/MerchantManagement/EntitySecurity), under Integration Settings > **Security Settings > Access Code**. If you don't have an account with us yet, you can create a test account by visiting the [link]("https://www.payfort.com/test-account/"). You can also get started with an active account by visiting this [link](https://www.payfort.com/get-started/)



<a name="figure2"></a><br/>

![](img\integrationsettings2.png)

Figure 2 : Access Code Generation

The Payment Page Template available in the backoffice provides you the feature to create a payment processing page using PayFort iFrame. Refer to the Figure 3  [<i class="fa fa-link"></i>](#figure3)



<a name="figure3"></a><br/>

![](img\paymentintegration settings.png)

Figure 3 : Use Payment Settings to create a payment form

------

## Sample iFrame code snippet

The following sample code snippet is the start of the payment process and allows you to tokenize a customer's sensitive card information using iFrames. 


​    


```html
<html>
   </head>
<body>
<iframe  style="border:5px dotted red" name="myframe" src = "" width="400" height="600">
</iframe>
<form action="https://sbcheckout.payfort.com/FortAPI/paymentPage" method="post" id="" target="myframe">
 
<INPUT type="hidden" NAME="service_command" value="TOKENIZATION">

<INPUT type="hidden" NAME="language" value=" ">

<INPUT type="hidden" NAME="merchant_identifier" value="">

<INPUT type="hidden" NAME="access_code" value="">

<INPUT type="hidden" NAME="signature" value="">

<INPUT type="hidden" NAME="return_url" value="">
 
<INPUT type="hidden" NAME="merchant_reference" value="">

<input value="Send" type="submit" id="form1">

</form>
</body>

</html>
```

------

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).