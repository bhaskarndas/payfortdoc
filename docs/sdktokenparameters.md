# SDK Token Parameters

------

## Request Parameters

**service_command**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/ expected values | Special Character | Description |
| -------------- | ------------------------- | ----------------- | ----------- |
| 20             | <mark>SDK_TOKEN</mark>    | <mark>_</mark>    | Command     |

------

**access_code**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example              | Description                                              |
| -------------- | -------------------- | -------------------------------------------------------- |
| 20             | zx0IPmPy5jp1vAz8Kpg7 | Merchant access code that can be found in the backoffice |

------

**merchant_identifier**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example  | Description                                     |
| -------------- | -------- | ----------------------------------------------- |
| 20             | CycHZxVj | Merchant ID that can be found in the backoffice |



------

**signature**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**language**<sup>(String, mandatory)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark>        | The checkout page and messages language where en is for english and ar for Arabic |

------

**device_id**<sup>(alphanumeric, mandatory)</sup>

| Maximum Length | Example                              | Special characters     | Description                 |
| -------------- | ------------------------------------ | ---------------------- | --------------------------- |
| 100            | ffffffff-a9fa-0b44-7b27-29e70033c587 | <mark>_ - . @ +</mark> | A unique device identifier. |

------



## Response Parameters

**service_command**<sup>(String)</sup>

| Maximum Length | Possible/ expected values | Special Character | Description |
| -------------- | ------------------------- | ----------------- | ----------- |
| 20             | <mark>SDK_TOKEN</mark>    | <mark>_</mark>    | Command     |

------

**access_code**<sup>(alphanumeric)</sup>

| Maximum Length | Example              | Description                                              |
| -------------- | -------------------- | -------------------------------------------------------- |
| 20             | zx0IPmPy5jp1vAz8Kpg7 | Merchant access code that can be found in the backoffice |

------

**merchant_identifier**<sup>(alphanumeric)</sup>

| Maximum Length | Example  | Description                                     |
| -------------- | -------- | ----------------------------------------------- |
| 20             | CycHZxVj | Merchant ID that can be found in the backoffice |



------

**signature**<sup>(alphanumeric)</sup>

| Maximum Length | Example                                  | Description                                                  |
| -------------- | ---------------------------------------- | ------------------------------------------------------------ |
| 200            | 7cad05f0212ed933c9a5d5dffa31661acf2c827a | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html#signature) |

------

**language**<sup>(String)</sup>

| Maximum Length | Possible/ expected values | Description                                                  |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| 2              | <mark>en/ar</mark>        | The checkout page and messages language where en is for english and ar for Arabic |

------

**sdk_token**<sup>(alphanumeric)</sup>

| Maximum Length | Example | Description                 |
| -------------- | ------- | --------------------------- |
| 100            | dwp78q3 | A unique device identifier. |

------

**response_message**<sup>(alphanumeric)</sup>

| Maximum Length | Possible/Expected Values                                     | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 100            | Possible/ expected values: Please refer to section [messages](transactioncodes.md) | Message description of the response code. It returns according to the request language. |

------

**response_code**<sup>(numeric)</sup>

| Maximum Length | Possible/Expected Values                                     | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 5              | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](transactioncodes.md), and the last 3 digits represent the response [messages](transactioncodes.md). | Message description of the response code. It returns according to the request language. |

------

**status**<sup>(numeric)</sup>

| Maximum Length | Possible/Expected Values                                | Description                                                  |
| -------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| 2              | Please refer to section [statuses](transactioncodes.md) | A two-digit numeric value that indicates the status of the transaction. |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>