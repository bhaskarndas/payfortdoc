# iOS SDK Operations

------

**command**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/ expected values            | Description                                 |
| -------------- | ------------------------------------ | ------------------------------------------- |
| 20             | <mark>AUTHORIZATION, PURCHASE</mark> | A command for payFORT server to understand. |

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

**customer_email**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example              | Special characters     | Description           |
| -------------- | -------------------- | ---------------------- | --------------------- |
| 254            | customer1@domain.com | <mark>_ - . @ +</mark> | The customer’s email. |

------

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**token_name**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example | Special characters   | Description                                       |
| -------------- | ------- | -------------------- | ------------------------------------------------- |
| 100            | Op9Vmp  | <mark>. @ - _</mark> | The Token received from the Tokenization process. |

------

**sdk_token**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example | Description                                       |
| -------------- | ------- | ------------------------------------------------- |
| 100            | Dwp78q3 | An SDK Token to enable using the FORT Mobile SDK. |

------





**payment_option**<sup>(String, optional)</sup>

| Maximum Length | Possible/ expected values                                    | Description     |
| -------------- | ------------------------------------------------------------ | --------------- |
| 10             | \- MASTERCARD<br/>\- VISA<br/>\- AMEX<br/>\- SADAD (for Purchase operations only)<br/>\- NAPS (for Purchase operations only)<br/>\- KNET(for Purchase operations only)<br/>\- MADA (for Purchase operations and eci Ecommerce only) Click here to download [MADA Branding Document](https://docs.payfort.com/pdf/mada branding - ecommerce merchant - payment providers.pdf)<br/>\- MEEZA (for Purchase operations and ECOMMERCE eci only) | Payment option. |

------



**eci**<sup>(String, optional)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 16             | -ECOMMERCE<br/>\- MOTO    | E-commerce indicator.<br> *MOTO and E-commerce indicator clickable in VISA, MASTERCARD and AMEX. |

------

**order_description**<sup>(Alphanumeric, optional)</sup>

| Maximum Length | Example    |                                          | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |

------

**customer_ip**<sup>(Alphanumeric, optional)</sup>

| Maximum Length | Example                                                      | Special Characters | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------ | ------------------------------------------------------------ |
| 45             | IPv4 → 192.178.1.10<br/>IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf | <mark>. :</mark>   | It holds the customer’s IP address. <br>*We support IPv4 and IPv6 as shown in the example. |

------

**customer_name**<sup>(String, optional)</sup>

| Maximum Length | Example    | Special Characters                   | Description          |
| -------------- | ---------- | ------------------------------------ | -------------------- |
| 40             | John Smith | <mark>_ \ / - . `' `**Space**</mark> | The customer’s name. |

------

**merchant_extra**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 999            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra1**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra2**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra3**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra4**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra5**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra5**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**remember_me**<sup>(alpha, optional)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 2              | <mark>-YES<br> -No</mark> | This parameter provides you with an indication to whether to save this token for the user based on the user selection. |

------

**phone_number**<sup>(numeric, optional)</sup>

| Maximum Length | Example        | Special Characters             | Description                  |
| -------------- | -------------- | ------------------------------ | ---------------------------- |
| 19             | 00962797219966 | <mark>+ - ( ) **Space**</mark> | The customer’s phone number. |

------

**settlement_reference**<sup>(alphanumeric, optional)</sup>

| Maximum Length | Example        | Special Characters  | Description                                                  |
| -------------- | -------------- | ------------------- | ------------------------------------------------------------ |
| 34             | 00962797219966 | <mark>\- _ .</mark> | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. |

------



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

### SDK Operations response

------

**command**<sup>(String)</sup>

| Maximum Length | Possible/ expected values            | Description                                 |
| -------------- | ------------------------------------ | ------------------------------------------- |
| 20             | <mark>AUTHORIZATION, PURCHASE</mark> | A command for payFORT server to understand. |

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

**customer_email**<sup>(alphanumeric)</sup>

| Maximum Length | Example              | Special characters     | Description           |
| -------------- | -------------------- | ---------------------- | --------------------- |
| 254            | customer1@domain.com | <mark>_ - . @ +</mark> | The customer’s email. |

------

**fort_id**<sup>(alphanumeric)</sup>

| Maximum Length | Example            | Description                                          |
| -------------- | ------------------ | ---------------------------------------------------- |
| 20             | 149295435400084008 | The order’s unique reference returned by our system. |

------

**sdk_token**<sup>(alphanumeric)</sup>

| Maximum Length | Example | Description                                       |
| -------------- | ------- | ------------------------------------------------- |
| 100            | Dwp78q3 | An SDK Token to enable using the FORT Mobile SDK. |

------

**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**token_name**<sup>(alphanumeric)</sup>

| Maximum Length | Example | Special characters   | Description                                       |
| -------------- | ------- | -------------------- | ------------------------------------------------- |
| 100            | Op9Vmp  | <mark>. @ - _</mark> | The Token received from the Tokenization process. |

------

**payment_option**<sup>(String)</sup>

| Maximum Length | Possible/ expected values                                    | Description     |
| -------------- | ------------------------------------------------------------ | --------------- |
| 10             | \- MASTERCARD<br/>\- VISA<br/>\- AMEX<br/>\- SADAD (for Purchase operations only)<br/>\- NAPS (for Purchase operations only)<br/>\- KNET(for Purchase operations only)<br/>\- MADA (for Purchase operations and eci Ecommerce only) Click here to download [MADA Branding Document](https://docs.payfort.com/pdf/mada branding - ecommerce merchant - payment providers.pdf)<br/>\- MEEZA (for Purchase operations and ECOMMERCE eci only) | Payment option. |

------



**eci**<sup>(String)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 16             | -ECOMMERCE<br/>\- MOTO    | E-commerce indicator.<br> *MOTO and E-commerce indicator clickable in VISA, MASTERCARD and AMEX. |

------

**authorization_code**<sup>(alphanumeric)</sup>

| Maximum Length | Example              | Description                                         |
| -------------- | -------------------- | --------------------------------------------------- |
| 100            | P1000000000000372136 | The authorization code returned from the 3rd party. |

------

**order_description**<sup>(Alphanumeric)</sup>

| Maximum Length | Example    | Special Characters                       | Description                            |
| -------------- | ---------- | ---------------------------------------- | -------------------------------------- |
| 150            | iPhone 6-S | <mark>`' `/ . _ - # : $ **Space**</mark> | It holds the description of the order. |

------

**response_message**<sup>(Alphanumeric)</sup>

| Maximum Length | Possible/Expected values                                | Description                                                  |
| -------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 150            | Please refer to section [messages](transactioncodes.md) | The message description of the response code; it returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Example | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| 5              | 20064   | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). |

------



**customer_ip**<sup>(Alphanumeric)</sup>

| Maximum Length | Example                                                      | Special Characters | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------ | ------------------------------------------------------------ |
| 45             | IPv4 → 192.178.1.10<br/>IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf | <mark>. :</mark>   | It holds the customer’s IP address. <br>*We support IPv4 and IPv6 as shown in the example. |

------

**customer_name**<sup>(String)</sup>

| Maximum Length | Example    | Special Characters                   | Description          |
| -------------- | ---------- | ------------------------------------ | -------------------- |
| 40             | John Smith | <mark>_ \ / - . `' `**Space**</mark> | The customer’s name. |

------

**expiry_date**<sup>(numeric)</sup>

| Maximum Length | Example | Description             |
| -------------- | ------- | ----------------------- |
| 4              | 2105    | The card’s expiry date. |

------

**card_number**<sup>(numeric)</sup>

| Maximum Length | Example           | Description                                                  |
| -------------- | ----------------- | ------------------------------------------------------------ |
| 16             | *400555******0001 | The masked credit card’s number. *Only the MEEZA payment option takes 19 digits card number.<br/>\*AMEX payment option takes 15 digits card number.<br/>\*Otherwise, they take 16 digits card number.* |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/Expected values                                | Description                                                  |
| -------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](transactioncodes.md) | A two-digit numeric value that indicates the status of the transaction. |

------

**merchant_extra**<sup>(alphanumeric)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 999            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra1**<sup>(alphanumeric)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra2**<sup>(alphanumeric)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra3**<sup>(alphanumeric)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra4**<sup>(alphanumeric)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra5**<sup>(alphanumeric)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**merchant_extra5**<sup>(alphanumeric)</sup>

| Maximum Length | Example    | Special Characters             | Description                                                  |
| -------------- | ---------- | ------------------------------ | ------------------------------------------------------------ |
| 250            | John Smith | <mark>. ; / _ - , `' `@</mark> | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |

------

**phone_number**<sup>(numeric)</sup>

| Maximum Length | Example        | Special Characters             | Description                  |
| -------------- | -------------- | ------------------------------ | ---------------------------- |
| 19             | 00962797219966 | <mark>+ - ( ) **Space**</mark> | The customer’s phone number. |

------

**settlement_reference**<sup>(alphanumeric)</sup>

| Maximum Length | Example        | Special Characters  | Description                                                  |
| -------------- | -------------- | ------------------- | ------------------------------------------------------------ |
| 34             | 00962797219966 | <mark>\- _ .</mark> | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. |

------



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>