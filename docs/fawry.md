[TOC]



# Fawry Payment

------

Start accepting payments using Fawry, a favorite payment method in Egypt.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>To start accepting Fawry payments, please contact your customer success manager.</div>

##  Request a Fawry payment

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

