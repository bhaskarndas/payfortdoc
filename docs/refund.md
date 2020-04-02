# Refund a payment

------

This operation **returns** the entire amount of a transaction or part of it AFTER being captured.

## The request

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

### Request example

#### JSON

```json
{
'command':'REFUND',
'access_code':'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier':'CycHZxVj',
'merchant_reference':' XYZ9239-yu898',
'amount':'10000',
'currency':'AED',  
'language':'en',
'signature':'7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'fort_id':'149295435400084008',
'order_description':'iPhone 6-S',
}
```

##  The response

------

If you receive status code `20064` with status code `04` it means your request for refund has been accepted by the PayFort Server. The response sent by the server will be in the format of JSON.

### Response examples

```json
{"command":"REFUND",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239-yu898",
 "amount":"10000",
 "currency":"AED",
 "language":"en",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "fort_id":"149295435400084008",
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