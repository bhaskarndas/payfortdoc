This page describe the request parameters that you are required to send through your payment processing page and the response parameters that will be sent back by the PayFORT server. The page describes the request parameters for both Merchant Page&nbsp;[<i class="fa fa-anchor"></i>](#merchant-page-request-parameters) and Merchant Page 2&nbsp;[<i class="fa fa-anchor"></i>](#merchant-page-2-request-parameters) integrations and <mark><em>response</em></mark> for Merchant Page&nbsp;[<i class="fa fa-anchor"></i>](#merchant-page-response) and Merchant Page 2&nbsp;[<i class="fa fa-anchor"></i>](#merchant-page-2-response).



## Merchant Page Request Parameters

------

**submission type** 

HTTPs Form Post Request

------

**List of Request Parameters**



**service_command**<sup>(String, mandatory)</sup>

| Maximum Length | Possible Value | Description                                                  |
| -------------- | -------------- | ------------------------------------------------------------ |
| 20             | TOKENIZATION   | Command for server to understand what type of service it requires to provide. |

------

**access_code**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example         | Description                                   |
| -------------- | --------------- | --------------------------------------------- |
| 20             | zx0IPmPy5jp1vAz | The access code generated in the back office. |

------

**merchant_identifier**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example  | Description                                                  |
| -------------- | -------- | ------------------------------------------------------------ |
| 20             | CycHZxVj | The ID of the Merchant which can be found in the back office |

------

**merchant_reference**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example       | Special character  | Description                         |
| -------------- | ------------- | ------------------ | ----------------------------------- |
| 40             | XYZ9239-yu898 | <mark>- _ .</mark> | The Merchant’s unique order number. |

------

**language**<sup>(String, mandatory)</sup>

| Maximum Length | Possible Values    | Description                                                  |
| -------------- | ------------------ | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark> | The checkout page and messages language where en stands for english and ar for arabic. |

------

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**token_name**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example | Special character    | Description                                       |
| -------------- | ------- | -------------------- | ------------------------------------------------- |
| 100            | Op9Vmp  | <mark>. @ - _</mark> | The token received from the Tokenization process. |

------

**return_url**<sup>(alphanumeric, optional)</sup>

| Length | Example                 | Special character                  | Description                                                  |
| ------ | ----------------------- | ---------------------------------- | ------------------------------------------------------------ |
| 400    | http://www.merchant.com | <mark>$ ! = ? # & - _ / : .</mark> | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |

------

## Merchant Page Response

------

List of Response Parameters that would be sent back by the PayFORT Server as a JSON format



**service_command**<sup>(String)</sup>

| Maximum Length | Possible/Expected Value | Description      |
| -------------- | ----------------------- | ---------------- |
| 20             | TOKENIZATION            | service command. |

------

**access_code**<sup>(alphanumeric)</sup>

| Maximum Length | Example              | Description            |
| -------------- | -------------------- | ---------------------- |
| 20             | zx0IPmPy5jp1vAz8Kpg7 | access code generated. |

------

**merchant_identifier**<sup>(alphanumeric)</sup>

| Maximum Length | Example  | Description             |
| -------------- | -------- | ----------------------- |
| 20             | CycHZxVj | The ID of the Merchant. |

------

**merchant_reference**<sup>(alphanumeric)</sup>

| Maximum Length | Example       | Special character | Description                         |
| -------------- | ------------- | ----------------- | ----------------------------------- |
| 40             | XYZ9239-yu898 | \- _ .            | The Merchant’s unique order number. |

------

**language**<sup>(String)</sup>

| Maximum Length | Possible/Expected Values | Description                                                  |
| -------------- | ------------------------ | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark>       | The checkout page and messages language where en stands for english and ar for arabic. |

------

**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**token_name**<sup>(alphanumeric)</sup>

| Maximum Length | Example | Special character    | Description                                       |
| -------------- | ------- | -------------------- | ------------------------------------------------- |
| 100            | Op9Vmp  | <mark>. @ - _</mark> | The token received from the Tokenization process. |

------

**expiry_date**<sup>(numeric)</sup>

| Maximum Length | Example | Description             |
| -------------- | ------- | ----------------------- |
| 4              | 2105    | The card’s expiry date. |

------

**card_number**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 19             | 2105    | The masked credit card’s number.<br/>*Only the MEEZA payment option takes 19 digits card number.<br/>\*AMEX payment option takes 15 digits card number.<br/>\*Otherwise, they take 16 digits card number.<br/>Example: 400555******0001 |

------

**response_message**<sup>(alphanumeric)</sup>

| Maximum Length | Possible/Expected Values                                     | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 150            | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages) | Message description of the response code. It returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 5              | 20064   | Response Code carries the value of PayFORT system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html#messages). |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/Expected Value                                      | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html#statuses) | A two-digit numeric value that indicates the status of the transaction. |

------

**card_bin**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 8              | 478773  | The first 6 digits of the card number.<br>*If the card number for MEEZA was of length 19 then the card bin will be the first 8 digits. |

------

**return_url**<sup>(alphanumeric, optional)</sup>

| Length | Example                 | Special character                  | Description                                                  |
| ------ | ----------------------- | ---------------------------------- | ------------------------------------------------------------ |
| 400    | http://www.merchant.com | <mark>$ ! = ? # & - _ / : .</mark> | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |

------

## Merchant Page 2 Request Parameters

------

**submission type** 

HTTPs Form Post Request

------

**List of Request Parameters**



**service_command**<sup>(String, mandatory)</sup>

| Maximum Length | Possible Value | Description                                                  |
| -------------- | -------------- | ------------------------------------------------------------ |
| 20             | TOKENIZATION   | Command for server to understand what type of service it requires to provide. |

------

**access_code**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example         | Description                                   |
| -------------- | --------------- | --------------------------------------------- |
| 20             | zx0IPmPy5jp1vAz | The access code generated in the back office. |

------

**merchant_identifier**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example  | Description                                                  |
| -------------- | -------- | ------------------------------------------------------------ |
| 20             | CycHZxVj | The ID of the Merchant which can be found in the back office |

------

**merchant_reference**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example       | Special character | Description                         |
| -------------- | ------------- | ----------------- | ----------------------------------- |
| 40             | XYZ9239-yu898 | \- _ .            | The Merchant’s unique order number. |

------

**language**<sup>(String, mandatory)</sup>

| Maximum Length | Possible Values    | Description                                                  |
| -------------- | ------------------ | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark> | The checkout page and messages language where en stands for english and ar for arabic. |

------

**expiry_date**<sup>(numeric, mandatory)</sup>

| Maximum Length | Example | Description             |
| -------------- | ------- | ----------------------- |
| 4              | 2105    | The card’s expiry date. |

------

**card_number**<sup>(numeric, mandatory)</sup>

| Maximum Length | Example          | Description                                                  |
| -------------- | ---------------- | ------------------------------------------------------------ |
| 19             | 4005550000000001 | *Only the MEEZA payment option takes 19 digits card number.<br/>*AMEX payment option takes 15 digits card number.<br/>*Otherwise, they take 16 digits card number. |

------

**card_security_code**<sup>(numeric, mandatory)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 4              | 123     | A security code for the card. <br>* Only AMEX accepts card security code of 4 digits. |

------

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**token_name**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example | Special character    | Description                                       |
| -------------- | ------- | -------------------- | ------------------------------------------------- |
| 100            | Op9Vmp  | <mark>. @ - _</mark> | The token received from the Tokenization process. |

------

**card_holder_name**<sup>(String, optional)</sup>

| Maximum Length | Example    | Special character  | Description           |
| -------------- | ---------- | ------------------ | --------------------- |
| 50             | John Smith | <mark>' - .</mark> | The card holder name. |

------

**remember_me**<sup>(String, optional)</sup>

| Maximum Length | Possible/Expected values | Special character  | Description           |
| -------------- | ------------------------ | ------------------ | --------------------- |
| 50             | -YES<br>-NO              | <mark>' - .</mark> | The card holder name. |

------

**return_url**<sup>(alphanumeric, optional)</sup>

| Length | Example                 | Special character                  | Description                                                  |
| ------ | ----------------------- | ---------------------------------- | ------------------------------------------------------------ |
| 400    | http://www.merchant.com | <mark>$ ! = ? # & - _ / : .</mark> | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i> Please don’t include the following parameters in calculating the signature if you are using Merchant Page 2.0 tokenization request:
card_security_code, card number, expiry_date, card_holder_name, remember_me.</div>
------

## Merchant Page 2 Response

------

List of Response Parameters that would be sent back by the PayFORT Server as a JSON format



**service_command**<sup>(String)</sup>

| Maximum Length | Possible/Expected Value | Description      |
| -------------- | ----------------------- | ---------------- |
| 20             | TOKENIZATION            | service command. |

------

**access_code**<sup>(alphanumeric)</sup>

| Maximum Length | Example              | Description            |
| -------------- | -------------------- | ---------------------- |
| 20             | zx0IPmPy5jp1vAz8Kpg7 | access code generated. |

------

**merchant_identifier**<sup>(alphanumeric)</sup>

| Maximum Length | Example  | Description             |
| -------------- | -------- | ----------------------- |
| 20             | CycHZxVj | The ID of the Merchant. |

------

**merchant_reference**<sup>(alphanumeric)</sup>

| Maximum Length | Example       | Special character | Description                         |
| -------------- | ------------- | ----------------- | ----------------------------------- |
| 40             | XYZ9239-yu898 | \- _ .            | The Merchant’s unique order number. |

------

**language**<sup>(String)</sup>

| Maximum Length | Possible/Expected Values | Description                                                  |
| -------------- | ------------------------ | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark>       | The checkout page and messages language where en stands for english and ar for arabic. |

------

**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**token_name**<sup>(alphanumeric)</sup>

| Maximum Length | Example | Special character    | Description                                       |
| -------------- | ------- | -------------------- | ------------------------------------------------- |
| 100            | Op9Vmp  | <mark>. @ - _</mark> | The token received from the Tokenization process. |

------

**expiry_date**<sup>(numeric)</sup>

| Maximum Length | Example | Description             |
| -------------- | ------- | ----------------------- |
| 4              | 2105    | The card’s expiry date. |

------

**card_number**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 19             | 2105    | The masked credit card’s number.<br/>*Only the MEEZA payment option takes 19 digits card number.<br/>\*AMEX payment option takes 15 digits card number.<br/>\*Otherwise, they take 16 digits card number.<br/>Example: 400555******0001 |

------

**response_message**<sup>(alphanumeric)</sup>

| Maximum Length | Possible/Expected Values                                     | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 150            | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html#messages) | Message description of the response code. It returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 5              | 20064   | Response Code carries the value of PayFORT system’s response. <br>*The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html#messages). |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/Expected Value                                      | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html#statuses) | A two-digit numeric value that indicates the status of the transaction. |

------

**card_bin**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 8              | 478773  | The first 6 digits of the card number.*If the card number for MEEZA was of length 19 then the card bin will be the first 8 digits. |

------

**card_holder_name**<sup>(String)</sup>

| Maximum Length | Example    | Description           |
| -------------- | ---------- | --------------------- |
| 50             | John Smith | The card holder name. |

------

**remember_me**<sup>(String)</sup>

| Maximum Length | Possible/Expected values | Description                                                  |
| -------------- | ------------------------ | ------------------------------------------------------------ |
| 3              | \- YES,<br>- NO          | This parameter provides you with an indication to whether to save this token for the user based on the user selection. |

------

**return_url**<sup>(alphanumeric, optional)</sup>

| Length | Example                 | Special character                  | Description                                                  |
| ------ | ----------------------- | ---------------------------------- | ------------------------------------------------------------ |
| 400    | http://www.merchant.com | <mark>$ ! = ? # & - _ / : .</mark> | The URL of the Merchant’s page to be displayed to the customer when the order is processed. |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.</div>

------

