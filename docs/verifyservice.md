# Verify Service Command

## Verify Service Command

Verify API provides PCI certified merchants several methods that you can use to determine if a particular card account is valid and in good standing. The ability to pre-validate a credit card (Visa, MasterCard and Amex) increases the probability of a successful, seamless transaction flow and more valid card registration.

### Before Starting

Before start integrating this service you need to know the below:
• This service command is applicable on two channels only; where you have to configure the channel you want to add this service to it from the FORT back-office:
  \1. Merchant page.
  \2. Trusted.
• This service command is only applicable on “MOTO” E-commerce indicator.
• You need to add the amount to be Authorized/ Captured from the customer for the verification.
• This Authorized/ Captured amount will be Voided/ Refunded after checking the card validity.
• The verification transactions will be recorded under one report “Card Verification Report” in the back-office.

### Verify Service Command on Trusted URLs

**Test Environment URL:**

https://sbpaymentservices.PayFort.com/FortAPI/paymentApi

**Production Environment URL:**

https://paymentservices.PayFort.com/FortAPI/paymentApi

### Parameters Submission Type

REST POST request using JSON.

### Verify Service Command on Trusted - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory max: 20 | Command. Possible/ expected values: VERIFY_CARD Special characters: _ |
|         **access_code** Alphanumeric Mandatory max: 20 | Merchant account Access Code. Example: zx0IPmPy5jp1vAz8Kpg7  |
| **merchant_identifier** Alphanumeric Mandatory max: 20 | FORT Merchant Account identifier. Example: CycHZxVj          |
|  **merchant_reference** Alphanumeric Mandatory max: 40 | The Merchant’s unique reference for a specific request. Example: XYZ9239-yu898 Special characters: _ - . |
|                    **currency** Alpha Mandatory Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: AED |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|               **expiry_date** Numeric Mandatory max: 4 | The card’s expiry date. Example: 2105                        |
|              **card_number** Numeric Mandatory max: 16 | The clear credit card’s number. Example: 4005550000000001    |
|          **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
| **settlement_reference** Alphanumeric Optional max: 34 | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. Example: example Special characters: _ - . |

 Remember - Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.

**Verify Service Command on Trusted Request Example**

{
“card_number”:“4005550000000001”,
“expiry_date”:“2105”,
“service_command”:“VERIFY_CARD”,
“settlement_reference”:“example”,
“merchant_reference”:“XYZ9239-yu898”,
“currency”:“AED”,
“access_code”:“zx0IPmPy5jp1vAz”,
“merchant_identifier”:“CycHZxVj”,
“language”:“en”,
“signature”:“eef26521d64ffd436b056ab9da0267334aa886acfe392f803e6705d0a5b0fc7a”
}

### Verify Service Command on Trusted - Response

**The following parameters will be returned in PayFort’s Response:**

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|             **service_command** Alpha max: 20 | Command. Possible/ expected values: VERIFY_CARD Special characters: _ |
|          **access_code** Alphanumeric max: 20 | Merchant account Access Code. Example: zx0IPmPy5jp1vAz8Kpg7  |
|  **merchant_identifier** Alphanumeric max: 20 | FORT Merchant Account identifier. Example: CycHZxVj          |
|   **merchant_reference** Alphanumeric max: 40 | The Merchant’s unique reference for a specific request. Example: XYZ9239-yu898 Special characters: _ - . |
|                     **currency** Alpha Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: AED |
|                     **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|                **expiry_date** Numeric max: 4 | The card’s expiry date. Example: 2105                        |
|               **card_number** Numeric max: 16 | The masked credit card’s number. Example: 400555******0001   |
|           **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                     **language** Alpha max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|    **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Example: Insufficient Funds |
|              **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). Example: 80000 |
|                     **status** Numeric max: 2 | A two-digit numeric value that indicates the status of the transaction Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses)). |
| **settlement_reference** Alphanumeric max: 34 | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. Example: example |

 Remember - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response - even the optional ones.

**Verify Service Command on Trusted Response Example**

{
“response_code”: “80000”,
“card_number”:“400555******0001”,
“expiry_date”:“2105”,
“service_command”:“VERIFY_CARD”,
“settlement_reference”:“example”,
“merchant_reference”:“XYZ9239-yu898”,
“currency”:“AED”,
“access_code”:“zx0IPmPy5jp1vAz”,
“merchant_identifier”:“CycHZxVj”,
“response_message”: “Success”,
“language”:“en”,
“status”:”80”,
“signature”:“eef26521d64ffd436b056ab9da0267334aa886acfe392f803e6705d0a5b0fc7a”
}

## Check Status for Verify Service Command

This feature allows the Merchants to easily check the actual status of the “Verify card command” results through this API.

### Check Status for Verify Service Command URLs

**Test Environment URL:**

https://sbpaymentservices.PayFort.com/FortAPI/paymentApi

**Production Environment URL:**

https://paymentservices.PayFort.com/FortAPI/paymentApi

### Parameters Submission Type

REST POST request using JSON.

### Check Status for Verify Service - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|              **query_command** Alpha Mandatory max: 50 | Query operations command. Possible/ expected values: CHECK_VERIFY_CARD_STATUS Special characters: _ |
|         **access_code** Alphanumeric Mandatory max: 20 | Access Code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Mandatory max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Mandatory max: 40 | The Merchant’s unique number. *Please, use the same merchant reference you used in the “Verify Card Service Command” request. Example: XYZ9239-yu898 |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|          **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |

**Check Status on Verify Service Command Request Example**

{
“query_command”:“CHECK_VERIFY_CARD_STATUS”,
“merchant_reference”:“XYZ9239-yu898”,
“access_code”:“zx0IPmPy5jp1vAz”,
“merchant_identifier”:“CycHZxVj”,
“language”:“en”,
“signature”:“f93c586997906bac21e8d046407c3fbed6b6820affcb7345353487287cc7c03a”
}

### Check Status for Verify Service Command - Response

**The following parameters will be returned in PayFort’s Response:**

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|               **query_command** Alpha max: 50 | Query operations command. Possible/ expected values: CHECK_VERIFY_CARD_STATUS |
|          **access_code** Alphanumeric max: 20 | Access Code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
|  **merchant_identifier** Alphanumeric max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|   **merchant_reference** Alphanumeric max: 40 | The Merchant’s unique reference for a specific request. Example: XYZ9239-yu898 |
|                     **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|           **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|    **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Example: Insufficient Funds |
|              **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). Example: 56000 |
|                     **status** Numeric max: 2 | A two-digit numeric value that indicates the status of the transaction Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses)). |
|         **transaction_status** Numeric max: 2 | The status of the last verify operation performed on a specific card. Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses)). |
| **transaction_message** Alphanumeric Max: 150 | The message returned for the last verify operation performed on a specific card. Example: success |

 Remember - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response - even the optional ones.

**Check Status on Verify Service Command Response Example**

{
“transaction_code”:“80000”,
“response_code”:“12000”,
“transaction_status”:“80”,
“signature”:“00c1ea64b7de291f7d5548630bbfbf329bd3fd963bf55c35fefc84d982da193e”,
“merchant_identifier”:“CycHZxVj”,
“access_code”:“zx0IPmPy5jp1vAz8Kpg7”,
“transaction_message”:“Success”,
“language”:“en”,
“response_message”:“Success”,
“merchant_reference”:“Verify31”,
“query_command”:“CHECK_VERIFY_CARD_STATUS”,
“status”:“12”
}