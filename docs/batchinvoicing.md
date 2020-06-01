## One to Many (Batch Invoicing)

------

PayFORT also allows you to generate and upload bulk of invoice to PayFORT as a batch. This service helps you to serve several customers in one go. For example sending bulk invoices to customers for fixed price item. Batch invoicing works on similar principle of [Batch Service](batchservice.md). There are two types of invoicing services which you can use as per your business requirement. This section describes one to many or batch invoicing service. For one to one invoice generation visit this [link](invoicing.md). 

------

### Before You Start

Before starting you have to know the following:

1. You’re only allowed to send <mark>PAYMENT_LINK</mark> service command in the invoice batch file.
2. You should active the Batch processing and invoicing services.
3. You can download the invoice batch file template from the Back office by clicking on the <mark><strong>Batch invoicing</strong></mark> tab that appears only if you activate the batch and invoicing services.

------

### Steps to activate Batch and Invoicing services

------

Provide steps to activate batch and invoicing services from the back office along with images, videos etc.

------

### Steps to download the Batch Invoicing Template

Provide steps to download batch invoicing template from the backoffice along with images, videos, etc.

------



### How it Works

Placeholder: Add Integration flow/Process flow diagram.





As Batch Invoice process applies similar steps as that of Batch service, here are steps :

1. **Upload Invoicing Batch File**
   
   This request is quite similar to the upload batch file request that you process in the [Batch Service](batchservice.md) . Only difference is that you will be uploading the batch invoicing template (which can be downloaded from the back office, provided you have activated the batch and invoicing service). This request allows you to upload the invoice batch file to PayFORT system.
   
   Please refer to the section upload batch file- request and upload batch file - response by visiting this [link](batchservice.md)

**Upload Invoicing Batch File - Request**

Placeholder: please provide sample code for the request

For more details on input parameters refer to the [link](batchserviceparameters.md)

**Upload Invoicing Batch File - Response**

Placeholder: Please provide sample response sent from the PayFORT.

2. **Get Invoicing Batch Results**
   This request is similar to the Get Batch file results request in the Batch Service. In this case you will be requesting the results of the invoicing template which has been uploaded to the PayFORT system. This request allows you to validate the format of the file and to check that the merchant reference for each and every transaction is unique. After validation the <mark>Account Administrator</mark> will receive an email notification with success invoices count.
   
   Please refer to the section get batch file results- request and get batch file results - response by visiting this [link](batchservice.md)

**Get Invoicing Batch Results - Request**

Placeholder: please provide sample code for the request

For more details on input parameters refer to the [link](batchserviceparameters.md)

**Get Invoicing Batch Results - Response**

Placeholder: Please provide sample response sent from the PayFORT.

3. **Process Invoicing Batch File**
   This is again similar to the last step in the Batch service where you process the batch file. In this case you will be requesting to process the invoicing template for further transactions. This request allows you to initiate the processing of transactions. To start the processing the file should have been validated in the Get Invoicing Batch Results-request and passed the validation process which you will be able to know from the PayFORT response. After processing the <mark>Account Administrator</mark> will receive an email notification with success invoices count.
   
   Please refer to the section process batch file- request and process batch file - response by visiting this [link](batchservice.md)

 **Process Invoicing Batch File - Request**

Placeholder: please provide sample code for the request

For more details on input parameters refer to the [link](batchserviceparameters.md)

**Process Invoicing Batch File - Response**

Placeholder: Please provide sample response sent from the PayFORT.



### Supported Schemes

------

Placeholder: Details for supported schemes to be added here.

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

