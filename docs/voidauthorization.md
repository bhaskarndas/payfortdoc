# Void Authorization

------

After a card payment has been authorized, the payment is not complete until it has been [captured](capturepayment.md). If you do not wish to capture the payment, you can void it using the void API described below.

## The Request

------

Use the details below to set up your request.

## Endpoints

### Live

```
POST  https://paymentservices.payfort.com/FortAPI/paymentApi
```

### Sandbox

```
POST https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>You can send “merchant_reference” and/ or “fort_id” in the VOID_AUTHORIZATION request.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response even the optional ones.</div>

### The Request Example

------

#### JSON 

------

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
	'order_description':'iPhone 6-S'
  
}
```

## The Response

------

If you receive response code `20064` with status code `04` it means that your request to void authorization has been accepted by PayFort server.

### Response Example

```json
{"command":"VOID_AUTHORIZATION",
 "access_code":"zx0IPmPy5jp1vAz8Kpg7",
 "merchant_identifier":"CycHZxVj",
 "merchant_reference":"XYZ9239yu898",
 "language":"en",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "order_description":"iPhone6-S",
 "fort_id":"149295435400084008",
 "response_message":"Success",
 "response_code":"20064",
 "status":"04"
}
```

You can check out various transaction codes by visiting this [link](transactioncodes.md)

# Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

