# Merchant Page

This integration uses PayFort inline frame (iframe) to collect Customer's credit card information. It helps you to accept your Customer's payments on your website.

PayFort processes the transaction and returns the results back to the Merchants through invisible redirection.

------

## Features

- No Customer redirection.
- No PCI-Compliance needed.
- A replica of your website appearance and your payment flow.

------



## How it works - overview

**1.** The Merchant page (payment details form) will appear to your Customer encapsulated inside an iframe that has the same look and feel of your website.

**2.** We then receive the payment details and send you confirmation to complete the transaction.

 Remember - You have the option to redirect the Customer directly to the Merchant Page (payment details form).

### Integration Flow

The Customer begins the checkout process on the Merchant’s website.

**2.** The Merchant requests to display the Merchant Page (payment details form) encapsulated inside an iframe which has been themed as the Merchant website. Then the Customer enters the card’s details on the Merchant page.

**3.** PayFort checks the card details.

**4.** PayFort creates a token for the Customer transaction and sends it to the Merchant.

**5.** The Merchant then sends a [JSON request](https://docs.payfort.com/docs/api/build/index.html#merchant-page-operations) along with the token to PayFort.

**6.** In case the Merchant receives from PayFort a 3-D Secure URL “3ds_url”, and response indicating that a 3Ds check is required:

  **a.** The Merchant redirects the Customer to the ACS to check his card enrollment.

  **b.** The Customer enters authentication data on the ACS platform.

  **c.** The ACS performs authentication of the Customer’s data and sends the authentication results to PayFort.



 Remember - In this case, PayFort returns **status “20: On hold”** and **message “064: 3-D Secure check requested”**. For example, PayFort is waiting for the Merchant to authenticate the Customer.

**7.** PayFort completes the operation based on the 3-D Secure response and returns the response to the Merchant.

**8.** PayFort sends the payment results to the Merchant.

 Remember -
\- If the Merchant includes the “token_name” parameter in the request and this Token already has a successful Authorization, then the card number (masked) and expiry date will be displayed in their allocated fields.
\- If the Token is sent by the Merchant, it will be generated with the same name sent by the Merchant.

### Merchant Page URLs

#### Test Environment URLs

https://sbcheckout.payfort.com/FortAPI/paymentPage

#### Production Environment URLs

https://checkout.payfort.com/FortAPI/paymentPage

### Parameters Submission Type

HTTPs Form Post Request

## Merchant Page - Request

**Include the following parameters in the Request you will send to PayFort:**

------

**service_command** ^string, mandatory^
	Description - Command
	Maximum length - 20
	Possible values - **Tokenization**

## Merchant Page - Response

**The following parameters will be returned in PayFort’s Response:**

## Merchant Page Operations

### Merchant Page Operations URLs

**Test Environment URL:**

https://sbpaymentservices.payfort.com/FortAPI/paymentApi

**Production Environment URL:**

https://paymentservices.payfort.com/FortAPI/paymentApi

### Parameters Submission Type

REST POST request using JSON.

### Operations - Request

**Include the following parameters in the Request you will send to PayFort:**

### Operations - Response

**The following parameters will be returned in PayFort’s Response:**

## How to add the Tokenization service on the Merchant Page channel?

The Tokenization service is applicable to be integrated through the Merchant Page Channel through the below steps:
**1.** The Customer processes the first PURCHASE/ AUTHORIZATION payment successfully.
**2.** The Merchant will receive a token_name in the response. This token_name should be considered as a permanent token name, and it can be used in the future customer’s payments by submitting the token_name in the next PURCHASE/ AUTHORIZATION payment with card_security_code parameter.
**3.** No need to open the Merchant Page to fill all the card details again in the next checkouts.

If the Customer wants to update/ delete his card, you should check [Update Token](https://docs.payfort.com/docs/api/build/index.html#update-token-service) section.

 **Remember:**
Please refer to section [FORT Tokenization Service](https://docs.payfort.com/docs/api/build/index.html#fort-tokenization-service) for more details about the token name parameter.

## Merchant Page Customization

**This is a list with all customizable CSS classes on the basic merchant page:**

- The **`Wrapper`** class: responsible for the total width of the form container and the background.
- The **`Container`** class: responsible for the form’s shape and width.
- The **`Popover`** class: responsible for the error messages.
- The **`Half-container`** class: used to merge the date and CVV fields into one block if needed.
- The **`Input`** class: is the container of each single input field.
- The **`Pay`** class: responsible for the submit button.
- The **`Visa/ MasterCard`** classes: used to change the color of the Visa/ MasterCard colors.

 Remember - You can always create multiple theme files that will enable you to switch freely and easily between them when necessary.

 Remember - “Theme” files can be uploaded from the back-office using the Payment Page template screen.

