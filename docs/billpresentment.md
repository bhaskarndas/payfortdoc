# Cash Payment

------

Accept cash payments using the same integration process you use for card payments. Through this service your customers can pay to any authorized PayFORT's payment partners for their order by showing a unique bill number that is displayed by your site or sent to them by you. 

This service allows you to generate a unique bill numbers for your Customer’s orders using the PayFORT API. 

------

## Endpoints

------

**Sandbox**

```http
POST https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

**Live**

```http
POST https://paymentservices.PayFort.com/FortAPI/paymentApi
```

------

## Supported Schemes

------

**Fawry**

| Features                    | Details |
| --------------------------- | ------- |
| Countries supported         | Egypt   |
| Type                        | voucher |
| Clearing and Settlement     | Instant |
| Processing currencies       | EGP     |
| Default settlement currency | USD     |
| Refunds                     | Yes     |
| Partial Refunds             | Yes     |

 

Placeholder: If more than one scheme is supported then toggable tab is required which will contain a table for each tab similar to the above.



# Fawry Payment

------

Start accepting payments using Fawry, a favorite payment method in Egypt.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>To start accepting Fawry payments, please contact your customer success manager.</div>

##  Request a Fawry payment

------



### The Request

Use the details below to set up your request.

#### Endpoints

**Live**

```http
POST  https://paymentservices.PayFort.com/FortAPI/paymentApi
```

**Sandbox**

```http
POST  https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

------

#### Body parameters

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>The table below describes the minimum recommended fields. You can find the full list, as well as complete request and response examples, in our <a href="https://docs.payfort.com/docs/api/build/index.html?java#bill-presentment-request">API reference</a></div>

**service_command**<sup>(String,mandatory,)</sup>

| Maximum Length | Possible/ expected values     | Special Characters | Description                                 |
| -------------- | ----------------------------- | ------------------ | ------------------------------------------- |
| 20             | <mark>BILL_PRESENTMENT</mark> | <mark>_</mark>     | A command for payFORT server to understand. |

------

**access_code**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example              | Description                                              |
| -------------- | -------------------- | -------------------------------------------------------- |
| 20             | zx0IPmPy5jp1vAz8Kpg7 | Merchant access code that can be found in the backoffice |

------

**merchant_identifier**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example  | Description                                     |
| -------------- | -------- | ----------------------------------------------- |
| 20             | CycHZxVj | Merchant ID that can be found in the backoffice |

------

**merchant_reference**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example       | Special Characters  | Description                         |
| -------------- | ------------- | ------------------- | ----------------------------------- |
| 40             | XYZ9239-yu898 | <mark>\- _ .</mark> | The Merchant’s unique order number. |

------

**amount**<sup>(numeric, mandatory)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 10             | 10000   | The transaction’s amount. <br>*Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount check the note after this table. |

------

**currency**<sup>(String, mandatory)</sup>

| Maximum Length | Example | Description                                             |
| -------------- | ------- | ------------------------------------------------------- |
| 3              | AED     | The currency of the transaction’s amount in ISO code 3. |

------

**language**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark>        | The checkout page and messages language where en is for english and ar for Arabic |

------

**request_expiry_date**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                   | Special Characters  | Description                                                  |
| -------------- | ------------------------- | ------------------- | ------------------------------------------------------------ |
| 25             | 2017-12-20T15:36:55+03:00 | <mark>\- + :</mark> | The date when the bill expires.<br/>*The merchant will hold the item till the expiry date. If the customer didn’t pay, the holding will be canceled. |

------

**payment_partner**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/Expected values | Special Characters  | Description                                                  |
| -------------- | ------------------------ | ------------------- | ------------------------------------------------------------ |
| 5              | <mark>FAWRY</mark>       | <mark>\- + :</mark> | A financial corporation that generate bills to the customer. |

------

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**customer_name**<sup>(alpha, optional)</sup>

| Maximum Length | Example    | Special Characters                   | Description         |
| -------------- | ---------- | ------------------------------------ | ------------------- |
| 50             | John Smith | <mark>_ \ / - . `' `**Space**</mark> | The customer’s name |

------

**customer_email**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example             | Special Characters     | Description           |
| -------------- | ------------------- | ---------------------- | --------------------- |
| 254            | customer@domain.com | <mark>_ - . @ +</mark> | The customer’s email. |

------

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

#### Response

**service_command**<sup>(String)</sup>

| Maximum Length | Possible/ expected values     | Special Characters | Description                                 |
| -------------- | ----------------------------- | ------------------ | ------------------------------------------- |
| 20             | <mark>BILL_PRESENTMENT</mark> | <mark>_</mark>     | A command for payFORT server to understand. |

------

**access_code**<sup>(alphanumeric)</sup>

| Maximum Length | Example              | Description                                              |
| -------------- | -------------------- | -------------------------------------------------------- |
| 20             | zx0IPmPy5jp1vAz8Kpg7 | Merchant access code that can be found in the backoffice |

------

**merchant_identifier**<sup>(alphanumeric)</sup>

| Maximum Length | Example  | Description                                     |
| -------------- | -------- | ----------------------------------------------- |
| 20             | CycHZxVj | Merchant ID that can be found in the backoffice |

------

**merchant_reference**<sup>(alphanumeric)</sup>

| Maximum Length | Example       | Special Characters  | Description                         |
| -------------- | ------------- | ------------------- | ----------------------------------- |
| 40             | XYZ9239-yu898 | <mark>\- _ .</mark> | The Merchant’s unique order number. |

------

**amount**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 10             | 10000   | The transaction’s amount. <br>*Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount check the note after this table. |

------

**currency**<sup>(String)</sup>

| Maximum Length | Example | Description                                             |
| -------------- | ------- | ------------------------------------------------------- |
| 3              | AED     | The currency of the transaction’s amount in ISO code 3. |

------

**language**<sup>(String)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark>        | The checkout page and messages language where en is for english and ar for Arabic |

------

**bill_number**<sup>(numeric)</sup>

| Maximum Length | Example        | Description                                        |
| -------------- | -------------- | -------------------------------------------------- |
| 14             | 14823285500005 | A unique number generated by PayFort to pay bills. |

------

**request_expiry_date**<sup>(alphanumeric)</sup>

| Maximum Length | Example                   | Special Characters  | Description                                                  |
| -------------- | ------------------------- | ------------------- | ------------------------------------------------------------ |
| 25             | 2017-12-20T15:36:55+03:00 | <mark>\- + :</mark> | The date when the bill expires.<br/>*The merchant will hold the item till the expiry date. If the customer didn’t pay, the holding will be canceled. |

------

**payment_partner**<sup>(String)</sup>

| Maximum Length | Possible/Expected values | Special Characters  | Description                                                  |
| -------------- | ------------------------ | ------------------- | ------------------------------------------------------------ |
| 5              | <mark>FAWRY</mark>       | <mark>\- + :</mark> | A financial corporation that generate bills to the customer. |

------

**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**customer_name**<sup>(alpha)</sup>

| Maximum Length | Example    | Special Characters                   | Description         |
| -------------- | ---------- | ------------------------------------ | ------------------- |
| 50             | John Smith | <mark>_ \ / - . `' `**Space**</mark> | The customer’s name |

------

**customer_email**<sup>(alphanumeric)</sup>

| Maximum Length | Example             | Special Characters     | Description           |
| -------------- | ------------------- | ---------------------- | --------------------- |
| 254            | customer@domain.com | <mark>_ - . @ +</mark> | The customer’s email. |

------

**response_message**<sup>(alphanumeric)</sup>

| Maximum Length | Possible/Expected value                                      | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 150            | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages) | Message description of the response code. It returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 5              | 46000   | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/Expected values                                     | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses) | A two-digit numeric value that indicates the status of the transaction. |

------

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

------

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

------



## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).