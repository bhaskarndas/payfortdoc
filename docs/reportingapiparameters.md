# Reporting API Request and Response

------

## Generate Report - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|              **query_command** Alpha Mandatory max: 50 | Query operations command. Possible/ expected values: GENERATE_REPORT Special characters: _ |
|         **access_code** Alphanumeric Mandatory max: 20 | Merchant account Access Code. Example: zx0IPmPy5jp1vAz8Kpg7  |
| **merchant_identifier** Alphanumeric Mandatory max: 20 | FORT Merchant Account identifier. Example: CycHZxVj          |
|  **merchant_reference** Alphanumeric Mandatory max: 40 | The Merchant’s unique reference for a specific request. Example: XYZ9239-yu898 Special characters: _ - . |
|           **from_date** Alphanumeric Mandatory max: 30 | Query parameter to filter from a specific date. Example: 2017-01-01T14:36:55+03:00 Special characters: + - : |
|             **to_date** Alphanumeric Mandatory max: 30 | Query parameter to filter the results till a specific date. Example: 2017-06-28T14:36:55+03:00 Special characters: + - : |
|                    **columns** List Mandatory max: 110 | The columns you want to appear in your report. Possible/ expected values: (Please refer to section [column parameters](https://docs.payfort.com/docs/api/build/index.html?ruby#columns-parameter)). Special characters: _ |
|          **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?ruby#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                     **language** Alpha Optional max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|              **response_format** Alpha Optional max: 4 | The FORT response format; weather its JSON or XML. *The default response format is “JSON”. Possible/ expected values: - JSON - XML |
|                      **filters** List Optional max: 10 | The filters the merchant wants to use to filter the generated report results. possible/ expected values: (Please refer to section [filters parameters](https://docs.payfort.com/docs/api/build/index.html?ruby#filters-parameter)). |

### Columns Parameter

**The following table contains all the possible values you want to revert in your response, you can choose any of them:**

|                     Value | Description                                                  |
| ------------------------: | :----------------------------------------------------------- |
|                   fort_id | The order’s unique reference returned by our system.         |
|        merchant_reference | The Merchant’s unique order number.                          |
|        authorization_code | The authorization code returned from the 3rd party responsible for processing the transaction. |
|             customer_name | The Customer’s name.                                         |
|               customer_ip | The customer’s IP address; where the Merchant sends as part of the authorization/ purchase request. |
|            geolocation_ip | The card for the Customer’s computer.                        |
|            customer_email | The Customer’s email; where the Merchant sends with the authorization/purchase request. |
|             acquirer_name | The name of the Acquirer.                                    |
|            payment_option | The payment option use to process the authorization/ purchase request. |
|                   channel | The FORT channel used to receive the authorization/purchase request. |
|          transaction_date | The date of the transaction.                                 |
|               card_number | The card number used to process the transaction.             |
|               expiry_date | The card’s expiry date.                                      |
|          card_holder_name | The cardholder’s name.                                       |
|                    amount | The transaction’s amount.                                    |
|                  currency | The currency of the transaction’s amount in ISO code 3.      |
|                  card_bin | The bank identification number (BIN); which is the initial four to eight numbers that appear on a credit card. |
|                       eci | The E-commerce indicator associated with the transactions authorization/ purchase request. |
|                 operation | The operation type (authorization, purchase, void authorization, capture, and refund) |
|                token_name | The Token associated with the card used to process the transaction. |
|             3ds_indicator | This indicator will hold the value “yes” in case 3-D Secure check was performed on a specific transaction. Otherwise, it will holds the value “no”. |
|           fraud_indicator | This indicator will hold the value “yes” in case fraud check was performed on a specific transaction. Otherwise, it will holds the value “no”. |
|    installments_indicator | This indicator will hold the value “yes” in case installments service was applied on a specific transaction. Otherwise, it will holds the value “no”. |
|                    status | A two-digit numeric value that indicates the status of the transaction. |
|             response_code | Carries the value of our system’s response.                  |
|          response_message | The Message description of the response code. It returns according to the request language. |
|       third_party_message | The message retrieved from the third party.                  |
|          third_party_code | The code retrieved from the third party.                     |
|                order_date | The creation date of the order.                              |
|         order_description | The description of the order provided by the merchant.       |
|              acquirer_mid | The Acquirer Merchant identifier.                            |
|    acquirer_response_code | The code the Acquirer returns.                               |
| acquirer_response_message | The code the Acquirer returns.                               |
|   processor_response_code | The code the Acquirer returns.                               |
|                 sadad_olp | SADAD Online Payment ID Alias. The value that SADAD’s Customer provides to process SADAD order. |
|      sadad_transaction_id | The identifier returned by SADAD for a specific SADAD transaction. |
|           payment_link_id | Payment link unique identifier.                              |
|                Invoice_id | The identification for a specific subscription service.      |
|            digital_wallet | The buyer’s digital wallet.                                  |

### Filters Parameter

**Include the following parameters into “filters” parameter you will send to PayFort:**

|                    ATTRIBUTES | Description                                                  |
| ----------------------------: | :----------------------------------------------------------- |
| **key** Alphanumeric max: 110 | The name of the column you want to filter. You can choose more than one. Possible/ expected values: (Please refer to section [Key parameter](https://docs.payfort.com/docs/api/build/index.html?ruby#key-parameter)). Special characters: # `' `\ / . _ - @ : **Space** |
| **value** Alphanumeric max: - | The value of the key you want to revert in your response. It depends on the key you have chosen to revert. |

### Key Parameter

**The following table contains all the possible values of the “key” parameter, you can choose any of them:**

|                       Key | Description & Possible Values                                |
| ------------------------: | :----------------------------------------------------------- |
|                   fort_id | The order’s unique reference returned by our system.         |
|        merchant_reference | The Merchant’s unique order number.                          |
|        authorization_code | The authorization code returned from the 3rd party responsible for processing the transaction. |
|             customer_name | The Customer’s name.                                         |
|               customer_ip | The customer’s IP address; where the Merchant sends as part of the authorization/ purchase request. |
|            geolocation_ip | The card for the Customer’s computer.                        |
|            customer_email | The Customer’s email; where the Merchant sends with the authorization/purchase request. |
|             acquirer_name | The name of the Acquirer.                                    |
|            payment_option | The payment option use to process the authorization/ purchase request. Possible/ Expected Values: - MASTERCARD - VISA - AMEX - SADAD - NAPS - KNET - MADA - MEEZA |
|                   channel | The FORT channel used to receive the authorization/purchase request. Possible/ Expected Values: - MOTO - Trusted - Merchant Page - Redirection - eTerminal - Recurring |
|          transaction_date | The date of the transaction.                                 |
|               card_number | The card number used to process the transaction.             |
|               expiry_date | The card’s expiry date.                                      |
|          card_holder_name | The cardholder’s name.                                       |
|                    amount | The transaction’s amount.                                    |
|                  currency | The currency of the transaction’s amount in ISO code 3.      |
|                  card_bin | The bank identification number (BIN); which is the initial four to eight numbers that appear on a credit card. |
|                       eci | The E-commerce indicator associated with the transactions authorization/ purchase request. Possible/ Expected Values: - ECOMMERCE - RECURRING - MOTO |
|                 operation | The operation type (authorization, purchase, void authorization, capture, and refund). |
|                token_name | The Token associated with the card used to process the transaction. |
|             3ds_indicator | This indicator will hold the value “yes” in case 3-D Secure check was performed on a specific transaction. Otherwise, it will holds the value “no”. Possible/ Expected Values: - YES - NO |
|           fraud_indicator | This indicator will hold the value “yes” in case fraud check was performed on a specific transaction. Otherwise, it will holds the value “no”. Possible/ Expected Values: - YES - NO |
|    installments_indicator | This indicator will hold the value “yes” in case installments service was applied on a specific transaction. Otherwise, it will holds the value “no”. Possible/ Expected Values: - YES - NO |
|                    status | A transaction status value that indicates the status of the transaction. |
|             response_code | Carries the value of our system’s response.                  |
|          response_message | The Message description of the response code. It returns according to the request language. |
|       third_party_message | The message retrieved from the third party.                  |
|          third_party_code | The code retrieved from the third party.                     |
|                order_date | The creation date of the order.                              |
|         order_description | The description of the order provided by the merchant.       |
|              acquirer_mid | The Acquirer Merchant identifier.                            |
|    acquirer_response_code | The code the Acquirer returns.                               |
| acquirer_response_message | The code the Acquirer returns.                               |
|   processor_response_code | The code the Acquirer returns.                               |
|                 sadad_olp | SADAD Online Payment ID Alias. The value that SADAD’s Customer provides to process SADAD order. |
|      sadad_transaction_id | The identifier returned by SADAD for a specific SADAD transaction. |
|           payment_link_id | Payment link unique identifier.                              |
|                Invoice_id | The identification for a specific subscription service.      |
|            digital_wallet | The buyer’s digital wallet. Possible/ Expected Values: - MASTERPASS - VISA_CHECKOUT - APPLE_PAY |



------



## Generate Report - Response

**The following parameters will be returned in PayFort’s Response:**

|                                   ATTRIBUTES | Description                                                  |
| -------------------------------------------: | :----------------------------------------------------------- |
|              **query_command** Alpha max: 50 | Query operations command. Possible/ expected values: GENERATE_REPORT |
|         **access_code** Alphanumeric max: 20 | Merchant account Access Code. Example: zx0IPmPy5jp1vAz8Kpg7  |
| **merchant_identifier** Alphanumeric max: 20 | FORT Merchant Account identifier. Example: CycHZxVj          |
|  **merchant_reference** Alphanumeric max: 40 | The Merchant’s unique reference for a specific request. Example: XYZ9239-yu898 |
| **from_date** Alphanumeric Mandatory max: 30 | Query parameter to filter from a specific date. Example: 2017-01-01T14:36:55+03:00 |
|   **to_date** Alphanumeric Mandatory max: 30 | Query parameter to filter the results till a specific date. Example: 2017-06-28T14:36:55+03:00 |
|          **signature** Alphanumeric max: 200 | A string hashed using the Secure Hash Algorithm. (Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?ruby#signature) for more details). Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                    **language** Alpha max: 2 | The checkout page and messages language. Possible/ expected values: en / ar |
|             **response_format** Alpha Max: 4 | The FORT response format; weather its JSON or XML. *The default response format is “JSON”. Possible/ expected values: - JSON - XML |
|   **response_message** Alphanumeric max: 150 | Message description of the response code. It returns according to the request language. Example: Insufficient Funds |
|             **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?ruby#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?ruby#messages). Example: 56000 |
|                    **status** Numeric max: 2 | A two-digit numeric value that indicates the status of the transaction Possible/ expected values: (Please refer to section [statuse](https://docs.payfort.com/docs/api/build/index.html?ruby#statuses) |