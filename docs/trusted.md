# What is Trusted?



**Trusted channel** allows PCI certified Merchants to collect their customers' credit card details on the Merchant’s checkout page. The Merchants are able to process (Ecommerce, Recurring and MOTO) transactions through the FORT using clear card data and credit card tokens.

------

## Trusted Channel Endpoints

**Sandbox**

```
POST  https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

**Live**

```
POST  https://paymentservices.PayFort.com/FortAPI/paymentApi
```

------



### Parameters Submission Type

REST POST request using JSON.

------

**JSON Request Example**

```json
{
	'command':'PURCHASE',
	'access_code':'zx0IPmPy5jp1vAz8Kpg7',
	'merchant_identifier':'CycHZxVj',
	'merchant_reference':' XYZ9239-yu898',
	'amount':'10000',
	'currency':'AED',  
	'language':'en',
    'customer_email': 'john_doe@abc.com',
    'eci': 'MOTO',
    'expiry_date': '2105',
    'card_number': '4005550000000001',
    'card_security_code': '123',
    'customer_ip': '192.178.1.10',
    'signature':'7cad05f0212ed933c9a5d5dffa31661acf2c827a',
    'card_holder_name': 'John Smith',
    'token_name': 'Op9Vmp',
    'payment_option': 'MASTERCARD',
    'order_description':'iPhone 6-S',
    'customer_name':'John Smith',
    'phone_number': '00962797219966',
    'settlement_reference': 'XYZ9239-yu898',
    'merchant_extra': 'John Smith',
    'merchant_extra1': 'John Smith',
    'merchant_extra2': 'John Smith',
    'merchant_extra3': 'John Smith',
    'merchant_extra4': 'John Smith',
    'merchant_extra5': 'John Smith',
    'return_url': 'http://www.merchant.com'

}
```

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>
    Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.
</div>

## The Response

------

You will receive sample response from the payfort server:

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
 "expiry_date":"2105",
 "card_number":"400555*****0001",
 "customer_ip":"192.178.1.10",
 "signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",
 "card_holder_name":" John Smith",
 "token_name":"Op9Vmp",
 "order_description":"iPhone6-S",
 "fort_id":"149295435400084008",
 "payment_option":"MASTERCARD",
 "customer_name": "John Smith",
 "merchant_extra":"JohnSmith",
 "merchant_extra1":"JohnSmith",
 "merchant_extra2":"JohnSmith",
 "merchant_extra3":"JohnSmith",
 "merchant_extra4":"JohnSmith",
 "merchant_extra5":"JohnSmith",
 "authorization_code":"P1000000000000372136",
 "response_message":"Success",
 "response_code":"20064",
 "status":"04",
 "3ds_url":"http://www.3dsecure.com",
 "phone_number": "00962797219966",
 "settlement_reference":"XYZ9239-yu898"
}
```

<div class="alert alert-info" role="alert"><i class="fa fa-info"></i>
    Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones.
</div>

# Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

