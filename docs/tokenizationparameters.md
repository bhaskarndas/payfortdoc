**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory Max: 20 | Command. Possible/ expected values: CREATE_TOKEN             |
|         **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Mandatory Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|              **card_number** Numeric Mandatory Max: 19 | The clear card data collect on the Merchant page form, developed by the Merchant. *Only the MEEZA payment option takes 19 digits card number. *AMEX payment option takes 15 digits card number. *Otherwise, they take 16 digits card number Example: 4005550000000001 |
|               **expiry_date** Numeric Mandatory Max: 4 | The card’s expiry date. Example: 2105                        |
|         **return_url** Alphanumeric Mandatory Max: 400 | The URL of the Merchant’s page that will be displayed to the customer when the order is processed. Example: http://www.merchant.com Special characters: $ ! = ? # & - _ / : . |
|          **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                     **currency** Alpha Optional Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|          **token_name** Alphanumeric Optional Max: 100 | The Token received from the Tokenization process. Example: Op9Vmp Special characters: . @ - _ |
|            **card_holder_name** Alpha Optional Max: 50 | The card holder name. Example: John Smith Special characters: `' `- . |

Create New Token Service - Response

**The following parameters will be returned in PayFort’s Response:**

|                                   ATTRIBUTES | Description                                                  |
| -------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Max: 20 | Command. Possible/ expected values: CREATE_TOKEN             |
|         **access_code** Alphanumeric Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                    **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|              **card_number** Numeric Max: 19 | The masked credit card’s number. *Only the MEEZA payment option takes 19 digits card number. \*AMEX payment option takes 15 digits card number. \*Otherwise, they take 16 digits card number Example: 400555******0001 |
|               **expiry_date** Numeric Max: 4 | The card’s expiry date. Example: 2105                        |
|         **return_url** Alphanumeric Max: 400 | The URL of the Merchant’s page that will be displayed to the customer when the order is processed. Example: http://www.merchant.com |
|          **signature** Alphanumeric Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                    **currency** Alpha Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|         **token_name** Alphanumeric Max: 100 | The Token received from the Tokenization process. Example: Op9Vmp |
|           **card_holder_name** Alpha Max: 50 | The card holder name. Example: John Smith                    |
|   **response_message** Alphanumeric Max: 150 | The message description of the response code; it returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages) |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?shell#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages). Example: 20064 |
|                    **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?shell#statuses) |

 Remember - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.

### Update Token Service

This service enables you to update your card associated with a token and the status of a token via API calls.

Update Token Service URLs

**Test Environment URL:**

https://sbpaymentservices.payfort.com/FortAPI/paymentApi

**Production Environment URL:**

https://paymentservices.payfort.com/FortAPI/paymentApi

Parameters Submission Type

REST POST request using JSON.

Update Token Service – Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory Max: 20 | Command. Possible/ expected values: UPDATE_TOKEN Special characters: _ |
|         **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Mandatory Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|         **token_name** Alphanumeric Mandatory Max: 100 | The token received from the Tokenization process. Example: Op9Vmp Special characters: . @ - _ |
|          **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                **expiry_date** Numeric Optional Max: 4 | The card’s expiry date. Example: 2105                        |
|            **card_holder_name** Alpha Optional Max: 50 | The card holder name. Example: John Smith Special characters: `' `- . |
|                     **currency** Alpha Optional Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|                 **token_status** Alpha Optional Max: 8 | Presents the token status. Possible/ expected values: - ACTIVE - INACTIVE |
|      **new_token_name** Alphanumeric Optional Max: 100 | The new name used to update the existing token. Example: Test1 Special characters: _ - @ . |

Update Token Service – Response

**The following parameters will be returned in PayFort’s Response:**

|                                   ATTRIBUTES | Description                                                  |
| -------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Max: 20 | Command. Possible/ expected values: UPDATE_TOKEN             |
|         **access_code** Alphanumeric Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                    **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|         **token_name** Alphanumeric Max: 100 | The Token received from the Tokenization process. Example: Op9Vmp |
|          **signature** Alphanumeric Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|               **expiry_date** Numeric Max: 4 | The card’s expiry date. Example: 2105                        |
|              **card_number** Numeric Max: 19 | The masked credit card’s number. *Only the MEEZA payment option takes 19 digits card number. \*AMEX payment option takes 15 digits card number. \*Otherwise, they take 16 digits card number Example: 400555******0001 |
|           **card_holder_name** Alpha Max: 50 | The card holder name. Example: John Smith                    |
|                    **currency** Alpha Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|   **response_message** Alphanumeric Max: 150 | The message description of the response code; it returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages) |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?shell#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages). Example: 58000 |
|                **token_status** Alpha Max: 8 | Presents the token status. Possible/ expected values: -ACTIVE -INACTIVE |
|       **creation_date** Alphanumeric Max: 30 | Creation date of content in UTC format. Example: 2017-03-13T10:09:19+02:00 |
|                 **card_brand** Alpha Max: 10 | Issuer account type. Possible/ expected values: - MASTERCARD - VISA - AMEX |
|                  **card_bin** Numeric Max: 8 | The first 6 digits of the card number.*If the card number for MEEZA was of length 19 then the card bin will be the first 8 digits. Example: 478773 |
|                    **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: Please refer to section [statuses]( |

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
|          **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |

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
|          **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|   **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Possible/ expected values: (Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages)). |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?shell#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages). Example: 20064 |
|                    **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?shell#statuses)). |
|            **converted_amount** Alpha max: 3 | The amount after converting to another currency. Example: 100 USD = 367.298 AED |
|          **converted_currency** Alpha max: 3 | The ISO3 currency code of the currency you are converting the amount to. Example: AED |
|   **conversion_number** Alphanumeric max: 20 | A unique number generated by PayFort for every valid currency conversion request. Example: 1443796866848 |

------

## Merchant Page 2.0 Tokenization - Request

Placeholder: Sample code for Merchant Page 2.0 installments request.





**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory max: 20 | Command. Possible/ expected values: TOKENIZATION             |
|         **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Mandatory Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|               **expiry_date** Numeric Mandatory Max: 4 | The card’s expiry date. Example: 2105                        |
|              **card_number** Numeric Mandatory Max: 16 | The clear credit card’s number. Example: 4005550000000001    |
|        **card_security_code** Numeric Mandatory Max: 4 | A security code for the card. * Only AMEX accepts card security code of 4 digits. Example: 123 |
|          **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) for more details). *Please don’t include the following parameters in calculating the signature of Merchant Page 2.0 tokenization request: card_security_code, card number, expiry_date, card_holder_name, remember_me. Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|          **token_name** Alphanumeric Optional Max: 100 | The token received from the Tokenization process. Example: Op9Vmp Special characters: . @ - _ |
|            **card_holder_name** Alpha Optional Max: 50 | The card holder name. Example: John Smith Special characters: . - ’ |
|                  **remember_me** Alpha Optional Max: 3 | This parameter provides you with an indication to whether to save this token for the user based on the user selection. Possible/ expected values: - YES - NO |
|          **return_url** Alphanumeric Optional Max: 400 | The URL of the Merchant’s page to be displayed to the customer when the order is processed. Example: http://www.merchant.com Special characters: $ ! = ? # & - _ / : . |

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Please don’t include the following parameters in calculating the signature if you are using Merchant Page 2.0 tokenization request: card_security_code, card number, expiry_date, card_holder_name, remember_me.</div>





------



## Merchant Page 2.0 Tokenization - Response

Placeholder: Provide sample json response.



**The following parameters will be returned in PayFort’s Response:**

|                                   ATTRIBUTES | Description                                                  |
| -------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Max: 20 | Command. Possible/ expected values: TOKENIZATION             |
|         **access_code** Alphanumeric Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                    **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|               **expiry_date** Numeric Max: 4 | The card’s expiry date. Example: 2105                        |
|              **card_number** Numeric Max: 19 | The masked credit card’s number. *AMEX payment option takes 15 digits card number. \*Otherwise, they take 16 digits card number. Example: 400555******0001 |
|          **signature** Alphanumeric Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#create-signature-value) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|         **token_name** Alphanumeric max: 100 | The Token received from the Tokenization process. Example: COp9Vmp |
|   **response_message** Alphanumeric Max: 150 | Message description of the response code. It returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages) |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?shell#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages). Example: 20064 |
|                    **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?shell#statuses)). |
|                  **card_bin** Numeric Max: 8 | The first 6 digits of the card number.*If the card number for MEEZA was of length 19 then the card bin will be the first 8 digits. Example: 478773 |
|           **card_holder_name** Alpha Max: 50 | The card holder name. Example: John Smith                    |
|                 **remember_me** Alpha Max: 3 | This parameter provides you with an indication to whether to save this token for the user based on the user selection. Possible/ expected values: - YES - NO |
|         **return_url** Alphanumeric Max: 400 | The URL of the Merchant’s page to be displayed to the customer when the order is processed. Example: http://www.merchant.com |