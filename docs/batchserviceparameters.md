# Batch Service Request and Response Parameters

------

### Upload Batch File - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory Max: 20 | Command. Possible/ expected values: UPLOAD_BATCH_FILE Special characters: _ |
|         **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|     **batch_reference** Alphanumeric Mandatory Max: 20 | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . / |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|                **file** Alphanumeric Mandatory Max: 50 | The file that contain a batch of transactions. The file should be of type CSV. Example: test.csv Special characters: . - ! @ # $ % ^ & ( ) _ + , **Space** |
|          **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |

------

### Upload Batch File - Response

**The following parameters will be returned in PayFort’s Response:**

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|             **service_command** Alpha Max: 20 | Command. Possible/ expected values: UPLOAD_BATCH_FILE        |
|          **access_code** Alphanumeric Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
|  **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|      **batch_reference** Alphanumeric Max: 20 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                     **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|                  **batch_id** Numeric Max: 20 | The Merchant’s unique batch ID. Example: 150754364000030895  |
| **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|    **response_message** Alphanumeric Max: 150 | The message description of the response code; it returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages) |
|              **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). Example: 50000 |
|                     **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses) |

------

### Get Batch Results - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory Max: 20 | Command. Possible/ expected values: GET_BATCH_RESULTS Special characters: _ |
|         **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|     **batch_reference** Alphanumeric Mandatory Max: 20 | The Merchant’s unique order number. *You have to use the same batch reference you used in the upload_batch_file. Example: XYZ9239-yu898 Special characters: - _ . / |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|          **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                  **batch_id** Numeric Optional Max: 20 | The Merchant’s unique batch ID returned when uploading a file successfully. Example: 150754364000030895 |

 **Get Batch Results Request Example!**
{
“merchant_identifier”:“bxgOIxIz”,
“access_code”:“1DFxVvhXWV6wumenTTg9”,
“signature”:“17e62207b17ea9f550b41811039cb4a05f86087c5cdec40aad1dcc250909b054”,
“service_command”:“GET_BATCH_RESULTS”,
“batch_reference”:“batch180”,
“language”:“en”,
“batch_id” : “151791753100095172”
}



### Get Batch Results - Response

**The following parameters will be returned in PayFort’s Response:**

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|             **service_command** Alpha Max: 20 | Command. Possible/ expected values: GET_BATCH_RESULTS        |
|          **access_code** Alphanumeric Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
|  **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|      **batch_reference** Alphanumeric Max: 20 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                     **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
| **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                  **batch_id** Numeric Max: 20 | The Merchant’s unique batch ID. Example: 150754364000030895  |
|        **transactions_count** Numeric Max: 10 | A parameter that counts the total number of transactions inside the file. Example: 9 |
|    **response_message** Alphanumeric Max: 150 | The message description of the response code; it returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages) |
|              **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). Example: 70000 |
|                     **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: Please refer to section [statuses]( |

------

### Process Batch File - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                             ATTRIBUTES | Description                                                  |
| -----------------------------------------------------: | :----------------------------------------------------------- |
|            **service_command** Alpha Mandatory Max: 20 | Command. Possible/ expected values: PROCESS_BATCH Special characters: _ |
|         **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
| **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|     **batch_reference** Alphanumeric Mandatory Max: 20 | The Merchant’s unique order number. *You have to use the same batch reference you used in the upload_batch_file. Example: XYZ9239-yu898 Special characters: - _ . / |
|                    **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|          **signature** Alphanumeric Mandatory Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                  **batch_id** Numeric Optional Max: 20 | The Merchant’s unique batch ID returned when uploading a file successfully. Example: 150754364000030895 |