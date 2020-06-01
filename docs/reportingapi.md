# What is Data Mine (Reporting API)?

For retail merchants like you biggest dilemma they face is to download a customized reports. These customized reports includes sales reports, transaction reports, recurring payment reports, bulk sales reports etc. If you are planning to develop your own solution then you can easily use the PayFORT's easy to use reporting API to generate your own customized reports. The Reporting API provides you the feature to generate misc.. reports that can be customized as per your business requirements. You can specify the columns to be included and filters, then download the generated report. The report is limited to 200,000 transactions. 

PayFORT provides you with two options to generate your reports one is through APIs and another through Backoffice portal. You can develop your own report generation tool and use the PayFORT endpoints to generate and download your own customized report for the business purpose.

------

## How it Works?

When you are developing the solution for report generation purpose then you need to send request to the PayFORT server using the Endpoints&nbsp;[<i class="fa fa-anchor"></i>](#endpoints). There will be two requests (<mark>Generate Report</mark> and <mark>Download Report</mark>) that you will be sending to the PayFORT server. Following steps describes the way Reporting API works:

1. You will submit <mark>***Generate Report***</mark> request for report generation. This request also allows you to specify the filters and columns to be included in the downloaded report.
2. The PayFORT server returns the <mark>**Generate Report**</mark> response.
3. You will then submit the <mark>**Download Report**</mark> request using the same <mark>*merchant reference*</mark> which was used to submit **<mark>Generate Report</mark>** request



------

## Endpoints

You can use these PayFORT endpoints for the purpose of testing and going live. If you don't have test account then you can use this [link](https://www.payfort.com/test-account/) to signup for the test account else you can directly signup for the live account by visiting this [link](https://www.payfort.com/get-started/)

**Sandbox**

```json
POST   https://sbpaymentservices.payfort.com/FortAPI/reportingApi
```

**Live**

```json
POST   https://paymentservices.payfort.com/FortAPI/reportingApi
```

------

## Parameters Submission Type

While submitting your request to PayFORT server using the Endpoints&nbsp; [<i class="fa fa-anchor"></i>](#endpoints) you need to pass parameters in your request. The parameters that you will pass to the server in your request should be ***<mark>REST POST request using JSON Format</mark>***. Both the requests <mark>Generate Report&nbsp;<a href="#generate-report-request"><i class="fa fa-anchor"></i></a></mark> and <mark>Download Report&nbsp;<a href="#download-report-request"><i class="fa fa-anchor"></i></a></mark> will use set of parameters including the column parameters, filter parameters and the key parameters.

------

## Generate Report Request

Since you will be submitting REST POST using JSON Format, you can refer to the given JSON sample for creating a <mark>***Generate Report***</mark> request. The JSON sample also shows the parameters that are required to be sent along the request.

*Sample JSON Request*



The above JSON sample is for information purpose and you need to check out the columns parameters, filter parameters and the key parameters (passed within the filters parameters as key value in the above JSON sample) to select the parameters you need to pass in your request.





**Generate Report Request Sample**

------

Below is the sample request for the generation of report in the JSON format to be sent to the PayFORT server. The command <mark><strong>GENERATE_REPORT</strong></mark> notifies PayFORT server to generate a customized report based on the customized parameters that are sent via request in the JSON format. You have to check the different [input parameters](reportingapiparameters.md) and select the parameters based on your requirements. You can opt for receiving the response either in JSON format or the xml format depending on the merchant site's design and architecture.



Placeholder: Sample code in Java/PHP/Python/Ruby for report generation request.



Sample JSON request

```json
{
“query_command”: “GENERATE_REPORT”,
“access_code”: “zx0IPmPy5jp1vAz8Kpg7”,
“merchant_identifier”: “CycHZxVj”,
“merchant_reference”: “XYZ9239-yu898”,
“from_date”: “2017-08-03T00:00:01+03:00”,
“to_date”: “2017-08-03T23:59:59+03:00”,
“response_format”: “JSON”,
“language”: “en”,
“columns”: [
  “order_description”,
  “customer_ip”,
  “eci”,
  “geolocation_ip”,
  “merchant_reference”,
  “card_holder_name”,
  “currency”,
  “amount”,
  “payment_option”,
  “fort_id”,
  “customer_email”,
  “customer_name”,
  “operation”,
],
“filters”: [
  {
  “key”: “currency”,
  “value”: “USD”
  },
  {
  “key”: “payment_option”,
  “value”: “VISA”
  }
],
“signature”: “03a36d58acfc611f521528f2039a2228031d7ae4248d95181f2a24cfbe9f7865”
}


```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>You can customize your own report by providing different input parameters. Not all parameters might be of interest to you, hence select only those parameters which you think are important for your requirement. Providing unnecessary parameters/all parameters at a time to the server can increase the time to generate the report.</div>

**Submit download Report Request**

Once the report generation request has been submitted next request would be to submit request for the download of the generated report. 



Placeholder: Sample code in Java/PHP/Python/Ruby for download report request.

**Generate Report “JSON” Response Example**

------

The below is the sample response sent in JSON format by the PayFORT server to the generate report request submitted by you.

```json
{
“query_command”: “GENERATE_REPORT”,
“access_code”: “ zx0IPmPy5jp1vAz8Kpg7”,
“merchant_identifier”: “CycHZxVj”,
“merchant_reference”: “XYZ9239-yu898”,
“from_date”: “2017-08-03T00:00:01+03:00”,
“to_date”: “2017-08-03T23:59:59+03:00”,
“response_format”: “JSON”,
“signature”: “521d32010a9988de86e16b49f6303985508d5f244784474da1184d457b53ded2”,
“language”: “en”,
“response_message”: “Success”,
“response_code”: “56000”,
“status”: “56”
}
```

------



**Generate Report “XML” Response Example**

------

The below is the sample response sent in XML format by the PayFORT server to the generate report request submitted by you.

```xml
<response>
    <response_code>56000</response_code>
    <from_date>2017-08-03T00:00:01+03:00</from_date><signature>521d32010a9988de86e16b49f6303985508d5f244784474da1184d457b53ded2</signature>		<merchant_identifier>CycHZxVj</merchant_identifier>										<access_code>zx0IPmPy5jp1vAz8Kpg7</access_code>
    <language>en</language><response_format>XML</response_format>							<response_message>Success</response_message>
    <to_date>2017-08-03T23:59:59+03:00</to_date>
    <merchant_reference>XYZ9239-yu898</merchant_reference>									<query_command>GENERATE_REPORT</query_command>
    <status>56</status>
</response>
```

------



## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).



