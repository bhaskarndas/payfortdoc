# What is Bypass?

---

The Bypass consists of security system which combines the features of 3-D secure services. This ensures that your account has additional layer of security services which will authenticate every transaction being carried out by the customers on your site. This will not only safeguard the interests of the customers but also safeguard you from potential fraud and threats from novel scammers. The Bypass consists of 3-D secure services and cvv suppression. This section explains the complete 3-D Secure services and cvv suppression.

---

# 3-D Secure services Overview

------

The 3D Secure (3DS) protocol, commonly known by its branded names [Verified by Visa](https://www.visa.co.uk/products/protection-benefits/verified-by-visa/), [Mastercard SecureCode](https://www.mastercard.co.uk/en-gb/consumers/features-benefits/securecode.html), [American Express SafeKey](https://www.americanexpress.com/uk/benefits/service-security/safety-fraud/how-amex-protects-you/safekey/), introduced an additional layer of verification to protect you from liability for fraudulent card payments and make online payments more secure.

Placeholder: Visual graphs and pictures to be added that displays the complete 3-D secure services

3-D Secure services is an extra authentication service to authenticate the transaction by sending an OTP to the card holder from the issuer bank then the card holder have to authenticate the transaction by entering this OTP on the 3DS page. There are two types of 3-D Secure Services:

1. [Check 3-D Secure & Flex 3-D Secure Services:](https://docs.payfort.com/docs/api/build/index.html?shell#check-3-d-secure-amp-flex-3-d-secure-services)

     
     
2. [External MPI & Expose 3-D Secure services:](https://docs.payfort.com/docs/api/build/index.html?shell#external-mpi-amp-expose-3-d-secure-services)

     ------
     
     

## Check 3-D Secure & Flex 3-D Secure Services

### Check 3-D Secure Service

This service provides cardholders a decreased risk of other people being able to use their payment cards fraudulently on the Merchant’s site.

Placeholder: Integration flow diagram to be added along with the sample php/java/ruby/curl code for check 3-D secure service request being sent to PayFORT.

For details on input parameters please visit the [link](bypassparameters.md)

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>PayFort’s Operations team must activate the 3-D Secure service.</div>

------



### Flex 3-D Secure Service

This service gives you the flexibility to downgrade the 3-D Secure authentication in the transaction processing, based on a set of rules of your choice. You can active/ deactivate this service under the “Flex Management” tab on your FORT Back-office.





Placeholder: Provide steps to activate/deactivate the service in the back office.

**How it Works?**

Placeholder: Provide visual presentation/Integration/process flow diagram alongwith description.

Placeholder: Provide Backoffice snapshot of the "Flex Management Tab"

Click on the <mark>Flex Management</mark> tab on the main menu of your PayFORT Back-office. The following tabs should be displayed:
• **Service configuration:** allows you to activate/ deactivate the flex service after you accept the terms and conditions.
• **List management:** allows you to add multiple lists with different list types (email, IP, BIN, custom field and country) through <mark>Add New List</mark>.
• **Rules Management:** sets the required rules for flex Management by your choice.
• **Audit log:** Provides logs of triggered actions by you in configurations of the Flex service.



Placeholder: Provide sample code for request sent to PayFORT for Flex 3-D secure service.

For details on input parameters please visit the [link](bypassparameters.md)



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>This Service is only available for eci = ECOMMERCE transactions (Redirection, Trusted, SDK, Merchant page and Merchant page 2.0) and credit cards (Visa, MasterCard and Amex).</div>

------



## External MPI & Expose 3-D Secure services

### External MPI 3-D Secure Service

This service allows the payFort system to accept Purchase/ Authorization transactions in which the 3ds check was done externally using an external MPI.

Placeholder: Provide integration flow diagram alongwith description.

### Endpoints

**Sandbox:**

```http
POST https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

**Live**

```http
POST https://paymentservices.PayFort.com/FortAPI/paymentApi
```

### Parameters Submission Type

REST POST request using JSON.

------



### External MPI 3-D Secure - Request

Placeholder: Provide sample code for External MPI 3-D Secure - Request

For details on input parameters please visit the [link](bypassparameters.md)



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i> Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>

---

### External MPI 3-D Secure - Response

Placeholder: Provide sample JSON response sent by PayFORT system.





For details on response parameters please visit the [link](bypassparameters.md)



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

---

### Expose 3-D Secure Service

This service allows you to use the 3-D Secure service in standalone request without the transaction purchase/Authorization flow, the user 3-D Secure Authentication can be done separately to get the user Authentication data and then you can perform the charge request <mark><em>Authorization/Purchase</em></mark> in another request.



Placeholder: Provide Integration flow/process flow diagram alongwith description if applicable.

### Endpoints

**Sandbox**

```http
POST https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

**Production Environment URL:**

```http
POST https://paymentservices.PayFort.com/FortAPI/paymentApi
```

----

### Parameters Submission Type

REST POST request using JSON.

----

### 3-D Secure Enrollment Service Command - Request

For details on input parameters please visit the [link](bypassparameters.md)

placeholder: Sample code to be inserted for the request.

**3-D Secure Enrollment Request Example in JSON file**

```json
{
“merchant_reference”:“XYZ9239-yu898”,
“access_code”:“zx0IPmPy5jp1vAz8Kpg7”,
“service_command”:“3DS_ENROLLMENT”,
“language”:“en”,
“merchant_identifier”:“CycHZxVj”,
“currency”:“AED”,
“amount”:“10000”,
“card_number”:“4005550000000001”,
“expiry_date”:“2105”,
“merchant_3ds_url”:“https://www.merchant.com”,
“signature”:“a10048ca30a401d798f236bbdeb8b63a3a944449fafa9af2dee28eb6054dc07e”
}
```

---

### 3-D Secure Enrollment Service Command - Response

For details on response parameters please visit the [link](bypassparameters.md)



**3-D Secure Enrollment Response sent by PayFORT**

```json
{
“amount”: “10000”,
“response_code”: “44000”,
“card_number”: “400555******0001”,
“signature”: “44d80139e9557661822c2e2d571983cc84a2de5a85e7499835dffd19f6192040”,
“merchant_identifier”: “CycHZxVj”,
“access_code”: “zx0IPmPy5jp1vAz8Kpg7”,
“expiry_date”: “2105”,
“merchant_3ds_url”: “https://www.merchant.com”,
“language”: “en”,
“threeds_id”: “153606397100001061”,
“3ds_url”: “https://migs.mastercard.com.au/vpcpay?paymentId=3499269050937443526&DOID=E870F0B65189A7128A86B7FC206F136E&o=pt&action=retry”,
“service_command”: “3DS_ENROLLMENT”,
“response_message”: “Success”,
“merchant_reference”: “XYZ9239-yu898”,
“3ds_enrolled”: “Y”,
“currency”: “AED”,
“status”: “44”
}
```



After you get back a 3Ds Enrollment response that includes the parameter <mark>3ds_enrolled</mark> of value <mark>Y</mark> follow the steps for the 3Ds Authentication request:

1. In case you are on <mark>MIGS</mark> processor, copy the returned 3ds_url in a new browser. Then, select all the returned parameters to be send in the next request “3Ds Authentication”.

2. In case you are on "Cybersource”/ “MPGS” processor; two parameters will returns in the “3Ds Enrollment”; as below:
     • MD
     • PaRes
   And you have to copy them in the “3Ds Authentication” request; as you will see in the 3Ds Authentication request example.
   
   ----
   
   
   
   

## 3-D Secure Authentication Service 

Placeholder: Provide process flow diagram along with description.

------



### Endpoints

**Sandbox**

```http
POST https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

**Live**

```http
POST https://paymentservices.PayFort.com/FortAPI/paymentApi
```

---

### Parameters Submission Type

REST POST request using JSON.

---

### 3-D Secure Authentication Service Command - Request

For details on input parameters please visit the [link](bypassparameters.md)

**Include the following parameters in the Request you will send to PayFort:**3-D Secure Authentication Request on MIGS processor Example!**

```json
{
“access_code”:“zx0IPmPy5jp1vAz8Kpg7”,
“service_command”:“3DS_AUTHENTICATION”,
“language”:“en”,
“merchant_identifier”:“bxgOIxIz”,

“third_party_body”:“vpc_3DSECI=05&vpc_3DSXID=6kQGHEiZDU0H4+mUWF7zELHAcqM=&vpc_3DSenrolled=Y&vpc_3DSstatus=Y&vpc_Amount=1000&vpc_BatchNo=0&vpc_Command=pay&vpc_Currency=USD&vpc_Locale=en_SA&vpc_MerchTxnRef=153615472100001289&vpc_Merchant=TEST81002&vpc_Message=Approved&vpc_OrderInfo=153615472100001289&vpc_SecureHash=5E22F556A03C3ED90065DDBDA51577D4FAFF45BD858C3587D6589E69953C5615&vpc_SecureHashType=SHA256&vpc_TransactionNo=0&vpc_TxnResponseCode=0&vpc_VerSecurityLevel=05&vpc_VerStatus=Y&vpc_VerToken=gIGCg4SFhoeIiYqLjI2Oj5CRkpM=&vpc_VerType=3DS&vpc_Version=1”,

“merchant_reference”: “XYZ9239-yu898”,
“signature”:“5342edd1b7f34cd7b2be93487f1b80e86a2266f78e274c9bde6b2c1b1eca0f20”
}
```

**3-D Secure Authentication Request on Cybersource/ MPGS Processors Example!**

```json
{
“access_code”:“zx0IPmPy5jp1vAz8Kpg7”,
“service_command”:“3DS_AUTHENTICATION”,
“language”:“en”,
“merchant_identifier”:“CycHZxVj”,



“third_party_body”:“MD=153354476300012267&PaRes=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”,

“merchant_reference”: “XYZ9239-yu898”,
“signature”:“714ae368b706be6db4073e75bd58e8feada61736edc7a07c0e59e3c9071ad2d5”
}
```

---



### 3-D Secure Authentication Service Command - Response

Placeholder: Provide sample Json response sent by PayFORT.

For details on input parameters please visit the [link](bypassparameters.md)

**3Ds Authentication Response on MIGS Processor Example!**

```json
{
“response_code”: “44000”,
“signature”: “1f87e311965bf27cd497396420eb9c7abe5bfac14d17eb09904517ec86ee2caa”,
“merchant_identifier”: “CycHZxVj”,
“ver_token”: “gIGCg4SFhoeIiYqLjI2Oj5CRkpM=”,
“access_code”: “zx0IPmPy5jp1vAz8Kpg7”,
“language”: “en”,
“3ds_eci”: “05”,
“threeds_id”: “153606397100001061”,
“3ds_status”: “Y”,
“service_command”: “3DS_AUTHENTICATION”,
“response_message”: “Success”,
“3ds_xid”: “6kQGHEiZDU0H4+mUWF7zELHAcqM=”,
“merchant_reference”: “XYZ9239-yu898”,
“3ds_enrolled”: “Y”,
“status”: “44”
}
```

**3-D Secure Authentication Response on Cybersource/ MPGS Processors Example!**

```json
{
“response_code”: “44000”,
“signature”: “1f87e311965bf27cd497396420eb9c7abe5bfac14d17eb09904517ec86ee2caa”,
“merchant_identifier”: “CycHZxVj”,
“ver_token”: “gIGCg4SFhoeIiYqLjI2Oj5CRkpM=”,
“access_code”: “zx0IPmPy5jp1vAz8Kpg7”,
“language”: “en”,
“3ds_eci”: “05”,
“threeds_id”: “153606397100001061”,
“3ds_status”: “Y”,
“service_command”: “3DS_AUTHENTICATION”,
“response_message”: “Success”,
“3ds_xid”: “6kQGHEiZDU0H4+mUWF7zELHAcqM=”,
“merchant_reference”: “XYZ9239-yu898”,
“3ds_enrolled”: “Y”,
“status”: “44”
}
```

---

## CVV suppression

---

The CVV Suppression enables you to process the eCommerce transaction with PayFort and reduce the requirement of CVV to be part of the transaction request. In this feature the merchant can simplify and ease the user experience for the customer during the checkout . 

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i> Not all the issuing banks participate in the CVV suppression enablement as the banks in the region check the CVV usually.</div>





## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

