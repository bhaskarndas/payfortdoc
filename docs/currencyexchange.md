## Currency Exchange Service

This service allows the merchant to convert the transaction amount from one currency into another currency using live currency exchange rate.

 Remember - Before start implementing this service please make sure to contact support@payfort.com to activate it in your account.

### Currency Exchange URLs

**Test Environment URL:**

https://sbpaymentservices.PayFort.com/FortAPI/paymentApi

**Production Environment URL:**

https://paymentservices.PayFort.com/FortAPI/paymentApi

### Parameters Submission Type

REST POST request using JSON.

### Currency Exchange - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory max: 20 | Command. Possible/ expected values: CURRENCY_CONVERSION Special characters: _ |
|         **access_code** Alphanumeric Mandatory max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric Mandatory max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|                   **amount** Numeric Mandatory max: 10 | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. Example: 10000 |
|                    **currency** Alpha Mandatory max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|                    **language** Alpha Mandatory max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|          **converted_currency** Alpha Mandatory max: 3 | The ISO3 currency code of the currency you are converting the amount to. Example: AED |
|          **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |

 Remember - Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.

### Currency Exchange - Response

**The following parameters will be returned in PayFort’s Response:**

|                                   ATTRIBUTES | Description                                                  |
| -------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha max: 20 | Command. Possible/ expected values: CURRENCY_CONVERSION      |
|         **access_code** Alphanumeric max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|                   **amount** Numeric max: 10 | The transaction’s amount. Example: 10000                     |
|                    **currency** Alpha max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|                    **language** Alpha max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|          **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|   **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Possible/ expected values: (Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages)). |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). Example: 20064 |
|                    **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses)). |
|            **converted_amount** Alpha max: 3 | The amount after converting to another currency. Example: 100 USD = 367.298 AED |
|          **converted_currency** Alpha max: 3 | The ISO3 currency code of the currency you are converting the amount to. Example: AED |
|   **conversion_number** Alphanumeric max: 20 | A unique number generated by PayFort for every valid currency conversion request. Example: 1443796866848 |

 Remember - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.