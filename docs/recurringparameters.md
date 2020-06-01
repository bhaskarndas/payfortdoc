## Recurring Transactions Request Parameters

------



| ATTRIBUTES                                               | Possible/Expected Values or examples              | Description                                                  |
| :------------------------------------------------------- | ------------------------------------------------- | :----------------------------------------------------------- |
| **command**( Alpha Mandatory max: 20)                    | PURCHASE                                          | command                                                      |
| **access_code**( Alphanumeric Mandatory max: 20)         | zx0IPmPy5jp1vAz                                   | Access code                                                  |
| **merchant_identifier**( Alphanumeric Mandatory max: 20) | CycHZxVj                                          | The ID of the Merchant.                                      |
| **merchant_reference**( Alphanumeric Mandatory max: 40)  | XYZ9239-yu898                                     | The Merchant’s unique order number.  Special characters: - _ . |
| **amount**( Numeric Mandatory max: 10)                   | 10000                                             | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. |
| **currency**(Alpha Mandatory max: 3)                     | AED                                               | The currency of the transaction’s amount in ISO code 3.      |
| **language**( Alpha Mandatory max: 2)                    | en / ar                                           | The checkout page and messages language.                     |
| **customer_email**(Alphanumeric Mandatory max: 254)      | [customer@domain.com](mailto:customer@domain.com) | The customer’s email. Special characters: _ - . @ +          |
| **eci** (Alpha Mandatory max: 16)                        | RECURRING                                         | Ecommerce indicator.                                         |
| **token_name**( Alphanumeric Mandatory max: 100)         | Op9Vmp                                            | The Token received from the Tokenization process. Special characters: _ - . @ |
| **signature**( Alphanumeric Mandatory max: 200)          | 7cad05f0212ed933c9a5d5dffa31661acf2c827a          | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). |
| **payment_option**( Alpha Optional Max: 10)              | -MASTERCARD  - VISA - AMEX                        | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX |
| **order_description**( Alphanumeric Optional max: 150)   | iPhone 6-S                                        | It holds the description of the order. Special characters: `'`/ . _ - # : $ **Space** |
| **customer_name**( Alpha Optional max: 40)               | John Smith                                        | The customer’s name.  Special characters: _ \ / - . `'`**Space** |
| **merchant_extra**( Alphanumeric Optional Max: 999)      | JohnSmith                                         | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Special characters: . ; / _ - , `'`@ |
| **merchant_extra1**( Alphanumeric Optional Max: 250)     | JohnSmith                                         | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report.  Special characters: . ; / _ - , `'`@ |
| **merchant_extra2**( Alphanumeric Optional Max: 250)     | JohnSmith                                         | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Special characters: . ; / _ - , `'`@ |
| **merchant_extra3**( Alphanumeric Optional Max: 250)     | JohnSmith                                         | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report.  Special characters: . ; / _ - , `'`@ |
| **merchant_extra4**( Alphanumeric Optional Max: 250)     | JohnSmith                                         | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report.  Special characters: . ; / _ - , `'`@ |
| **merchant_extra5**( Alphanumeric Optional Max: 250)     | JohnSmith                                         | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report.  Special characters: . ; / _ - , `'`@ |
| **phone_number**( Alphanumeric Optional max: 19)         | 00962797219966                                    | The customer’s phone number.  Special characters: + - ( ) **Space** |
| **settlement_reference**( Alphanumeric Optional max: 34) | XYZ9239-yu898                                     | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file.  Special characters: - _ . |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

------

## Recurring Transaction Response

------

|                                                 ATTRIBUTES | Possible/Expected  values or Example                         | Description                                                  |
| ---------------------------------------------------------: | ------------------------------------------------------------ | :----------------------------------------------------------- |
|                     **command**<sup>( Alpha max: 20)</sup> | <mark>PURCHASE</mark>                                        | command.                                                     |
|          **access_code**<sup>( Alphanumeric max: 20)</sup> | zx0IPmPy5jp1vAz                                              | Access code.                                                 |
|  **merchant_identifier**<sup>( Alphanumeric max: 20)</sup> | CycHZxVj                                                     | The ID of the Merchant.                                      |
|   **merchant_reference**<sup>( Alphanumeric max: 40)</sup> | XYZ9239-yu898                                                | The Merchant’s unique order number.                          |
|                    **amount**<sup>( Numeric max: 10)</sup> | 10000                                                        | The transaction’s amount.                                    |
|                     **currency**<sup>( Alpha max: 3)</sup> | AED                                                          | The currency of the transaction’s amount in ISO code 3.      |
|                           **language**<sup>( Alpha max: 2) | <mark>en / ar</mark>                                         | The checkout page and messages language.                     |
|      **customer_email**<sup>( Alphanumeric max: 254)</sup> | customer@domain.com                                          | The customer’s email.                                        |
|                         **eci** <sup>(Alpha max: 16)</sup> | <mark>RECURRING</mark>                                       | Ecommerce indicator.                                         |
|          **token_name**<sup>( Alphanumeric max: 100)</sup> | Op9Vmp                                                       | The Token received from the Tokenization process.            |
|           **signature**<sup>( Alphanumeric max: 200)</sup> | 7cad05f0212ed933c9a5d5dffa31661acf2c827a                     | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). |
|                   **fort_id**<sup>( Numeric max: 20)</sup> | 149295435400084008                                           | The order’s unique reference returned by our system.         |
|                           **payment_option** Alpha Max: 10 | - MASTERCARD <br/>- VISA<br/>- AMEX                          | Payment option.                                              |
|   **order_description**<sup>( Alphanumeric max: 150)</sup> | iPhone 6-S                                                   | It holds the description of the order.                       |
|                     **customer_name**<sup>( Alpha max: 40) | John Smith                                                   | The customer’s name.                                         |
|      **merchant_extra**<sup>( Alphanumeric Max: 999)</sup> | JohnSmith                                                    | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |
|     **merchant_extra1**<sup>( Alphanumeric Max: 250)</sup> | JohnSmith                                                    | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |
|     **merchant_extra2**<sup>( Alphanumeric Max: 250)</sup> | JohnSmith                                                    | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |
|     **merchant_extra3**<sup>( Alphanumeric Max: 250)</sup> | JohnSmith                                                    | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |
|     **merchant_extra4**<sup>( Alphanumeric Max: 250)</sup> | JohnSmith                                                    | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |
|     **merchant_extra5**<sup>( Alphanumeric Max: 250)</sup> | JohnSmith                                                    | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. |
|                **expiry_date**<sup>( Numeric Max: 4)</sup> | 2015                                                         | The card’s expiry date. Example: 2105                        |
|               **card_number**<sup>( Numeric Max: 16)</sup> | 400555******0001                                             | The clear credit card’s number.                              |
|  **authorization_code**<sup>( Alphanumeric max: 100)</sup> | P1000000000000372136                                         | The authorization code returned from the 3rd party.          |
|    **response_message**<sup>( Alphanumeric max: 150)</sup> | Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages) | Message description of the response code. It returns according to the request language. Possible/ expected values: |
|              **response_code**<sup>( Numeric Max: 5)</sup> | 20064                                                        | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). |
|                     **status**<sup> (Numeric max: 2)</sup> | Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses) | A two-digit numeric value that indicates the status of the transaction |
|         **phone_number**<sup>( Alphanumeric max: 19)</sup> | 00962797219966                                               | The customer’s phone number.                                 |
| **settlement_reference**<sup>( Alphanumeric max: 34)</sup> | XYZ9239-yu898                                                | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

------

