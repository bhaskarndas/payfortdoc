# Invoicing (One to One) Request and Response Parameters

------

| **service_command** Alpha Mandatory max: 20            | Command. Possible/ expected values: PAYMENT_LINK Special characters: _ |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| **access_code** Alphanumeric Mandatory max: 20         | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric Mandatory max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
| **merchant_reference** Alphanumeric Mandatory max: 40  | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . |
| **amount** Numeric Mandatory max: 10                   | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. Example: 100 USD=1.00 USD |
| **currency** Alpha Mandatory max: 3                    | The currency of the transaction’s amount in ISO code 3. Example: USD |
| **language** Alpha Mandatory max: 2                    | The invoice and the received messages language. Possible/ expected values: en / ar |
| **customer_email** Alphanumeric Mandatory max: 254     | The customer’s email. Example: customer@domain.com Special characters: _ - . @ + |
| **request_expiry_date** Alphanumeric Mandatory max: 25 | The invoice link expiry date. Example: 2017-12-20T15:36:55+03:00 Special characters: + : - |
| **notification_type** Alpha Mandatory max: 20          | The way the Customer wants to use to get his notification. The Merchant can choose more than one way. * If the Customer chooses NONE with “EMAIL” or “SMS”, then the NONE will be taken as notification type. Possible/ expected values: - SMS - EMAIL - NONE Special characters: , |
| **signature** Alphanumeric Mandatory max: 200          | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?ruby#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
| **link_command** Alphanumeric Optional max: 15         | Link operation to be executed. Possible/ expected values: AUTHORIZATION/ PURCHASE |
| **payment_link_id** Alphanumeric Optional max: 20      | The ID of the generated Invoice payment link. Example: 148708392700020346 Special characters: - _ . |
| **payment_option** Alpha Optional max: 10              | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX - SADAD (for Purchase operations only) - NAPS (for Purchase operations only) - KNET(for Purchase operations only) - MADA (for Purchase operations and eci Ecommerce only) Click here to download [MADA Branding Document](https://docs.payfort.com/pdf/mada branding - ecommerce merchant - payment providers.pdf) - MEEZA (for Purchase operations and ECOMMERCE eci only) |
| **order_description** Alphanumeric Optional max: 150   | It holds the description of the order. Example: iPhone 6-S Special characters: `' `/ . _ - # : $ **Space** |
| **customer_name** Alpha Optional max: 40               | The customer’s name. Example: John Smith Special characters: _ \ / - . `' `**Space** |
| **customer_phone** Numeric Optional max: 19            | The Customer mobile number. It’s mandatory when selecting SMS as notification type. Example: 00962797219966 |
| **return_url** Alphanumeric Optional max: 400          | The URL of the Merchant’s page to be redirected to when the order is processed. Example: http://www.merchant.com Special characters:$ ! = ? # & _ - / : . |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>If the Customer chooses NONE with “EMAIL” or “SMS”, then the NONE will be taken as notification type.</div>

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

## Invoicing Service - Response

**The following parameters will be returned in PayFort’s Response:**

|                                   ATTRIBUTES | Description                                                  |
| -------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha max: 20 | Command. Possible/ expected values: PAYMENT_LINK             |
|         **access_code** Alphanumeric max: 20 | Access code. Possible/ expected Example: zx0IPmPy5jp1vAz     |
| **merchant_identifier** Alphanumeric max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric max: 40 | The Merchant’s unique order number. Example: XYZ2939-yu898   |
|                   **amount** Numeric max: 10 | The transaction’s amount. Example: 100 USD=1.00 USD          |
|                    **currency** Alpha max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|                    **language** Alpha max: 2 | The invoice and received messages language. Possible/ expected values: en / ar |
|     **customer_email** Alphanumeric max: 254 | The customer’s email. Example: customer@domain.com           |
| **request_expiry_date** Alphanumeric max: 25 | The invoice link expiry date. Example: 2017-12-20T15:36:55+03:00 |
|          **notification_type** Alpha max: 20 | The way the Customer wants to use to get his notification. The Merchant can choose more than one way. *If the Customer chooses NONE with “EMAIL” or “SMS”, then the NONE will be taken as notification type. Possible/ expected values: - SMS - EMAIL - NONE |
|          **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?ruby#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|        **link_command** Alphanumeric max: 15 | Link operation to be executed. Possible/ expected values: AUTHORIZATION/ PURCHASE |
|     **payment_link_id** Alphanumeric max: 20 | The ID of the generated Invoice payment link. Example: 148708392700020346 |
|       **payment_link** Alphanumeric max: 150 | The generated invoice link notified to the Customer by one of the notification types, used to complete the payment process. Example: https://checkout.payfort.com/dfc3d762 |
|             **payment_option** Alpha max: 10 | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX - SADAD (for Purchase operations only) - NAPS (for Purchase operations only) - KNET(for Purchase operations only) - MADA (for Purchase operations and eci Ecommerce only) Click here to download [MADA Branding Document](https://docs.payfort.com/pdf/mada branding - ecommerce merchant - payment providers.pdf) - MEEZA (for Purchase operations and ECOMMERCE eci only) |
|  **order_description** Alphanumeric max: 150 | It holds the description of the order. Example: iPhone 6-S   |
|              **customer_name** Alpha max: 40 | The customer’s name. Example: John Smith                     |
|   **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?ruby#messages) |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code is made up of five digits, the first 2 digits refer to the request [status](https://docs.payfort.com/docs/api/build/index.html?ruby#statuses), and the last 3 digits refer to the request [messages](https://docs.payfort.com/docs/api/build/index.html?ruby#messages). Example: 20064 |
|                    **status** Numeric max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: [statuses](https://docs.payfort.com/docs/api/build/index.html?ruby#statuses) |
|           **customer_phone** Numeric max: 19 | The Customer mobile number. Example: 00962797219966          |
|         **return_url** Alphanumeric max: 400 | The URL of the Merchant’s page to be redirected to when the order is processed. Example: http://www.merchant.com |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones.</div>

After completing the checkout process through the payment link; the following list of parameters will be returned under the “Direct Transaction Feedback”:



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>To find your “Direct Transaction Feedback” from the back office; follow these steps:
Integration Settings → Technical Settings → Redirection Channel → you will find your “Direct Transaction Feedback”.</div>

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|                     **command** Alpha Max: 20 | A command. Possible/ expected values: AUTHORIZATION, PURCHASE |
|          **access_code** Alphanumeric Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
|  **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|   **merchant_reference** Alphanumeric Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                    **amount** Numeric Max: 10 | The transaction’s amount. Example: 10000                     |
|                     **currency** Alpha Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: AED |
|                     **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|      **customer_email** Alphanumeric Max: 254 | The customer’s email. Example: customer1@domain.com          |
|           **signature** Alphanumeric Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?ruby#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|      **payment_link_id** Alphanumeric max: 20 | The ID of the generated Invoice payment link. Example: 148708392700020346 |
|          **token_name** Alphanumeric max: 100 | The Token received from the Tokenization process. Example: Op9Vmp |
|                   **fort_id** Numeric Max: 20 | The order’s unique reference returned by our system. Example: 149295435400084008 |
|              **payment_option** Alpha Max: 10 | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX - SADAD (for Purchase operations only) - NAPS (for Purchase operations only) - KNET(for Purchase operations only) - MADA (for Purchase operations and eci Ecommerce only) Click here to download [MADA Branding Document](https://docs.payfort.com/pdf/mada branding - ecommerce merchant - payment providers.pdf) - MEEZA (for Purchase operations and ECOMMERCE eci only) |
|            **sadad_olp** Alphanumeric Max: 12 | SADAD Online Payment ID Alias. The merchant sends this value if the OLP ID is collected on the merchant checkout. Example: SABBP2P_UAT2 |
|                         **eci** Alpha Max: 16 | The E-commerce indicator. Possible/ expected values: - ECOMMERCE - MOTO |
|   **order_description** Alphanumeric Max: 150 | It holds the description of the order. Example: iPhone 6-S   |
|          **customer_ip** Alphanumeric max: 45 | It holds the customer’s IP address. *We support IPv4 and IPv6 as shown in the example below. Example: IPv4 → 192.178.1.10 IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf |
|               **customer_name** Alpha Max: 40 | The customer’s name. Example: John Smith                     |
|      **merchant_extra** Alphanumeric Max: 999 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra1** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra2** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra3** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra4** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra5** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|  **authorization_code** Alphanumeric Max: 100 | The authorization code returned from the 3rd party. Example: P1000000000000372136 |
|    **response_message** Alphanumeric Max: 150 | The message description of the response code; it returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?ruby#messages) |
|              **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?ruby#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?ruby#messages). Example: 20064 |
|                     **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?ruby#statuses) |
|            **card_holder_name** Alpha Max: 50 | The card holder name. Example: John Smith                    |
|                **expiry_date** Numeric Max: 4 | The card’s expiry date. Example: 2105                        |
|               **card_number** Numeric Max: 19 | The masked credit card’s number. *Only the MEEZA payment option takes 19 digits card number. \*AMEX payment option takes 15 digits card number. \*Otherwise, they take 16 digits card number.  Example: 400555******0001 |
|                  **remember_me** Alpha Max: 2 | This parameter provides you with an indication to whether to save this token for the user based on the user selection. Possible/ expected values: NO |
|         **phone_number** Alphanumeric max: 19 | The customer’s phone number. Example: 00962797219966         |
| **settlement_reference** Alphanumeric max: 34 | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. Example: XYZ9239-yu898 |

------



## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

To learn more about Tokens and Tokenization process visit this [link](tokenization.md)

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).