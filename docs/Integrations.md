[TOC]

# Integrations

There are two ways by which you can achieve integrations as mentioned:

1. Using **PayFort iFrame**.

2. Using custom payment form.

   

------

## Features

- No Customer redirection.
- No PCI-Compliance needed.
- A replica of your website appearance and your payment flow.

------

## Integration Page URLs 

### Test Environment URLs

https://sbpaymentservices.payfort.com/FortAPI/paymentApi

### Production Environment URLs

https://paymentservices.payfort.com/FortAPI/paymentApi

### Parameters Submission Type

REST POST request using JSON

------

## 1. Using PayFort iFrame

You can use ***PayFort iFrame*** on your website to collect Customer's credit card information. 

*PayFort* processes the transaction and returns the results back to the your site through invisible redirection. Please refer figure 1.

![Figure1](img\image-20200211222706973.png)
Figure 1 - Using PayFort iFrame

------

### How it Works - Overview

**1.** The payment details form will appear to your Customer encapsulated inside an iframe that has the same look and feel of as that of your website.

**2.** PayFort then receives the payment details and sends you the confirmation to complete the transaction.

 ***Note*** - *You have the option to redirect the Customer directly to the payment details form.*

------

### Integration Flow Using iFrame

![Integration](img\image-20200212214741915.png)

1. The Customer begins the checkout process on your website.

2. The Merchant requests to display the Merchant Page (payment details form) encapsulated inside an iframe which has been themed as the Merchant website. Then the Customer enters the card’s details on the Merchant page.

3. PayFort checks the card details.

4. PayFort creates a token for the Customer transaction and sends it to the Merchant.

5. The Merchant then sends a [JSON request](https://docs.payfort.com/docs/api/build/index.html#merchant-page-operations) along with the token to PayFort.

6. In case the Merchant receives from PayFort a 3-D Secure URL “3ds_url”, and response indicating that a 3Ds check is required:

   **a.** The Merchant redirects the Customer to the ACS to check his card enrollment.

   **b.** The Customer enters authentication data on the ACS platform.

   **c.** The ACS performs authentication of the Customer’s data and sends the authentication results to PayFort.

***Note*** 

- *In this case, PayFort returns* **status “20: On hold”** *and* **message “064: 3-D Secure check requested”**. *For example, PayFort is waiting for the Merchant to authenticate the Customer.*

1. PayFort completes the operation based on the 3-D Secure response and returns the response to the Merchant.

2. PayFort sends the payment results to the Merchant.

   ***Note*** -
   \- *If you include the “token_name” parameter in the request and this Token already has a successful Authorization, then the card number (masked) and expiry date will be displayed in their allocated fields.*
   *\- If the Token is sent by you, it will be generated with the same name as sent by your website.*

   

------

### Integration Using iFrame

------

#### Request Parameters

**Include the following parameters in the Request you will send to PayFort:**

------

**service_command <sup>string,mandatory</sup>**

| Attribute Features              | Description      |
| :------------------------------ | :--------------- |
| Type                            | Command          |
| Maximum length                  | 20               |
| Possible values/Expected values | **TOKENIZATION** |

------

**Access_code**<sup> alphanumeric, mandatory</sup>

| Attribute Features | Description         |
| ------------------ | ------------------- |
| Type               | Access Code         |
| Maximum length     | 20                  |
| Possible values    | **zx0IPmPy5jp1vAz** |

------

**merchant_identifier** <sup>alphanumeric, mandatory</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The ID of the Merchant. |
| Maximum length     | 20                      |
| Possible values    | **CycHZxVj**            |

------

**merchant_reference**<sup>alphanumeric, mandatory</sup>

| Attribute Features | Description                    |
| ------------------ | ------------------------------ |
| Type               | Merchant’s unique order number |
| Maximum length     | 40                             |
| Special characters | \- _ .                         |
| Possible values    | **XYZ9239-yu898**              |

------

**language** <sup>string, mandatory</sup>

| Attribute Features              | Description                              |
| ------------------------------- | ---------------------------------------- |
| Type                            | The checkout page and messages language. |
| Maximum length                  | 2                                        |
| Possible values/Expected values | **en/ar**                                |

------

**signature** <sup>hash, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |
| Maximum length     | 200                                                          |
| Example            | **7cad05f0212ed933c9a5d5dffa31661acf2c827a**                 |

------

**token_name**<sup> alphanumeric, optional</sup>

| Attribute Features | Description                                       |
| ------------------ | ------------------------------------------------- |
| Type               | The token received from the Tokenization process. |
| Maximum length     | 100                                               |
| Special characters | **@ - _**                                         |
| Example            | **Op9Vmp**                                        |

------

**return_url**<sup> alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |
| Maximum length     | 400                                                          |
| Special characters | **$ ! = ? # & - _ /**                                        |
| Example            | [**http://www.merchant.com**](http://www.merchant.com)       |

------

#### Response Parameters

**The following parameters will be returned in PayFort’s Response:**

------

**service_command**<sup> string</sup>

| Attribute Features | Description      |
| ------------------ | ---------------- |
| Type               | Command          |
| Maximum length     | 20               |
| Possible values    | **TOKENIZATION** |

------

**access_code**<sup> alphanumeric</sup>

| Attribute Features | Description              |
| ------------------ | ------------------------ |
| Type               | Access Code              |
| Maximum length     | 20                       |
| Example            | **zx0IPmPy5jp1vAz8Kpg7** |

------

**merchant_identifier** <sup>alphanumeric</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The ID of the Merchant. |
| Maximum length     | 20                      |
| Example            | **CycHZxVj**            |

------

**merchant_reference** <sup>alphanumeric</sup>

| Attribute Features | Description                         |
| ------------------ | ----------------------------------- |
| Type               | The Merchant’s unique order number. |
| Maximum length     | 40                                  |
| Example            | **XYZ9239-yu898**                   |

------

**language** <sup>string</sup>

| Attribute Features | Description                             |
| ------------------ | --------------------------------------- |
| Type               | The checkout page and message language. |
| Maximum length     | 2                                       |
| Possible values    | **en/ar**                               |

------

**signature**<sup> hash</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |
| Maximum length     | 200                                                          |
| Example            | **7cad05f0212ed933c9a5d5dffa31661acf2c827a**                 |

------

**token_name** <sup>alphanumeric</sup>

| Attribute Features | Description                                       |
| ------------------ | ------------------------------------------------- |
| Type               | The token received from the Tokenization process. |
| Maximum length     | 100                                               |
| Example            | **Op9Vmp**                                        |

------

**expiry_date** <sup>numeric</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The card’s expiry date. |
| Maximum length     | 4                       |
| Example            | **2105**                |

------

**card_number** <sup>numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The masked credit card’s number. *Only the MEEZA payment option takes 19 digits card number.***AMEX payment option takes 15 digits card number.<br/>\*Otherwise, they take 16 digits card number.* |
| Maximum length     | 19                                                           |
| Example            | **400555******0001**                                         |

------

**response_message** <sup>alphanumeric</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | Message description of the response code. It returns according to the request language. |
| Maximum length           | 150                                                          |
| Possible/expected values | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages) |

------

**response_code**<sup> numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html#messages). |
| Maximum length     | 5                                                            |
| Example            | **20064**                                                    |

------

**status** <sup>numeric</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | A two-digit numeric value that indicates the status of the transaction. |
| Maximum length           | 2                                                            |
| Possible/Expected values | Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html#statuses). |

------

**card_bin** <sup>numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The first 6 digits of the card number.*If the card number for MEEZA was of length 19 then the card bin will be the first 8 digits. |
| Maximum length     | 8                                                            |
| Example            | **478773**                                                   |

------

**return_url** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |
| Maximum length     | 400                                                          |
| Example            | **http://www.merchant.com**                                  |

***Note:***

*Every parameter that you send in the Request should be received at your end in the Response -even the optional ones-.*

------

## 2. Using Custom Payment Form

You can also design and develop your own custom for for collecting the card details. The card details are sent directly to PayFort and substituted with Token. You can then use this Token to complete the transaction.

![image-20200213222409527](img\custom-payment-form)

------

### How it works - overview

**1.** You develop your own custom payment form that collects the card details (credit card number, expiry date, CVV), and sends the request to PayFort.
**2.** PayFort receives the payment details and returns the response which includes the Token to your website.
**3.** You use the token to complete the [Authorization or Purchase operation](https://docs.payfort.com/docs/api/build/index.html#operations-request).

 ***Note*** - You should develop a form that does not send data to your website but directly submits the form to PayFort.*

------

### Integration Flow Using Custom Payment Form

**1.** The Customer begins the checkout process on your website.

**2.** Your website displays the custom payment form to collect the card’s details. Then the Customer enters the card’s details on the payment page.

**3.** PayFort validates the card format.

**4.** PayFort creates a token for the card details and sends it back to your website.

**5.** Your website stores the Token and proceeds with the transaction.

**6.** Your website sends a payment request along with the Token to PayFort.

**7.** PayFort sends your website the 3-D Secure URL, and response indicating that a check is required:

  **a.** Payment form redirects the Customer to check his card enrollment.
  **b.** The Customer enters authentication data.
  **c.** 3-D Secure authentication is completed and PayFort receives the authentication results.

 ***Note*** - *In this case, PayFort returns* **status “20: On hold”** *and* **message “064: 3-D Secure check requested”**. *For example, PayFort is waiting for the payment form to authenticate the Customer.*

**8.** PayFort completes the operation based on the 3-D Secure response and returns the response to the website.

**9.** The payment results are displayed to the Customer.

 ***Note*** -
\- *If the Token is sent by the payment form, it will be generated with the same name sent by the website.*

------

### Integration Using Custom Payment Form

------

#### Request Parameters

**Include the following parameters in the Request you will send to PayFort:**

------

**service_command <sup>string,mandatory</sup>**

| Attribute Features              | Description  |
| :------------------------------ | :----------- |
| Type                            | Command      |
| Maximum length                  | 20           |
| Possible values/Expected values | TOKENIZATION |

------

**Access_code**<sup> alphanumeric, mandatory</sup>

| Attribute Features | Description     |
| ------------------ | --------------- |
| Type               | Access Code     |
| Maximum length     | 20              |
| Possible values    | zx0IPmPy5jp1vAz |

------

**merchant_identifier** <sup>alphanumeric, mandatory</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The ID of the Merchant. |
| Maximum length     | 20                      |
| Possible values    | CycHZxVj                |

------

**merchant_reference**<sup>alphanumeric, mandatory</sup>

| Attribute Features | Description                    |
| ------------------ | ------------------------------ |
| Type               | Merchant’s unique order number |
| Maximum length     | 40                             |
| Special characters | \- _ .                         |
| Possible values    | **XYZ9239-yu898**              |

------

**language** <sup>string, mandatory</sup>

| Attribute Features              | Description                              |
| ------------------------------- | ---------------------------------------- |
| Type                            | The checkout page and messages language. |
| Maximum length                  | 2                                        |
| Possible values/Expected values | **en/ar**                                |

------

**expiry_date** <sup>numeric, mandatory</sup>

| Attribute Features | Description                              |
| ------------------ | ---------------------------------------- |
| Type               | The checkout page and messages language. |
| Maximum length     | 4                                        |
| Example            | **2105**                                 |

------

**card_number** <sup>numeric, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The clear credit card’s number.<br />*Only the MEEZA payment option takes 19 digits card number.<br/>*AMEX payment option takes 15 digits card number.<br/>*Otherwise, they take 16 digits card number. |
| Maximum length     | 19                                                           |
| Example            | **4005550000000001**                                         |

------

**card_security_code** <sup>numeric, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A security code for the card. * Only AMEX accepts card security code of 4 digits. |
| Maximum length     | 4                                                            |
| Example            | **123**                                                      |

------

**signature** <sup>hash, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |
| Maximum length     | 200                                                          |
| Example            | **7cad05f0212ed933c9a5d5dffa31661acf2c827a**                 |

------

**token_name**<sup> alphanumeric, optional</sup>

| Attribute Features | Description                                       |
| ------------------ | ------------------------------------------------- |
| Type               | The token received from the Tokenization process. |
| Maximum length     | 100                                               |
| Special characters | **@ - _**                                         |
| Example            | **Op9Vmp**                                        |

------

**card_holder_name**<sup> string, optional</sup>

| Attribute Features | Description           |
| ------------------ | --------------------- |
| Type               | The card holder name. |
| Maximum length     | 50                    |
| Special characters | **@ - _**             |
| Example            | **John Smith**        |

------

**remember_me**<sup> string, optional</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | This parameter provides you with an indication to whether to save this token for the user based on the user selection. |
| Maximum length           | 3                                                            |
| Possible/Expected values | **-Yes**<br />**-No**                                        |

------

**return_url**<sup> alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |
| Maximum length     | 400                                                          |
| Special characters | **$ ! = ? # & - _ /**                                        |
| Example            | [**http://www.merchant.com**](http://www.merchant.com)       |

------

#### Response Parameters

**The following parameters will be returned in PayFort’s Response:**

------

**service_command**<sup> string</sup>

| Attribute Features | Description      |
| ------------------ | ---------------- |
| Type               | Command          |
| Maximum length     | 20               |
| Possible values    | **TOKENIZATION** |

------

**access_code**<sup> alphanumeric</sup>

| Attribute Features | Description              |
| ------------------ | ------------------------ |
| Type               | Access Code              |
| Maximum length     | 20                       |
| Example            | **zx0IPmPy5jp1vAz8Kpg7** |

------

**merchant_identifier** <sup>alphanumeric</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The ID of the Merchant. |
| Maximum length     | 20                      |
| Example            | **CycHZxVj**            |

------

**merchant_reference** <sup>alphanumeric</sup>

| Attribute Features | Description                         |
| ------------------ | ----------------------------------- |
| Type               | The Merchant’s unique order number. |
| Maximum length     | 40                                  |
| Example            | **XYZ9239-yu898**                   |

------

**language** <sup>string</sup>

| Attribute Features | Description                             |
| ------------------ | --------------------------------------- |
| Type               | The checkout page and message language. |
| Maximum length     | 2                                       |
| Possible values    | **en/ar**                               |

------

**signature**<sup> hash</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |
| Maximum length     | 200                                                          |
| Example            | **7cad05f0212ed933c9a5d5dffa31661acf2c827a**                 |

------

**token_name** <sup>alphanumeric</sup>

| Attribute Features | Description                                       |
| ------------------ | ------------------------------------------------- |
| Type               | The token received from the Tokenization process. |
| Maximum length     | 100                                               |
| Example            | **Op9Vmp**                                        |

------

**expiry_date** <sup>numeric</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The card’s expiry date. |
| Maximum length     | 4                       |
| Example            | **2105**                |

------

**card_number** <sup>numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The masked credit card’s number. *Only the MEEZA payment option takes 19 digits card number.***AMEX payment option takes 15 digits card number.<br/>\*Otherwise, they take 16 digits card number.* |
| Maximum length     | 19                                                           |
| Example            | ***400555******0001**                                        |

------

**response_message** <sup>alphanumeric</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | Message description of the response code. It returns according to the request language. |
| Maximum length           | 150                                                          |
| Possible/expected values | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages) |

------

**response_code**<sup> numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html#messages). |
| Maximum length     | 5                                                            |
| Example            | 20064                                                        |

------

**status** <sup>numeric</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | A two-digit numeric value that indicates the status of the transaction. |
| Maximum length           | 2                                                            |
| Possible/Expected values | Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html#statuses). |

------

**card_bin** <sup>numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The first 6 digits of the card number.*If the card number for MEEZA was of length 19 then the card bin will be the first 8 digits. |
| Maximum length     | 8                                                            |
| Example            | **478773**                                                   |

------

**card_holder_name** <sup>string</sup>

| Attribute Features | Description           |
| ------------------ | --------------------- |
| Type               | The card holder name. |
| Maximum length     | 50                    |
| Example            | **John Smith**        |

------

**remember_me** <sup>string</sup>

| Attribute Features        | Description                                                  |
| ------------------------- | ------------------------------------------------------------ |
| Type                      | This parameter provides you with an indication to whether to save this token for the user based on the user selection. |
| Maximum length            | 3                                                            |
| Possible/ expected values | **\- YES,<br /> - NO**                                       |

------

**return_url** <sup>string</sup>

| Attribute Features        | Description                                                  |
| ------------------------- | ------------------------------------------------------------ |
| Type                      | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |
| Maximum length            | 400                                                          |
| Possible/ expected values | **http://www.merchant.com**                                  |

***Note:***

*Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.*

------

# Integration Page - Operations

## Operations URLs

### **Test Environment URL**

https://sbpaymentservices.payfort.com/FortAPI/paymentApi

### **Production Environment URL**

https://paymentservices.payfort.com/FortAPI/paymentApi

------

### Parameters Submission Type

REST POST request using JSON.

------

### Operations - Request Parameters

**Include the following parameters in the Request you will send to PayFort:**

------

**command**<sup> string, mandatory</sup>

| Attribute Features | Description                 |
| ------------------ | --------------------------- |
| Type               | Command                     |
| Maximum length     | 20                          |
| Possible values    | **AUTHORIZATION, PURCHASE** |

------

**access_code**<sup> alphanumeric, mandatory</sup>

| Attribute Features | Description         |
| ------------------ | ------------------- |
| Type               | access code         |
| Maximum length     | 20                  |
| Example            | **zx0IPmPy5jp1vAz** |

------

**merchant_identifier** <sup>alphanumeric, mandatory</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The ID of the Merchant. |
| Maximum length     | 20                      |
| Example            | **CycHZxVj**            |

------

**merchant_reference** <sup>alphanumeric, mandatory</sup>

| Attribute Features | Description                         |
| ------------------ | ----------------------------------- |
| Type               | The Merchant’s unique order number. |
| Special characters | **- _ .**                           |
| Maximum length     | 40                                  |
| Example            | **XYZ9239-yu898**                   |

------

**amount** <sup>numeric, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. |
| Maximum length     | 10                                                           |
| Example            | **10000**                                                    |

------

**currency**<sup> string, mandatory</sup>

| Attribute Features | Description                                             |
| ------------------ | ------------------------------------------------------- |
| Type               | The currency of the transaction’s amount in ISO code 3. |
| Maximum length     | 3                                                       |
| Example            | **AED**                                                 |

------

**language** <sup>string, mandatory</sup>

| Attribute Features       | Description                              |
| ------------------------ | ---------------------------------------- |
| Type                     | The checkout page and messages language. |
| Maximum length           | 2                                        |
| Possible/Expected values | **en/ar**                                |

------

**customer_email** <sup>alphanumeric, mandatory</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The customer's email    |
| Maximum length     | 254                     |
| Special Characters | **_ - . @ +**           |
| Example            | **customer@domain.com** |

------

**customer_ip** <sup>alphanumeric, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | It holds the customer’s IP address.<br /> *It’s Mandatory, if the fraud service is active.<br /> *We support IPv4 and IPv6 as shown in the example below. |
| Maximum length     | 45                                                           |
| Special Characters | **. :**                                                      |
| Example            | **IPv4 → 192.178.1.10**<br />**IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf** |

------

**token_name** <sup>alphanumeric, mandatory</sup>

| Attribute Features | Description                                       |
| ------------------ | ------------------------------------------------- |
| Type               | The Token received from the Tokenization process. |
| Maximum length     | 100                                               |
| Special Characters | **- . @****                                       |
| Example            | **Op9Vmp**                                        |

------

**signature**<sup> hash, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |
| Maximum length     | 200                                                          |
| Example            | **7cad05f0212ed933c9a5d5dffa31661acf2c827a**                 |

------

**payment_option** <sup>string, optional</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | Payment Option                                               |
| Maximum length           | 10                                                           |
| Possible/Expected values | **- MASTERCARD**<br />- **VISA**<br />- **AMEX**<br />- **MADA** (for Purchase operations and eci Ecommerce only) Click here to download [**MADA Branding Document**](https://docs.payfort.com/pdf/mada branding - ecommerce merchant - payment providers.pdf)<br />**- MEEZA** (for Purchase operations and ECOMMERCE eci only) |

------

**eci** <sup>string, optional</sup>

| Attribute Features       | Description                                          |
| ------------------------ | ---------------------------------------------------- |
| Type                     | Ecommerce indicator.                                 |
| Maximum length           | 16                                                   |
| Possible/Expected values | - **ECOMMERCE**<br />- **MOTO**<br />- **RECCURING** |

------

**order_description** <sup>alphanumeric, optional</sup>

| Attribute Features | Description                            |
| ------------------ | -------------------------------------- |
| Type               | It holds the description of the order. |
| Maximum length     | 150                                    |
| Special characters | **' / . _ - # : $ Space**              |
| Example            | **iPhone 6-S**                         |

------

**card_security_code** <sup>numeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A security code for the card. <br />* Only AMEX accepts card security code of 4 digits. |
| Maximum length     | 4                                                            |
| Example            | **123**                                                      |

------

**customer_name** <sup>string, optional</sup>

| Attribute Features | Description           |
| ------------------ | --------------------- |
| Type               | The Customer’s name   |
| Maximum length     | 40                    |
| Special characters | **_ \ / - . ' Space** |
| Example            | **John Smith**        |

------

**merchant_extra** <sup>alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 999                                                          |
| Special characters | **. ; / _ - , ' @**                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra1** <sup>alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Special characters | **. ; / _ - , ' @**                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra2** <sup>alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Special characters | **. ; / _ - , ' @**                                          |
| Example            | **John Smith**                                               |

**merchant_extra3** <sup>alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Special characters | **. ; / _ - , ' @**                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra4** <sup>alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Special characters | **. ; / _ - , ' @**                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra5** <sup>alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Special characters | **. ; / _ - , ' @**                                          |
| Example            | **John Smith**                                               |

------

**remember_me**<sup> string, optional</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | This parameter provides you with an indication to whether to save this token for the user based on the user selection.<br /> *The Tokenization service MUST be activated in order to be able to send “remember_me” parameter. |
| Maximum length           | 3                                                            |
| Possible/Expected values | **-Yes**<br />**- No**                                       |

------

**phone_number**<sup>alphanumeric, optional</sup>

| Attribute Features | Description           |
| ------------------ | --------------------- |
| Type               | The customer’s number |
| Maximum length     | 19                    |
| Special characters | **+ - ( ) Space**     |
| Example            | **00962797219966**    |

------

**settlement_reference**<sup> alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. |
| Maximum length     | 34                                                           |
| Special characters | **- _ .**                                                    |
| Example            | **XYZ9239-yu898**                                            |

------

**return_url**<sup> alphanumeric, optional</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The URL of the Merchant’s page to be displayed to the customer when theorder is processed. |
| Maximum length     | 400                                                          |
| Special characters | **$ ! = ? # & - _ / : .**                                    |
| Example            | **http://www.merchant.com**                                  |

***Note*** : Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.<br/>For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.<br/>Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.

------

### Operations - Response Parameters

**The following parameters will be returned in PayFort’s Response:**

------

**command**<sup> string</sup>

| Attribute Features | Description                 |
| ------------------ | --------------------------- |
| Type               | Command                     |
| Maximum length     | 20                          |
| Possible values    | **AUTHORIZATION, PURCHASE** |

------

**access_code**<sup> alphanumeric</sup>

| Attribute Features | Description         |
| ------------------ | ------------------- |
| Type               | access code         |
| Maximum length     | 20                  |
| Example            | **zx0IPmPy5jp1vAz** |

------

**merchant_identifier** <sup>alphanumeric</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The ID of the Merchant. |
| Maximum length     | 20                      |
| Example            | **CycHZxVj**            |

------

**merchant_reference** <sup>alphanumeric</sup>

| Attribute Features | Description                         |
| ------------------ | ----------------------------------- |
| Type               | The Merchant’s unique order number. |
| Maximum length     | 40                                  |
| Example            | **XYZ9239-yu898**                   |

------

**amount** <sup>numeric</sup>

| Attribute Features | Description                     |
| ------------------ | ------------------------------- |
| Type               | The transaction’s amount.<br /> |
| Maximum length     | 10                              |
| Example            | **10000**                       |

------

**currency**<sup> string</sup>

| Attribute Features | Description                                             |
| ------------------ | ------------------------------------------------------- |
| Type               | The currency of the transaction’s amount in ISO code 3. |
| Maximum length     | 3                                                       |
| Example            | **AED**                                                 |

------

**language** <sup>string</sup>

| Attribute Features       | Description                              |
| ------------------------ | ---------------------------------------- |
| Type                     | The checkout page and messages language. |
| Maximum length           | 2                                        |
| Possible/Expected values | **en/ar**                                |

------

**customer_email** <sup>alphanumeric</sup>

| Attribute Features | Description              |
| ------------------ | ------------------------ |
| Type               | The customer's email     |
| Maximum length     | 254                      |
| Example            | **customer1@domain.com** |

------

**customer_ip** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | It holds the customer’s IP address.<br /> *We support IPv4 and IPv6. |
| Maximum length     | 45                                                           |
| Example            | **IPv4 → 192.178.1.10**<br />**IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf** |

------

**token_name** <sup>alphanumeric</sup>

| Attribute Features | Description                                       |
| ------------------ | ------------------------------------------------- |
| Type               | The Token received from the Tokenization process. |
| Maximum length     | 100                                               |
| Example            | **Op9Vmp**                                        |

------

**signature**<sup> hash</sup>

| Attribute Features | Description                                      |
| ------------------ | ------------------------------------------------ |
| Type               | A string hashed using the Secure Hash Algorithm. |
| Maximum length     | 200                                              |
| Example            | **7cad05f0212ed933c9a5d5dffa31661acf2c827a**     |

------

**payment_option** <sup>string</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | Payment Option                                               |
| Maximum length           | 10                                                           |
| Possible/Expected values | **- MASTERCARD**<br />- **VISA**<br />- **AMEX**<br />- **MADA** (for Purchase operations and eci Ecommerce only) Click here to download [**MADA Branding Document**](https://docs.payfort.com/pdf/mada branding - ecommerce merchant - payment providers.pdf)<br />**- MEEZA** (for Purchase operations and ECOMMERCE eci only) |

------

**eci** <sup>string,</sup>

| Attribute Features       | Description                                          |
| ------------------------ | ---------------------------------------------------- |
| Type                     | Ecommerce indicator.                                 |
| Maximum length           | 16                                                   |
| Possible/Expected values | - **ECOMMERCE**<br />- **MOTO**<br />- **RECCURING** |

------

**order_description** <sup>alphanumeric</sup>

| Attribute Features | Description                            |
| ------------------ | -------------------------------------- |
| Type               | It holds the description of the order. |
| Maximum length     | 150                                    |
| Example            | **iPhone 6-S**                         |

------

**fort_id** <sup>numeric</sup>

| Attribute Features | Description                                          |
| ------------------ | ---------------------------------------------------- |
| Type               | The order’s unique reference returned by our system. |
| Maximum length     | 20                                                   |
| Example            | **149295435400084008**                               |

------

**authorization_code** <sup>alphanumeric</sup>

| Attribute Features | Description                                         |
| ------------------ | --------------------------------------------------- |
| Type               | The authorization code returned from the 3rd party. |
| Maximum length     | 100                                                 |
| Example            | **P1000000000000372136**                            |

------

**response_message** <sup>alphanumeric</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | Message description of the response code. It returns according to the request language. |
| Maximum length           | 150                                                          |
| Possible/Expected values | **Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages)** |

------

**response_code** <sup>numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html#messages). |
| Maximum length     | 5                                                            |
| Example            | **20064**                                                    |

------

**customer_name** <sup>string</sup>

| Attribute Features | Description         |
| ------------------ | ------------------- |
| Type               | The Customer’s name |
| Maximum length     | 40                  |
| Example            | **John Smith**      |

------

**merchant_extra** <sup>alphanumeric, </sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 999                                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra1** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra2** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Example            | **John Smith**                                               |

**merchant_extra3** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra4** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Example            | **John Smith**                                               |

------

**merchant_extra5** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | Extra data sent by merchant. <br />Will be received and sent back as received. <br />Will not be displayed in any report. |
| Maximum length     | 250                                                          |
| Example            | **John Smith**                                               |

------

**expiry_date**<sup> numeric</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The card’s expiry date. |
| Maximum length     | 4                       |
| Example            | **2105**                |

------

**card_number** <sup>numeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The masked credit card’s number. <br />Only the MEEZA payment option takes19 digits card number.<br />*AMEX payment option takes 15 digits card number.*<br />Otherwise, they take 16 digits card number. |
| Maximum length     | 19                                                           |
| Example            | 400555********0001                                           |

------

**status**<sup> numeric</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | A two-digit numeric value that indicates the status of the transaction. |
| Maximum length           | 2                                                            |
| Possible/Expected values | Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html#statuses) |

------

**card_holder_name** <sup>string</sup>

| Attribute Features | Description           |
| ------------------ | --------------------- |
| Type               | The card holder name. |
| Maximum length     | 50                    |
| Example            | **John Smith**        |

------

**3ds_url** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The URL where the Merchant redirects a customer whose card is 3-D Secure for authentication. |
| Maximum length     | 300                                                          |
| Example            | **http://www.3dsecure.com**                                  |

------

**remember_me** <sup>string</sup>

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | This parameter provides you with an indication to whether to save this token for the user based on the user selection. |
| Maximum length           | 3                                                            |
| Possible/Expected values | **-Yes**<br />**-No**                                        |

------

**phone_number**<sup> alphanumeric</sup>

| Attribute Features | Description                  |
| ------------------ | ---------------------------- |
| Type               | The customer’s phone number. |
| Maximum length     | 19                           |
| Example            | **00962797219966**           |

------

**settlement_reference** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The Merchant submits this value to the FORT. The value is then passed to the acquiring bank and displayed to the merchant in the Acquirer settlement file. |
| Maximum length     | 34                                                           |
| Example            | **XYZ9239-yu898**                                            |

 ***Note*** - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.

------

## How to add the Tokenization service on the Integration Page channel?

The Tokenization service is applicable to be integrated through the Merchant Page Channel through the below steps:
**1.** The Customer processes the first PURCHASE/ AUTHORIZATION payment successfully.
**2.** The Merchant will receive a token_name in the response. This token_name should be considered as a permanent token name, and it can be used in the future customer’s payments by submitting the token_name in the next PURCHASE/ AUTHORIZATION payment with card_security_code parameter.
**3.** No need to open the Merchant Page to fill all the card details again in the next checkouts.

If the Customer wants to update/ delete his card, you should check [Update Token](https://docs.payfort.com/docs/api/build/index.html#update-token-service) section.

 ***Note***
Please refer to section [FORT Tokenization Service](https://docs.payfort.com/docs/api/build/index.html#fort-tokenization-service) for more details about the token name parameter.

------

## Integration Page Customization

**This is a list with all customizable CSS classes on the basic merchant page:**

- The **`Wrapper`** class: responsible for the total width of the form container and the background.
- The **`Container`** class: responsible for the form’s shape and width.
- The **`Popover`** class: responsible for the error messages.
- The **`Half-container`** class: used to merge the date and CVV fields into one block if needed.
- The **`Input`** class: is the container of each single input field.
- The **`Pay`** class: responsible for the submit button.
- The **`Visa/ MasterCard`** classes: used to change the color of the Visa/ MasterCard colors.

 ***Note*** - You can always create multiple theme files that will enable you to switch freely and easily between them when necessary.

 ***Note***- “Theme” files can be uploaded from the back-office using the Payment Page template screen.

