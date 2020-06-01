### Installments Redirection Service - Request

You have to include the following parameters in the [Purchase - Request Parameters](redirectionsparameters.md) which you will send to PayFort:

|                              ATTRIBUTES | Description                                                  |
| --------------------------------------: | :----------------------------------------------------------- |
| **installments** Alpha Optional max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |



------

### Installments Redirection Service - Response

Placeholder : Provide sample JSON response

The following parameters will be returned in PayFort’s JSON Response in addition to the [Purchase - Response Parameters](redirectionsparameters.md):

|                                ATTRIBUTES | Description                                                  |
| ----------------------------------------: | :----------------------------------------------------------- |
|            **installments** Alpha max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |
| **number_of_installments** Numeric max: 2 | The number of installments the customer has selected in the payment page. Example: 3 |

------

### Installments Merchant page Service - Request

------

Placeholder: Provide sample code for request



Include the following parameters in the [Merchant page - Request Parameters](merchantpageparameters.md) you will send to PayFort:

|                                      ATTRIBUTES | Description                                                  |
| ----------------------------------------------: | :----------------------------------------------------------- |
|        **installments** Alpha Mandatory max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |
|            **amount** Numeric Mandatory Max: 10 | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. Example: 10000 |
|             **currency** Alpha Mandatory Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
| **customer_country_code** Alpha Optional Max: 3 | The Customer’s country code. ISO 3 digit country code. Example: JOR |

------

### Installments Merchant page Service - Response

Placeholder: Please provide sample JSON response.

The following parameters will be returned in PayFort’s Response in addition to the [Merchant Page - Response Parameters](merchantpageparameters.md)

|                                ATTRIBUTES | Description                                                  |
| ----------------------------------------: | :----------------------------------------------------------- |
|            **installments** Alpha max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |
|                **amount** Numeric Max: 10 | The transaction’s amount. Example: 10000                     |
|                 **currency** Alpha Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|    **customer_country_code** Alpha Max: 3 | The Customer’s country code. ISO 3-digit country code. Example: JOR |
| **number_of_installments** Numeric Max: 2 | The number of installments the customer has selected in payment page. Example: 3 |
|         **plan_code** Alphanumeric Max: 8 | A code that refers to the **“installments plan”** the customer selected from the merchant page. Example: NNNN89JJ |
|       **issuer_code** Alphanumeric Max: 8 | A code that refers to the **“card issuer”** the customer selected from the merchant page. Example: 12HP34SE |

------

### Installments Purchase Service - Request

Placeholder: Sample code for merchant page operations request

For transactions being carried out under operations you have to Include the following parameters in the [Operation - Request Parameters](https://docs.payfort.com/docs/api/build/index.html?shell#operations-request) while sending to PayFort:

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|      **installments** Alpha Mandatory max: 10 | Used to specify the type of the Installments service. Possible/ expected values: YES |
|   **plan_code** Alphanumeric Mandatory Max: 8 | A code that refers to the **“installments plan”** the customer selected from the merchant page. Example: NNNN89JJ |
| **issuer_code** Alphanumeric Mandatory Max: 8 | A code that refers to the **“card issuer”** the customer selected from the merchant page. Example: 12HP34SE |

------

### Installments Purchase Service - Response

------

Placeholder: Provide sample JSON response sent from the PayFORT server.

The following parameters will be returned in PayFort’s Response in addition to the [Operation - Response Parameters](https://docs.payfort.com/docs/api/build/index.html?shell#operations-response):

|                                ATTRIBUTES | Description                                                  |
| ----------------------------------------: | :----------------------------------------------------------- |
|            **installments** Alpha max: 10 | Used to specify the type of the Installments service. Possible/ expected values: YES |
|         **plan_code** Alphanumeric Max: 8 | A code that refers to the **“installments plan”** the customer selected from the merchant page. Example: NNNN89JJ |
|       **issuer_code** Alphanumeric Max: 8 | A code that refers to the **“card issuer”** the customer selected from the merchant page. Example: 12HP34SE |
| **number_of_installments** Numeric Max: 2 | The number of installments the customer has selected in payment page. Example: 3 |

------

### Get Installments Plans API - Request

Placeholder: Provide the sample code for the request

Include the following parameters in the Request you will send to PayFort:

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|              **query_command** Alpha Mandatory max: 50 | Query operations command. Possible/ expected values: GET_INSTALLMENTS_PLANS Special characters: _ |
|         **access_code** Alphanumeric Mandatory max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric Mandatory max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|          **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                    **amount** Numeric Optional max: 10 | The transaction’s amount.*Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. Example: 10000 |
|                     **currency** Alpha Optional max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|                     **language** Alpha Optional max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|           **issuer_code** Alphanumeric Optional max: 8 | A code that refers to the “card issuer” the customer selected from the merchant page. Example: 12HP34SE |

------

### Get Installments Plans API - Response

Placeholder: Provide sample JSON response

The following parameters will be returned in PayFort’s Response:

|                                   ATTRIBUTES | Description                                                  |
| -------------------------------------------: | :----------------------------------------------------------- |
|              **query_command** Alpha max: 50 | Query operations command. Possible/ expected values: GET_INSTALLMENTS_PLANS |
|         **access_code** Alphanumeric max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|          **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                   **amount** Numeric max: 10 | The transaction’s amount. Example: 10000                     |
|                    **currency** Alpha max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|                    **language** Alpha max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|          **issuer_code** Alphanumeric max: 8 | A code that refers to the “card issuer” the customer selected from the merchant page. Example: 12HP34SE |
|   **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Example: Insufficient Funds |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?shell#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages). Example: 20064 |
|                    **status** Numeric max: 2 | A two-digit numeric value that indicates the status of the transaction Possible/ expected values: (Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?shell#statuses)). |
|           **installment_detail** List max: - | This parameter is a parent parameter for other parameters that contain the details of installment. Possible/ expected values: (Please refer to the below section **issuer_detal**). |

------

### Issuer Detail

You can use the following attributes to know the details of the installment services issuers.

Placeholder: Provide sample code for issuer details

This parameter is a sub parameter of the <mark><strong>installment_detail</strong></mark> parameter, the table below shows the children parameters of the <mark><strong>issuer_detail</strong></mark>:

|                                           ATTRIBUTES | Description                                                  |
| ---------------------------------------------------: | :----------------------------------------------------------- |
|                  **issuer_code** Alphanumeric max: 8 | A code that refers to the “card issuer” the customer selected from the merchant page. Example: 12HP34SE |
|              **issuer_name_ar** Alphanumeric max: 50 | The issuer name in Arabic. Example: Issuer2عربي              |
|              **issuer_name_en** Alphanumeric max: 50 | The issuer name in English. Example: Issuer2                 |
|     **terms_and_condition_ar** Alphanumeric max: 200 | The Arabic terms and condition URL. Example: http://www.gmail.com |
|     **terms_and_condition_en** Alphanumeric max: 200 | The English terms and condition URL. Example: http://www.yahoo.com |
|                        **country_code** Alpha max: 3 | The country’s code in ISO 3-digits. Example: JOR             |
|             **issuer_logo_ar** Alphanumeric max: 350 | The issuer logo for the Arabic version. Example: https://payfort-fort-images-lt.s3.amazonaws.com/frontend/files/logos/issuer/logo_en_164.jpg |
|             **issuer_logo_en** Alphanumeric max: 350 | The issuer logo for the English version. Example: https://payfort-fort-images-lt.s3.amazonaws.com/frontend/files/logos/issuer/logo_en_164.jpg |
|                     **banking_system** Alpha max: 11 | The type of institutions that provide financial services. Possible/ expected values: -Non Islamic -Islamic |
|                    **formula** Alphanumeric max: 100 | The equation of calculating the installment value. Example: (amount +(amount *effective rate/100))/period Please check the note below the table for more details. |
|                         **plan_details** List max: - | This parameter contain all the plans for this issuer. Possible/ expected values: (Please refer to next **plan_detail** section). |
|                                 **bins** List max: - | List of 6 digits of the card number related to this issuer. Possible/ expected values: (Please refer to next **bins** section). |
|    **confirmation_message_ar** Alphanumeric max: 500 | This parameter shows to the customer the confirmation message in Arabic. |
|      **disclaimer_message_ar** Alphanumeric max: 500 | This parameter shows to the customer the disclaimer message in Arabic. |
| **processing_fees_message_ar** Alphanumeric max: 500 | This parameter shows to the customer the processing fee message in Arabic. |
|    **confirmation_message_en** Alphanumeric max: 500 | This parameter shows the customer to the confirmation message in English. |
|      **disclaimer_message_en** Alphanumeric max: 500 | This parameter shows to the customer the disclaimer message in English. |
| **processing_fees_message_en** Alphanumeric max: 500 | This parameter shows to the customer the processing fee message in English. |

------

### Plan Details

If you want to fetch details of various installment plans you can use the attributes in this section and send in your request to the PayFORT server.

Placeholder: provide sample code for plan details.

This parameter is a sub parameter of the <mark><strong>issuer_detail</strong></mark> parameter, the table below shows the children parameters of the <mark><strong>plan_detail</strong></mark>:

|                                 ATTRIBUTES | Description                                                  |
| -----------------------------------------: | :----------------------------------------------------------- |
|          **plan_code** Alphanumeric max: 8 | A code that refers to the “installments plan”. Example: NNNN89JJ |
|             **currency_code** Alpha max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|   **number_of_installment** Numeric max: 2 | The number of installments. Example: 3                       |
|                **fees_type** Alpha max: 10 | The type of the fee. Possible/ expected values: -Fixed -Percentage *Please refer to the below formulas section to know the difference. |
|            **fees_amount** Numeric max: 10 | The amount of the fee. Example: 11                           |
|     **processing_fees_type** Alpha max: 10 | The type of the processing fee. Possible/ expected values: -Fixed -Percentage *Please refer to the below formulas section to know the difference. |
| **processing_fees_amount** Numeric max: 10 | The amount of the processing fee. Example: 11                |
|                **rate_type** Alpha max: 15 | The type of the rate. Possible/ expected values: -Reducing Balance -Flat |
|       **plan_merchant_type** Alpha max: 11 | The type of agreement between the plan and Merchant. Possible/ expected values: -Partner -Non Partner |
|                **plan_type** Alpha max: 12 | The type of the installments plan. Possible/ expected values: -Local -Cross-Border |
|         **fee_display_value** Numeric max: | The display value that represent the fees amount. Example: 11.0 |
|         **minimum_amount** Numeric max: 10 | The minimum range of the accepted amount for this plan. Example: 11 |
|         **maximum_amount** Numeric max: 10 | The maximum range of the accepted amount for this plan. Example: 110000000 |
|         **amountPerMonth** Numeric max: 10 | The payable amount per month. Example: 3.00                  |

------

### Bins Details

This section will help you to capture the details of the credit card that customer will use for availing the installment service. You have to use the attributes in your request to fetch the details of the credit card.

Placeholder: provide  sample code for bins details.

This parameter is a sub parameter of the <mark><strong>issuer_detail</strong></mark> parameter, the table below shows the children parameters of the <mark><strong>bins</strong></mark>:

|                        ATTRIBUTES | Description                                                  |
| --------------------------------: | :----------------------------------------------------------- |
|            **bin** Numeric max: 6 | The first 6 digits of the card number. Example: 478773       |
|    **currency_code** Alpha max: 3 | The currency of the transaction’s amount in ISO code 3. Example: JOR |
| **card_brand_code** Alpha max: 16 | The type of the credit card. Possible/ expected values: -VISA -Master Card -American Express |

------

## Installment Service For Merchant Page 2.0 Operations - Request

You can use the endpoints to integrate and send request for Merchant Page 2.0 operations.



Placeholder: Provide sample code for merchant page 2.0 operations for installment service.

Include the following parameters in the Request you will send to PayFort:

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|                    **command** Alpha Mandatory max: 20 | Command. Possible/ expected values: PURCHASE                 |
|         **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz                        |
| **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|  **merchant_reference** Alphanumeric Mandatory Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . |
|                   **amount** Numeric Mandatory Max: 10 | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. Example: 10000 |
|                    **currency** Alpha Mandatory Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: AED |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|     **customer_email** Alphanumeric Mandatory Max: 254 | The customer’s email. Example: customer@domain.com Special characters: _ - . @ + |
|         **token_name** Alphanumeric Mandatory Max: 100 | The Token received from the Tokenization process. Example: Op9Vmp Special characters: _ - . @ |
|               **installments** Alpha Mandatory Max: 10 | Used to specify the type of the Installments service. Possible/ expected values: HOSTED |
|          **issuer_code** Alphanumeric Mandatory Max: 8 | A code that refers to the “card issuer” the customer selected from the merchant page. Example: 12HP34SE |
|            **plan_code** Alphanumeric Mandatory Max: 8 | A code that refers to the “installments plan” the customer selected from the merchant page. Example: NNNN89JJ |
|         **customer_ip** Alphanumeric Mandatory max: 45 | It holds the customer’s IP address. *It’s Mandatory, if the fraud service is active. *We support IPv4 and IPv6 as shown in the example below. Example: IPv4 → 192.178.1.10 IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf Special characters: . : |
|          **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|              **payment_option** Alpha Optional Max: 10 | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX |
|                         **eci** Alpha Optional Max: 16 | Ecommerce indicator. Possible/ expected values: ECOMMERCE    |
|   **order_description** Alphanumeric Optional Max: 150 | It holds the description of the order. Example: iPhone 6-S Special characters: `' `/ . _ - # : $ **Space** |
|         **card_security_code** Numeric Optional Max: 4 | A security code for the card. * Only AMEX accepts card security code of 4 digits. Example: 123 |
|               **customer_name** Alpha Optional Max: 40 | The customer’s name. Example: John Smith Special characters: _ \ / - . `' `**Space** |
|      **merchant_extra** Alphanumeric Optional Max: 999 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra1** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra2** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra3** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra4** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|     **merchant_extra5** Alphanumeric Optional Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith Special characters: . ; / _ - , `' `@ |
|                  **remember_me** Alpha Optional Max: 3 | This parameter provides you with an indication to whether to save this token for the user based on the user selection. *The Tokenization service MUST be activated in order to be able to send “remember_me” parameter. Possible/ expected values: -YES -NO |
|         **phone_number** Alphanumeric Optional max: 19 | The customer’s phone number. Example: 00962797219966 Special characters: + - ( ) **Space** |
| **settlement_reference** Alphanumeric Optional max: 34 | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. Example: XYZ9239-yu898 Special characters: - _ . |
|          **return_url** Alphanumeric Optional Max: 400 | The URL of the Merchant’s page to be displayed to the customer when the order is processed. Example: http://www.merchant.com Special characters: $ ! = ? # & - _ / : . |

 Remember - Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.

------



## Installment Service For Merchant Page 2.0 Operations - Response

------

Placeholder: Provide sample JSON response for merchant page 2.0 operations for installments.



The following parameters will be returned in PayFort’s Response:

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|                     **command** Alpha max: 20 | Command. Possible/ expected values: PURCHASE                 |
|          **access_code** Alphanumeric Max: 20 | The ID of the Merchant. Example: zx0IPmPy5jp1vAz             |
|  **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|   **merchant_reference** Alphanumeric Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                    **amount** Numeric Max: 10 | The transaction’s amount. Example: 10000                     |
|                     **currency** Alpha Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: AED |
|                     **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|      **customer_email** Alphanumeric Max: 254 | The customer’s email. Example: customer1@domain.com          |
|          **token_name** Alphanumeric max: 100 | The Token received from the Tokenization process. Example: COp9Vmp |
|                **installments** Alpha Max: 10 | Used to specify the type of the Installments service. Possible/ expected values: HOSTED |
|           **issuer_code** Alphanumeric Max: 8 | A code that refers to the “card issuer” the customer selected from the merchant page. Example: 12HP34SE |
|             **plan_code** Alphanumeric Max: 8 | A code that refers to the “installments plan” the customer selected from the merchant page. Example: NNNN89JJ |
|          **customer_ip** Alphanumeric max: 45 | It holds the customer’s IP address. *We support IPv4 and IPv6 as shown in the example below. Example: IPv4 → 192.178.1.10 IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf |
|           **signature** Alphanumeric Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?shell#signature) Example: d7c185c475ac0e3 |
|                   **fort_id** Numeric Max: 20 | The order’s unique reference returned by our system. Example: 149295435400084008 |
|              **payment_option** Alpha Max: 10 | Payment option. Possible/ expected values: - MASTERCARD - VISA - AMEX |
|                         **eci** Alpha Max: 16 | Ecommerce indicator. Possible/ expected values: ECOMMERCE    |
|   **order_description** Alphanumeric Max: 150 | It holds the description of the order. Example: iPhone 6-S   |
|  **authorization_code** Alphanumeric Max: 100 | The authorization code returned from the 3rd party. Example: P1000000000000372136 |
|    **response_message** Alphanumeric Max: 150 | Message description of the response code. It returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages) |
|              **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?shell#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?shell#messages). Example: 20064 |
|               **customer_name** Alpha Max: 40 | The customer’s name. Example: John Smith                     |
|      **merchant_extra** Alphanumeric Max: 999 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra1** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra2** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra3** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra4** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|     **merchant_extra5** Alphanumeric Max: 250 | Extra data sent by merchant. Will be received and sent back as received. Will not be displayed in any report. Example: JohnSmith |
|                **expiry_date** Numeric Max: 4 | The card’s expiry date. Example: 2105                        |
|               **card_number** Numeric Max: 19 | The masked credit card’s number. *AMEX payment option takes 15 digits card number. \*Otherwise, they take 16 digits card number. Example: 400555******0001 |
|                     **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?shell#statuses) |
|            **card_holder_name** Alpha Max: 50 | The card holder name. Example: John Smith                    |
|             **3ds_url** Alphanumeric Max: 300 | The URL where the Merchant redirects a customer whose card is 3-D Secure for authentication. Example: http://www.3dsecure.com |
|                  **remember_me** Alpha Max: 3 | This parameter provides you with an indication to whether to save this token for the user based on the user selection. Possible/ expected values: - YES - NO |
|         **phone_number** Alphanumeric max: 19 | The customer’s phone number. Example: 00962797219966         |
| **settlement_reference** Alphanumeric max: 34 | The Merchant submits this value to the FORT. The value is then passed to the Acquiring bank and displayed to the merchant in the Acquirer settlement file. Example: XYZ9239-yu898 |

 Remember - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.

------

### Installments Hosted for Trusted – Request

Placeholder: Please provide sample code for trusted channel partner request for installment.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>First, you need to send a [Get Instalments Plans API](https://docs.payfort.com/docs/api/build/index.html?shell#get-installments-plans-api) request; to get the instalments details.


Include the following input parameters in the [Trusted Channel – Request](https://docs.payfort.com/docs/api/build/index.html?shell#trusted-channel-request) Parameters you will send to PayFort:</div>



|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|      **installments** Alpha Mandatory Max: 10 | Used to specify the type of the Installments service. Possible/ expected values: HOSTED |
| **issuer_code** Alphanumeric Mandatory Max: 8 | A code that refers to the “card issuer” the customer selected from the merchant page. Example: 12HP34SE |
|   **plan_code** Alphanumeric Mandatory Max: 8 | A code that refers to the “installments plan” the customer selected from the merchant page. Example: NNNN89JJ |

------



### Installments Hosted for Trusted – Response

------

The following parameters will be returned in PayFort’s Response in addition to [Trusted Channel – Response](trustedchannelparameters.md) parameters:

|                          ATTRIBUTES | Description                                                  |
| ----------------------------------: | :----------------------------------------------------------- |
|      **installments** Alpha Max: 10 | Used to specify the type of the Installments service. Possible/ expected values: HOSTED |
| **issuer_code** Alphanumeric Max: 8 | A code that refers to the “card issuer” the customer selected from the merchant page. Example: 12HP34SE |
|   **plan_code** Alphanumeric Max: 8 | A code that refers to the “installments plan” the customer selected from the merchant page. Example: NNNN89JJ |

------

