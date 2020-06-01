## MOTO Request Parameters

------

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|                    **command** Alpha Mandatory max: 20 | Command. Possible/ expected values: AUTHORIZATION, PURCHASE  |
|         **access_code** Alphanumeric Mandatory max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric Mandatory max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Mandatory max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . |
|                   **amount** Numeric Mandatory max: 10 | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. Example: 10000 |
|                    **currency** Alpha Mandatory max: 3 | The currency of the transaction’s amount in ISO code 3. Example: AED |
|                    **language** Alpha Mandatory max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|     **customer_email** Alphanumeric Mandatory max: 254 | The customer’s email. Example: customer@domain.com Special characters: _ - . @ + |
|                        **eci** Alpha Mandatory max: 16 | Ecommerce indicator. Possible/ expected values: MOTO         |
|         **token_name** Alphanumeric Mandatory max: 100 | The token received from the Tokenization process. Example: Op9Vmp Special characters: _ - . @ |
|          **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|              **payment_option** Alpha Optional max: 10 | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX |
|   **order_description** Alphanumeric Optional max: 150 | It holds the description of the order. Example: iPhone 6-S Special characters: `' `/ . _ - # : $ **Space** |
|          **customer_ip** Alphanumeric Optional max: 45 | It holds the customer’s IP address. *It’s Mandatory, if the fraud service is active. *We support IPv4 and IPv6 as shown in the example below. Example: IPv4 → 192.178.1.10 IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf Special characters: . : |
|               **customer_name** Alpha Optional max: 40 | The customer’s name. Example: John Smith Special characters: _ \ / - . `' `**Space** |
|         **phone_number** Alphanumeric Optional max: 19 | The customer’s phone number. Example: 00962797219966 Special characters: + - ( ) **Space** |
| **settlement_reference** Alphanumeric Optional max: 34 | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. Example: XYZ9239-yu898 Special characters: - _ . |
|      **merchant_extra** Alphanumeric Optional Max: 999 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra1** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra2** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra3** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra4** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra5** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|          **return_url** Alphanumeric Optional max: 400 | The URL of the Merchant’s page to be redirected to when the order is processed. Example: http://www.merchant.com Special characters: $ ! = ? # & - _ / : . |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

------

## MOTO Response

------

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|                     **command** Alpha max: 20 | Command. Possible/ expected values: AUTHORIZATION, PURCHASE  |
|          **access_code** Alphanumeric max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
|  **merchant_identifier** Alphanumeric max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|   **merchant_reference** Alphanumeric max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                    **amount** Numeric max: 10 | The transaction’s amount. Example: 10000                     |
|                     **currency** Alpha max: 3 | The currency of the transaction’s amount in ISO code 3. Example: AED |
|                     **language** Alpha max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|      **customer_email** Alphanumeric max: 254 | The customer’s email. Example: customer@domain.com           |
|                         **eci** Alpha max: 16 | Ecommerce indicator. Possible/ expected values: MOTO         |
|          **token_name** Alphanumeric max: 100 | The token received from the Tokenization process. Example: Op9Vmp |
|           **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                   **fort_id** Numeric max: 20 | The order’s unique reference returned by our system. Example: 149295435400084008 |
|              **payment_option** Alpha max: 10 | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX |
|   **order_description** Alphanumeric max: 150 | It holds the description of the order. Example: iPhone 6-S   |
|          **customer_ip** Alphanumeric max: 45 | It holds the customer’s IP address. *We support IPv4 and IPv6 as shown in the example below. Example: IPv4 → 192.178.1.10 IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf |
|               **customer_name** Alpha max: 40 | The customer’s name. Example: John Smith                     |
|  **authorization_code** Alphanumeric max: 100 | The authorization code returned from the 3rd party. Example: P1000000000000372136 |
|    **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages) |
|              **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). Example: 20064 |
|                     **status** Numeric max: 2 | A two-digit numeric value that indicates the status of the transaction Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses)). |
|                **expiry_date** Numeric max: 4 | The card’s expiry date. Example: 2105                        |
|               **card_number** Numeric max: 16 | The card’s number masked based on a certain standard that is selected in the technical settings. Example: 400555******0001 |
|         **phone_number** Alphanumeric max: 19 | The customer’s phone number. Example: 00962797219966         |
| **settlement_reference** Alphanumeric max: 34 | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. Example: XYZ9239-yu898 |
|      **merchant_extra** Alphanumeric Max: 999 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra1** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra2** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra3** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra4** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra5** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|          **return_url** Alphanumeric max: 400 | The URL of the Merchant’s page to be redirected to when the order is processed. Example: http://www.merchant.com |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>