# What is Recurring?

------

**Recurring** transactions allows the Merchant to charge Customer’s card a specific amount on regular basis using the [Purchase operation](https://docs.payfort.com/docs/api/build/index.html#recurring-request) configured in single message mode. For example, the Merchant will be charging his Customer’s card the subscription fee on monthly basis.

------

## How It Works - Overview

1. The Merchant has to have a Token created assigned to a specific Customer account. For more details on “Token” please refer to the [FORT Tokenization Service.](https://docs.payfort.com/docs/api/build/index.html#fort-tokenization-service)
2. The Merchant’s server sends the recurring transaction details along with the Customer’s Token to PayFort.
3. The transaction is processed and a valid response is returned to the Merchant servers indicating the status of the transaction.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>The Token used to process recurring transactions, should be created when processing a successful transaction using an e-commerce MID registered for the same legal entity the recurring MID is configured for.</div>

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Issuers will charge the customer’s card if the card was used to process a successful e-commerce transaction for that merchant prior to the recurring transaction.</div>

------

### Endpoints

**Sandbox**

```http
POST  https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

**Live**

```http
POST  https://paymentservices.payfort.com/FortAPI/paymentApi
```

------

### Parameters Submission Type

REST POST request using JSON.

------

## The Request

The sample JSON Request

```json
{"command":"PURCHASE",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239yu898",
 "amount": "10000",
 "currency": "AED",
 "language":"en",
 "customer_email":"customer@domain.com",
 "eci":"RECURRING",
 "token_name":"Op9Vmp",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "payment_option":"MASTERCARD",
 "order_description":"iPhone6-S",
 "customer_ip":"192.178.1.10",
 "customer_name":"John Smith",
 "phone_number":"00962797219966",
 "settlement_reference":"XYZ9239-yu898",
 "merchant_extra":"JohnSmith",
 "merchant_extra1":"JohnSmith",
 "merchant_extra2":"JohnSmith",
 "merchant_extra3":"JohnSmith",
 "merchant_extra4":"JohnSmith",
 "merchant_extra5":"JohnSmith",
 "return_url":"http://www.merchant.com"
}
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

## The Response

------

Here is the response example

```json
{"command":"PURCHASE",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239yu898",
 "amount":"10000",
 "currency":"AED",
 "language":"en",
 "customer_email":"customer@domain.com",
 "eci":"RECURRING",
 "token_name":"Op9Vmp",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "order_description":"iPhone6-S",
 "fort_id":"149295435400084008",
 "payment_option":"MASTERCARD",
 "customer_ip":"192.178.1.10",
 "customer_name":"John Smith",
 "authorization_code":"P1000000000000372136",
 "response_message":"Success",
 "response_code":"20064",
 "status":"04",
 "expiry_date":"2105",
 "card_number":"400555******0001",
 "phone_number":"00962797219966",
 "settlement_reference":"XYZ9239-yu898",
 "merchant_extra":"JohnSmith",
 "merchant_extra1":"JohnSmith",
 "merchant_extra2":"JohnSmith",
 "merchant_extra3":"JohnSmith",
 "merchant_extra4":"JohnSmith",
 "merchant_extra5":"JohnSmith",
 "return_url":"http://www.merchant.com"
}
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones.</div>

# Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

