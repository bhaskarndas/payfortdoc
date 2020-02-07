[TOC]

# Merchant Page

This type of integration allows the Merchant to develop his own payment form that collects the card details. The card details are sent directly to PayFort and substituted with Token. The Merchant uses the Token created to complete the transaction.

------

## Features

- No Customer redirection.
- No PCI-Compliance needed.
- A replica of your website appearance and your payment flow.

------



## How it works - overview

**1.** The Merchant develops the form that collects the card details (credit card number, expiry date, CVV), and sends the request to PayFort.
**2.** PayFort receives the payment details and returns the response which includes the Token to the Merchant.
**3.** The Merchant use it to complete the [Authorization or Purchase operation](https://docs.payfort.com/docs/api/build/index.html#operations-request).

 ***Note*** - *The Merchant should develop a form that does not send data to his website but directly submits the form to PayFort.*

### Integration Flow

**1.** The Customer begins the checkout process on the Merchant’s website.

**2.** The Merchant displays the form he developed to collect the card’s details. Then the Customer enters the card’s details on the Merchant page.

**3.** PayFort validates the card format.

**4.** PayFort creates a token for the card details and sends it back to the Merchant.

**5.** The Merchant stores the Token and proceeds with the transaction.

**6.** The Merchant sends a payment request along with the Token to PayFort.

**7.** PayFort sends the Merchant the 3-D Secure URL, and response indicating that a check is required:

  **a.** The Merchant redirects the Customer to check his card enrollment.
  **b.** The Customer enters authentication data.
  **c.** 3-D Secure authentication is completed and PayFort receives the authentication results.

 ***Note*** - *In this case, PayFort returns* **status “20: On hold”** *and* **message “064: 3-D Secure check requested”**. *For example, PayFort is waiting for the Merchant to authenticate the Customer.*

**8.** PayFort completes the operation based on the 3-D Secure response and returns the response to the Merchant.

**9.** The payment results are displayed to the Customer.

 ***Note*** -
\- *If the Token is sent by the Merchant, it will be generated with the same name sent by the Merchant.*

### Merchant Page 2.0 URLs

#### Test Environment URLs

https://sbcheckout.payfort.com/FortAPI/paymentPage

#### Production Environment URLs

https://checkout.payfort.com/FortAPI/paymentPage

### Parameters Submission Type

HTTPs Form Post Request

## Merchant Page 2.0 - Request

**Include the following parameters in the Request you will send to PayFort:**

------

**service_command <sup>string,mandatory</sup>**

| Attribute Features | Description  |
| :----------------- | :----------- |
| Type               | Command      |
| Maximum length     | 20           |
| Possible values    | Tokenization |

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
| Possible values    | CycHZxVj                       |

------

**language** <sup>string, mandatory</sup>

| Attribute Features              | Description                              |
| ------------------------------- | ---------------------------------------- |
| Type                            | The checkout page and messages language. |
| Maximum length                  | 2                                        |
| Possible values/Expected values | **en/ar**                                |

------

**expiry_date** <sup>numeric, mandatory</sup>

| Attribute Features | Description             |
| ------------------ | ----------------------- |
| Type               | The card's expiry date. |
| Maximum length     | 4                       |
| Example            | **2105**                |

------

**card_number** <sup>numeric, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The clear credit card’s number.<br/>*Only the MEEZA payment option takes 19 digits card number.<br/>*AMEX payment option takes 15 digits card number.<br/>*Otherwise, they take 16 digits card number. |
| Maximum length     | 19                                                           |
| Example            | **4005550000000001**                                         |

------

**card_security_code** <sup>numeric, mandatory</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | A security code for the card. <br />* Only AMEX accepts card security code of 4 digits. |
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

**card_holder_name** <sup>string, optional</sup>

| Attribute Features | Description           |
| ------------------ | --------------------- |
| Type               | The card holder name. |
| Maximum length     | 50                    |
| Special characters | **`' `- .**           |
| Example            | **John Smith**        |

------

**remember_me** <sup>string, optional</sup>

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

***Note*** - *Please don’t include the following parameters in calculating the signature if you are using Merchant Page 2.0 tokenization request:*
*card_security_code, card number, expiry_date, card_holder_name, remember_me.*



## Merchant Page 2.0 - Response

**The following parameters will be returned in PayFort’s Response:**

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

| Attribute Features       | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Type                     | This parameter provides you with an indication to whether to save this token for the user based on the user selection. |
| Maximum length           | 3                                                            |
| Possible/Expected values | **-Yes**<br />**-No**                                        |

------

**return_url** <sup>alphanumeric</sup>

| Attribute Features | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| Type               | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |
| Maximum length     | 400                                                          |
| Example            | **http://www.merchant.com**                                  |

------

***Note*** - *Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones*.

------



## Merchant Page 2.0 Operations

### Merchant Page 2.0 Operations URLs

**Test Environment URL:**

https://sbpaymentservices.payfort.com/FortAPI/paymentApi

**Production Environment URL:**

https://paymentservices.payfort.com/FortAPI/paymentApi

### Parameters Submission Type

REST POST request using JSON.

### Operations - Request

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

***Note*** : Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.

------

### Operations - Response

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

## How to add the Tokenization service on the Merchant 2.0 Page channel?

The Tokenization service is applicable to be integrated through the Merchant Page 2.0 Channel through the below steps:
**1.** The Customer processes the first PURCHASE/ AUTHORIZATION payment successfully.
**2.** The Merchant will receive a token_name in the response. This token_name should be considered as a permanent token name, and it can be used in the future customer’s payments by submitting the token_name in the next PURCHASE/ AUTHORIZATION payment with card_security_code parameter.
**3.** No need to open the Merchant Page to fill all the card details again in the next checkouts.

If the Customer wants to update/ delete his card, you should check [Update Token](https://docs.payfort.com/docs/api/build/index.html#update-token-service) section.

 ***Note***
Please refer to section [FORT Tokenization Service](https://docs.payfort.com/docs/api/build/index.html#fort-tokenization-service) for more details about the token name parameter.



Was this helpful? Yes No

