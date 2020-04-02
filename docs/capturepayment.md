# Capture a payment

------

This operation that allows you to **capture** the authorized amount to your account. The capture could be partial or full depends on your requirements and request.

# The request

Use the details below to set up your request.

## Endpoints

### Live

```
POST https://paymentservices.payfort.com/FortAPI/paymentApi
```

### Sandbox

```
POST https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```



<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>You can send “merchant_reference” and/ or “fort_id” in the CAPTURE request.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code.<br/>
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.<br/>
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.

</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response even the optional ones.</div>

## Request example

```json
{
'command':'CAPTURE',
'access_code':'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier':'CycHZxVj',
'merchant_reference':'XYZ9239-yu898',
'amount':'10000',
'currency':'AED',
'language':'en',
'fort_id':'149295435400084008',
'signature':'7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'order_description':'iPhone 6-S',
};
```

#  The response

------

If you receive response code `20064` with status code `04` then your request to capture a payment has been accepted by the PayFort Server.

### Response examples

```json
{"command":"CAPTURE",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239-yu898",
 "amount":"10000",
 "currency":"AED",
 "language":"en",
 "fort_id":"149295435400084008",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "order_description":"iPhone 6-S",
 "response_message":"Success",
 "response_code":"20064",
 status":"04"
}
```

You can check out various transaction codes by visiting this [link](transactioncodes.md)

# Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).