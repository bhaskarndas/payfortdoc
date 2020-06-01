# Maintenance Operations Parameters

------



## Capture Payment  Request Parameters

------

**command**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/ expected values | Description                                 |
| -------------- | ------------------------- | ------------------------------------------- |
| 20             | <mark>CAPTURE</mark>      | A command for payFORT server to understand. |

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

**fort_id**<sup>(numeric, optional)</sup>

| Maximum Length | Example            | Description                                          |
| -------------- | ------------------ | ---------------------------------------------------- |
| 20             | 149295435400084008 | The order’s unique reference returned by our system. |

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

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |



------

**order_description**<sup>(Alphanumeric, optional)</sup>

| Maximum Length | Example    |                                          | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |

------





<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info">Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</i></div>
<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info">You can send “merchant_reference” and/ or “fort_id” in the CAPTURE request.</i></div>

## Capture Payment Response

------



**command**<sup>(String)</sup>

| Maximum Length | Possible/ expected values | Description                                 |
| -------------- | ------------------------- | ------------------------------------------- |
| 20             | <mark>CAPTURE</mark>      | A command for payFORT server to understand. |

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

| Maximum Length | Example | Description                    |
| -------------- | ------- | ------------------------------ |
| 10             | 10000   | The transaction’s amount. <br> |

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

**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------



**order_description**<sup>(Alphanumeric)</sup>

| Maximum Length | Example    |                                          | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |

------

**fort_id**<sup>(numeric)</sup>

| Maximum Length | Example            | Description                                          |
| -------------- | ------------------ | ---------------------------------------------------- |
| 20             | 149295435400084008 | The order’s unique reference returned by our system. |

------

**response_message**<sup>(alphanumeric)</sup>

| Maximum Length | Possible/ expected values                                    | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 150            | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages) | The message description of the response code; it returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 5              | 20064   | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](transactioncodes.md), and the last 3 digits represent the response [messages](transactioncodes.md). |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/ expected values                               | Description                                                  |
| -------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](transactioncodes.md) | A two-digit numeric value that indicates the status of the transaction. |

------

------

<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info"></i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones.</div>

Please refer to section [Transactions Response Codes](transactioncodes.md) for more details about operation’s statuses

------

## Void Payment  Request Parameters

**command**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/ expected values       | Description                                 |
| -------------- | ------------------------------- | ------------------------------------------- |
| 20             | <mark>VOID_AUTHORIZATION</mark> | A command for payFORT server to understand. |

------

**fort_id**<sup>(numeric, optional)</sup>

| Maximum Length | Example            | Description                                          |
| -------------- | ------------------ | ---------------------------------------------------- |
| 20             | 149295435400084008 | The order’s unique reference returned by our system. |

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

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------



**order_description**<sup>(Alphanumeric, optional)</sup>

| Maximum Length | Example    |                                          | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |

------

<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info">You can send “merchant_reference” and/ or “fort_id” in the VOID_AUTHORIZATION request.</i></div>



## Void Payment Response

------



**command**<sup>(String)</sup>

| Maximum Length | Possible/ expected values       | Description                                 |
| -------------- | ------------------------------- | ------------------------------------------- |
| 20             | <mark>VOID_AUTHORIZATION</mark> | A command for payFORT server to understand. |

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

**language**<sup>(String)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark>        | The checkout page and messages language where en is for english and ar for Arabic |



------

**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |



------

**order_description**<sup>(Alphanumeric)</sup>

| Maximum Length | Example    |                                          | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |



------

**fort_id**<sup>(numeric)</sup>

| Maximum Length | Example            | Description                                          |
| -------------- | ------------------ | ---------------------------------------------------- |
| 20             | 149295435400084008 | The order’s unique reference returned by our system. |

------

**response_message**<sup>(alphanumeric)</sup>

| Maximum Length | Possible/ expected values                                    | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 150            | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages) | The message description of the response code; it returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 5              | 20064   | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](transactioncodes.md), and the last 3 digits represent the response [messages](transactioncodes.md). |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/ expected values                               | Description                                                  |
| -------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](transactioncodes.md) | A two-digit numeric value that indicates the status of the transaction. |



------

<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info"></i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones.</div>





Please refer to section [Transactions Response Codes](transactioncodes.md) for more details about operation’s statuses

------

## Refund Payment Request Parameters

**command**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/ expected values | Description                                 |
| -------------- | ------------------------- | ------------------------------------------- |
| 20             | <mark>REFUND</mark>       | A command for payFORT server to understand. |

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

**fort_id**<sup>(numeric, optional)</sup>

| Maximum Length | Example            | Description                                          |
| -------------- | ------------------ | ---------------------------------------------------- |
| 20             | 149295435400084008 | The order’s unique reference returned by our system. |

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

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**order_description**<sup>(Alphanumeric, optional)</sup>

| Maximum Length | Example    |                                          | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |



------



**maintenance_reference**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example     | Special Characters  | Description                                                  |
| -------------- | ----------- | ------------------- | ------------------------------------------------------------ |
| 200            | customer123 | <mark>\- _ .</mark> | The Refund’s unique order number. <br/>* You will be able to retry on the refund request using the same maintenance reference if the refund transaction was declined. |

------



<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info">Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</i></div>
<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info">You can send “merchant_reference” and/ or “fort_id” in the REFUND request.</i></div>


## Refund Payment Response

------



**command**<sup>(String)</sup>

| Maximum Length | Possible/ expected values            | Description                                 |
| -------------- | ------------------------------------ | ------------------------------------------- |
| 20             | <mark>AUTHORIZATION, PURCHASE</mark> | A command for payFORT server to understand. |

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

| Maximum Length | Example | Description                    |
| -------------- | ------- | ------------------------------ |
| 10             | 10000   | The transaction’s amount. <br> |

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



**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**order_description**<sup>(Alphanumeric)</sup>

| Maximum Length | Example    |                                          | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |

------

**maintenance_reference**<sup>(alphanumeric)</sup>

| Maximum Length | Example     | Description                                                  |
| -------------- | ----------- | ------------------------------------------------------------ |
| 200            | customer123 | The Refund’s unique order number. <br/>* You will be able to retry on the refund request using the same maintenance reference if the refund transaction was declined. |

------



**fort_id**<sup>(numeric)</sup>

| Maximum Length | Example            | Description                                          |
| -------------- | ------------------ | ---------------------------------------------------- |
| 20             | 149295435400084008 | The order’s unique reference returned by our system. |



------

**response_message**<sup>(alphanumeric)</sup>

| Maximum Length | Possible/ expected values                                    | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 150            | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages) | The message description of the response code; it returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 5              | 20064   | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](transactioncodes.md), and the last 3 digits represent the response [messages](transactioncodes.md). |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/ expected values                               | Description                                                  |
| -------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](transactioncodes.md) | A two-digit numeric value that indicates the status of the transaction. |



------

<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info"></i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones.</div>

Please refer to section [Transactions Response Codes](transactioncodes.md) for more details about operation’s statuses

------

