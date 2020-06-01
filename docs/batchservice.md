# Batch Service

On several occasions you will be required to perform tasks in batches. PayFORT <mark>Batch Service</mark> allows you to process requests in bulk as a batch. One example that  can fits the description of batch service is the bulk invoice generation.  This service reduces the time and manual effort required as in case of one to one service. For example creating a invoice for 100 customers for same product with same price increases the effort if done in single units, however batch service reduces the effort by perform the operation in one go.

------

## Before You Start

You have to bear in mind certain conditions while performing Batch Operations. Here they are:

1. You’re only allowed to send one of the following transactions in your batch file or a mixture of them:

   - Recurring Transactions:

     In the recurring transactions PURCHASE command should be sent while performing bulk operations.

   - Maintenance operations (capture, refund , and void authorization) 

     You can perform any of the maintenance operations for bulk processing of transactions after completing a successful Authorization or Purchase transactions through one of PayFort’s channels.

2. You should activate the Batch processing service to process the transactions in bulk.

   ------

   

## How it works 

The batch service works in three steps. The following steps describes how batch processing service works.

Placeholder: Provide process flow/Integration flow diagram along with description.

1. **Upload Batch File**
   This request allows you to upload the batch file to the PayFORT system.

2. **Get Batch Results**
   This request allows you to validate the format of the file and to check that the merchant reference for each and every transaction is unique.

3. **Process Batch File**
   This request allows you to initiate the processing of transactions(recurring,maintenance or combination of both). In order to start the processing the file should have been validated and passed the validation process.

   ------

   

## Upload Batch file

This request allows you to upload the Batch file to the PayFORT system. You will specify the order of the fields in the batch file. Then you will receive a success message (response code: 50000) indicating that the batch file uploaded successfully at PayFORT side. Then Payfort will start the validation process on the uploaded file

### Endpoints

**Sandbox**

```http
POST https://sbpaymentservices.payfort.com/FortAPI/upload/
```

**Live**

```http
POST https://paymentservices.payfort.com/FortAPI/upload/
```

------



### Parameters Submission Type

Host to Host Form Post Request (From the backend)



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Make sure to add the action, method and enctype properties on the form tag as shown below:</div>

***

```html
<form action=“https://sbpaymentservices.payfort.com/FortAPI/upload/” method=“POST” enctype=“multipart/form-data”>
```

------



### Upload Batch File - Request

------

The first process in the Batch processing is Upload Batch File request to PayFORT system. The below html sample code describes how to create a request for bulk upload to the PayFORT. You can visit the [link](batchserviceparameters.md) to learn more about input parameters for the request.

 Upload Batch Request Example!

```html
<html><body>
    <form action="https://sbpaymentservices.payfort.com/FortAPI/upload" method="POST" enctype="multipart/form-data">
        <input type="text" name="merchant_identifier" value="bxgOIxIz" />
        <input type="text" name="access_code" value="1DFxVvhXWV6wumenTTg9" />
        <input type="text" name="service_command" value="UPLOAD_BATCH_FILE" />
        <input type="text" name="batch_reference" value="batch180" />
        <input type="text" name="language" value="en" />
        <input type="text" name="signature" value="9bea9f369473b8355b2c32884f4b2e8425b145b10d647c2fcaeeee79d7f86fdc" /><input type="file" name="file" accept="test.csv">
        <input type="submit">
    </form>
    </body></html>
```



### Upload Batch File - Response

------

Here is the sample JSON response sent by the PayFORT server  with <mark>response_code</mark> as <mark>50000</mark> indicating successful upload.

```json
{“response_code”:“50000”,
 “service_command”:“UPLOAD_BATCH_FILE”,
 “response_message”:“Success”,
 “batch_id”:“151791753100095172”,
 “signature”:“a8888a646b30f756a4f7ce892574e9da7342d7833c3b83cf6f2393978430d74f”,
“merchant_identifier”:“bxgOIxIz”,
 “access_code”:“1DFxVvhXWV6wumenTTg9”,
“batch_reference”:“batch180”,
 “language”:“en”,
 “status”:“50”}
```

------

## Get Batch Results

------

Once the batch upload operation has been successfully completed next batch operation is to fetch batch results. This request allows you to validate the format of the file and to check that the merchant reference for each and every transaction is unique. In the response of this request the merchant will receive the batch file validation results such as (Batch validation successfully, Validation done with errors, The Batch file still under validation)

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>The batch file cannot be processed if the validation status is (The Batch file still under validation).</div>

------



### Endpoints

**Sandbox**

```http
POST https://sbpaymentservices.payfort.com/FortAPI/batchApi/
```

**Live**

```http
POST https://paymentservices.payfort.com/FortAPI/batchApi/
```



------



### Parameters Submission Type

REST POST request using JSON.

------



### Get Batch Results - Request

The below JSON sample file describes how to create a request for fetching batch results from the PayFORT. You can visit the [link](batchserviceparameters.md) to learn more about input parameters for the request.



 **Get Batch Results Request Example!**

```json
{
“merchant_identifier”:“bxgOIxIz”,
“access_code”:“1DFxVvhXWV6wumenTTg9”,
“signature”:“17e62207b17ea9f550b41811039cb4a05f86087c5cdec40aad1dcc250909b054”,
“service_command”:“GET_BATCH_RESULTS”,
“batch_reference”:“batch180”,
“language”:“en”,
“batch_id” : “151791753100095172”
}
```

------



### Get Batch Results - Response

Once the Batch Results have been requested from PayFORT you will receive a response similar to the sample shown here:

 Sample JSON response sent by PayFORT server

```json
{
“transactions_count”: “9”,
“response_code”: “70000”,
“service_command”: “GET_BATCH_RESULTS”,
“response_message”: “Success”,
“batch_id”: “151791753100095172”,
“signature”: “036823f98cfca2a1b7efcf7552dd87fc44df666fc345d553ce733efb2003f5cd”,
“merchant_identifier”: “bxgOIxIz”,
“access_code”: “1DFxVvhXWV6wumenTTg9”,
“batch_reference”: “batch180”,
“language”: “en”,
“status”: “70”
}
```



## Process Batch file

The last step in Batch Processing is to process the uploaded batch file for transaction. This request allows you to initiate the processing of transactions. In order to start processing, the file should have been validated and passed the validation successfully regarding less the validation done without/with errors.

------



### Endpoints

**Sandbox**

```http
POST https://sbbatch.payfort.com/integration-batch/batchApi/
```

**Live**

```http
POST https://paymentservices.payfort.com/FortAPI/batchApi/
```

------



### Parameters Submission Type

REST POST request using JSON.

------



### Process Batch File - Request

The below JSON sample file describes how to create a request for processing the batch file . You can visit the [link](batchserviceparameters.md) to learn more about input parameters for the request.

 **Process Batch Request Example!**

```json
{
“merchant_identifier”:“bxgOIxIz”,
“access_code”:“1DFxVvhXWV6wumenTTg9”,
“signature”:“17e62207b17ea9f550b41811039cb4a05f86087c5cdec40aad1dcc250909b054”,
“service_command”:“PROCESS_BATCH”,
“batch_reference”:“batch180”,
“language”:“en”,
“batch_id” : “151791753100095172”
}
```

------



### Process Batch File - Response

PayFORT will return the response in the form of JSON format and the <mark>response_code</mark> as <mark>72147</mark> stating that the batch file has been processed successfully for the transaction.

 **Process Batch Response Example!**

```json
{
“response_code”:“72147”,
“service_command”:“PROCESS_BATCH”,
“response_message”:“Process batch request received”,
“signature":“ee1d30d4fcc6f61100cca0a5ee0639e3c22620ae88d6dc7ec2b6aad2a2489184”,
“merchant_identifier”:“bxgOIxIz”,
“access_code”:“1DFxVvhXWV6wumenTTg9”,
“batch_reference”:“batch180”,
“language”:“en”,
“status”:“72”
}


```

------

Now you can initiate Get Batch Results Request once again to see final status for each transaction within the processed batch file. PayFORT will send the response example as shown below



```
Line_Number,response_code,response_message,status,eci,fort_id,merchant_reference,
amount,card_number,expiry_date,currency “5”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095202”,“newww33”,“10003”,
“400555******0001”,“2105”,“USD”
“4”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095203”,“newww32”,“10002”,
“400555******0001”,“2105”,“USD”
“10”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095208”,“newww38”,“10008”,
“400555******0001”,“2105”,“USD”
“8”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095204”,“newww36”,“10006”,
“400555******0001”,“2105”,“USD”
“9”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095205”,“newww37”,“10007”,
“400555******0001”,“2105”,“USD”
“2”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095206”,“newww30”,“10000”,
“400555******0001”,“2105”,“USD”
“6”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095201”,“newww34”,“10004”,
“400555******0001”,“2105”,“USD”
“7”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095207”,“newww35”,“10005”,
“400555******0001”,“2105”,“USD”
“3”,“14000”,“Success”,“14”,“RECURRING”,“151792390600095200”,“newww31”,“10001”,
“400555******0001”,“2105”,“USD”
```

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

