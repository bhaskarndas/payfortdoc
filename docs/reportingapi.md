# What is Data Mine (Reporting API)?

For retail merchants like you biggest dilemma they face is to download a customized reports. These customized reports includes sales reports, transaction reports, recurring payment reports, bulk sales reports etc. If you are planning to develop your own solution then you can easily use the PayFORT's easy to use reporting API to generate your own customized reports. The Reporting API provides you the feature to generate misc.. reports that can be customized as per your business requirements. You can specify the columns to be included and filters, then download the generated report. The report is limited to 200,000 transactions.

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

```json
{
"query_command": "GENERATE_REPORT",
"access_code": "zx0IPmPy5jp1vAz8Kpg7",
"merchant_identifier": "CycHZxVj",
"merchant_reference": "XYZ9239-yu898",
"from_date": "2017-08-03T00:00:01+03:00",
"to_date": "2017-08-03T23:59:59+03:00",
"response_format": "JSON",
"language": "en",
"columns": [
    "order_description",
    "customer_ip",
    "eci",
    "geolocation_ip",
    "merchant_reference",
    "card_holder_name",
    "currency",
    "amount",
    "payment_option",
    "fort_id",
    "customer_email",
    "customer_name",
    "operation",
],
"filters": [
    {
    "key": "currency",
    "value": "USD"
    },
    {
    "key": "payment_option",
    "value": "VISA"
    }
],
"signature": "03a36d58acfc611f521528f2039a2228031d7ae4248d95181f2a24cfbe9f7865"
}
```

The above JSON sample is for information purpose and you need to check out the columns parameters, filter parameters and the key parameters (passed within the filters parameters as key value in the above JSON sample) to select the parameters you need to pass in your request.

**Columns Parameter**

Below is the sample of various column parameters which you can chose to pass in your request as a list. The list is surrounded by [] (square brackets) which is JSON based list. The list which you pass in your request will generate the data under the respective columns (passed as a list in the generate and download reports).

*Sample Column Parameters in JSON's List Format*

```json
[
"fort_id",
"merchant_reference",
"authorization_code",
"customer_name",
"customer_ip",
"geolocation_ip",
"customer_email",
"acquirer_name",
"payment_option",
"channel",
"transaction_date",
"card_number",
"expiry_date",
"card_holder_name",
"amount",
"currency",
"card_bin",
"eci",
"operation",
"token_name",
"3ds_indicator",
"fraud_indicator",
"installments_indicator",
"status",
"response_code",
"response_message",
"third_party_message",
"third_party_code",
"order_date",
"order_description",
"acquirer_mid",
"acquirer_response_code",
"acquirer_response_message",
"processor_response_code",
"sadad_olp",
"sadad_transaction_id",
"payment_link_id",
"Invoice_id",
"digital_wallet"
]
```



Filter Parameters and Key Parameters

```
[]
```







```
["fort_id",
 "merchant_reference",
 "authorization_code",
 "customer_name",
 "customer_ip",
 "geolocation_ip",
 "customer_email",
 "acquirer_name",
 "payment_option",
 "channel",
 "transaction_date",
 "card_number",
 "expiry_date",
 "card_holder_name",
 "amount",
 "currency",
 "card_bin",
 "eci",
 "operation",
 "token_name",
 "3ds_indicator",
 "fraud_indicator",
 "installments_indicator",
 "status",
 "response_code",
 "response_message",
 "third_party_message",
 "third_party_code",
 "order_date",
 "order_description",
 "acquirer_mid",
 "acquirer_response_code",
 "acquirer_response_message",
 "processor_response_code",
 "sadad_olp",
 "sadad_transaction_id",
 "payment_link_id",
 "Invoice_id",
 "digital_wallet"
]
```

