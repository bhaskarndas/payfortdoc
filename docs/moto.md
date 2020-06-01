# MOTO Channel

------

Now your customers can make transactions through mobile and Telephone orders also. **MOTO** (Mobile Order/ Telephone Order) channel allows the you to process MOTO transactions through the FORT API using credit card Tokens ONLY. 

Whenever any customer places an order in your site he/she can carry out transactions over the telephone and cellphone IVR.

## Endpoints

**Sandbox**

```http
POST  https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

**Live**

```http
POST  https://paymentservices.PayFort.com/FortAPI/paymentApi
```



------

## Parameters Submission Type

REST POST request using JSON.

------

## The Request

The sample JSON Request

Placeholder: Provide Sample code for MOTO request.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
    Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>
For input parameters please visit the [link](motoparameters.md)

## The Response

------

Here is the response that would be sent by PayFORT to the request sent to it for MOTO transactions.

```json
{"command":"PURCHASE",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239yu898",
 "amount":"10000",
 "currency":"AED",
 "language":"en",
 "customer_email":"customer@domain.com",
 "eci":"MOTO",
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

