# Installments

------

Installments helps your customer to pay for any product or services at your site in easy equitable monthly installments (EMI). If your customers don't have enough cash for payment of products or services offered by your site, then PayFORT in partnership with several banks and credit cards facilitates installment services for your customer requirements. However, you will be paid the full amount immediately.



<div class="embed-responsive embed-responsive-16by9">
    <iframe width="734" height="413" src="https://www.youtube.com/embed/nU53vW3N94o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
PayFORT is offering the services at present in UAE Egypt KSA only.

------



### Supported Schemes

------



**List of Banks enrolled for installment services**

1. Emirates NBD 
2. ADCB Mashreq 
3. Dubai First CBD 
4. Mawarid Finance NCB 
5. SABB Bank AlJazira 
6. Saudi Hollandi bank Riyadh 
7. bank CIB Barclays

------

### How it works?

Placeholder: Provide Integration flow/process flow diagram.

Despite the involvement of multiple parties (merchant, bank and customer), the installment process is simple and can be implemented in seconds.

1. At Checkout customer selects his bank, installment plans and enters his credit card details to complete the purchase. 

2. Customer is not required to call his bank to convert the transaction into Installments. PayFORT will work with banks to convert the transaction into installments.

3. Customer then receives an sms or an email from the bank confirming the conversion of the transaction into EMI.

   <div class="embed-responsive embed-responsive-16by9">
       <iframe width="734" height="413" src="https://www.youtube.com/embed/-QKm45xojfs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>



## Installments Redirection

------

Now most of the transactions can be converted into Installments so in this section all the transactions of Redirections can be converted into Installments. 

### Installments Redirection Service - Request

You have to include the following parameters in the [Purchase - Request Parameters](redirectionsparameters.md) which you will send to PayFort:

|                              ATTRIBUTES | Description                                                  |
| --------------------------------------: | :----------------------------------------------------------- |
| **installments** Alpha Optional max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |



Placeholder: Please provide sample code for Installments Redirection service - requirements



------



### Installments Redirection Service - Response

Placeholder : Provide sample JSON response

The following parameters will be returned in PayFort’s JSON Response in addition to the [Purchase - Response Parameters](redirectionsparameters.md):

|                                ATTRIBUTES | Description                                                  |
| ----------------------------------------: | :----------------------------------------------------------- |
|            **installments** Alpha max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |
| **number_of_installments** Numeric max: 2 | The number of installments the customer has selected in the payment page. Example: 3 |

------



## Installments Merchant Page (Iframe)

------

If you are integrating Merchant Page (iFrame feature) then you can easily redesign your merchant page to easily send installment request from the merchant page itself as shown in this section.

### Installments Merchant page Service - Request

------

Placeholder: Provide sample code for request



Include the following parameters in the [Merchant page - Request Parameters](merchantpageparameters.md) you will send to PayFort:

|                                      ATTRIBUTES | Description                                                  |
| ----------------------------------------------: | :----------------------------------------------------------- |
|        **installments** Alpha Mandatory max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |
|            **amount** Numeric Mandatory Max: 10 | The transaction’s amount. *Each currency has predefined allowed decimal points that should be taken into consideration when sending the amount. Example: 10000 |
|             **currency** Alpha Mandatory Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
| **customer_country_code** Alpha Optional Max: 3 | The Customer’s country code. ISO 3 digit country code. Example: JOR |

 

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>
------

### Installments Merchant page Service - Response

Placeholder: Please provide sample JSON response.

The following parameters will be returned in PayFort’s Response in addition to the [Merchant Page - Response Parameters](merchantpageparameters.md)

|                                ATTRIBUTES | Description                                                  |
| ----------------------------------------: | :----------------------------------------------------------- |
|            **installments** Alpha max: 10 | Used to specify the type of the Installments service. Possible/ expected values: STANDALONE |
|                **amount** Numeric Max: 10 | The transaction’s amount. Example: 10000                     |
|                 **currency** Alpha Max: 3 | The currency of the transaction’s amount in ISO code 3. Example: USD |
|    **customer_country_code** Alpha Max: 3 | The Customer’s country code. ISO 3-digit country code. Example: JOR |
| **number_of_installments** Numeric Max: 2 | The number of installments the customer has selected in payment page. Example: 3 |
|         **plan_code** Alphanumeric Max: 8 | A code that refers to the **“installments plan”** the customer selected from the merchant page. Example: NNNN89JJ |
|       **issuer_code** Alphanumeric Max: 8 | A code that refers to the **“card issuer”** the customer selected from the merchant page. Example: 12HP34SE |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

------

### Installments Purchase Service - Request

Placeholder: Sample code for merchant page operations request

For transactions being carried out under operations you have to Include the following parameters in the [Operation - Request Parameters](https://docs.payfort.com/docs/api/build/index.html?shell#operations-request) while sending to PayFort:

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
|      **installments** Alpha Mandatory max: 10 | Used to specify the type of the Installments service. Possible/ expected values: YES |
|   **plan_code** Alphanumeric Mandatory Max: 8 | A code that refers to the **“installments plan”** the customer selected from the merchant page. Example: NNNN89JJ |
| **issuer_code** Alphanumeric Mandatory Max: 8 | A code that refers to the **“card issuer”** the customer selected from the merchant page. Example: 12HP34SE |

------



### Installments Purchase Service - Response

------

Placeholder: Provide sample JSON response sent from the PayFORT server.

The following parameters will be returned in PayFort’s Response in addition to the [Operation - Response Parameters](https://docs.payfort.com/docs/api/build/index.html?shell#operations-response):

|                                ATTRIBUTES | Description                                                  |
| ----------------------------------------: | :----------------------------------------------------------- |
|            **installments** Alpha max: 10 | Used to specify the type of the Installments service. Possible/ expected values: YES |
|         **plan_code** Alphanumeric Max: 8 | A code that refers to the **“installments plan”** the customer selected from the merchant page. Example: NNNN89JJ |
|       **issuer_code** Alphanumeric Max: 8 | A code that refers to the **“card issuer”** the customer selected from the merchant page. Example: 12HP34SE |
| **number_of_installments** Numeric Max: 2 | The number of installments the customer has selected in payment page. Example: 3 |

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>



## Installments Hosted Checkout

------

### Get Installments Plans API

By using Hosted Checkout you will be able to fetch various installment plan details for your various products and services as well as various issuers configured in your account for the installment service. You can use the following endpoints to setup hosted checkout service.



#### Endpoints

**Sandbox**

```http
POST https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

**Live**

```http
POST https://paymentservices.payfort.com/FortAPI/paymentApi
```

------



### Parameters Submission Type



REST POST request using JSON.

------

### Get Installments Plans API - Request

Placeholder: Provide the sample code for the request

Include the following parameters in the Request you will send to PayFort:

For input parameters please visit the section Get Installments Plans API - Request under the [link](installmentsparameters.md)

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Please note that you can’t send these parameters (amount/ currency) separately; you should send them together or not sending them at all.</div>

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>If you send the amount and the currency in get plans API, you will receive AmountPerMonth parameter calculated from our side, and no need to use the formulas returned to complete the amount calculations.</div>

------

### Get Installments Plans API - Response

Placeholder: Provide sample JSON response

The following parameters will be returned in PayFort’s Response:

For more details on the parameters please visit the section Get Installments Plans API - Response in the [link](installmentsparameters.md)

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>



------

### Issuer Detail

You can use the following attributes to know the details of the installment services issuers.

Placeholder: Provide sample code for issuer details

This parameter is a sub parameter of the <mark><strong>installment_detail</strong></mark> parameter, please refer the section Issuer Detail in the [link](installmentsparameters.md) for the children parameters of the <mark><strong>issuer_detail</strong></mark>

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>What does each of the formula parameters mean:
  (amount +(amount *effective rate/100))/period
  Amount: The transaction amount.
  Effective rate: The fee_amount retrieved in the response inside the next plan_detail section
  Period: number_of_installment retrieved in the response inside the next plan_detail section</div>
------



### Plan Details

If you want to fetch details of various installment plans you can use the attributes in this section and send in your request to the PayFORT server.

Placeholder: provide sample code for plan details.

This parameter is a sub parameter of the <mark><strong>issuer_detail</strong></mark> parameter, please refer the section Plan Detail in the [link](installmentsparameters.md) for the children parameters of the <mark><strong>plan_detail</strong></mark>:

------

### Bins Details

This section will help you to capture the details of the credit card that customer will use for availing the installment service. You have to use the attributes in your request to fetch the details of the credit card.

Placeholder: provide  sample code for bins details.

This parameter is a sub parameter of the <mark><strong>issuer_detail</strong></mark> parameter, please refer the section Bin Detail in the [link](installmentsparameters.md) for the children parameters of the <mark><strong>bins</strong></mark>:

------

### Get Installments Plans API formulas

This section helps you to calculate the installment formula that would be displayed to your customers when they checkout. Following are the key formulas applicable for calculating the installments.

- **Percentage Fees:** Installments interest rate in percent (%) charged to the customer by the bank.

- **Rate Flat:**
  \- Non Islamic:
    ((amount + ((amount * (fees / 100)) * months))) / months
    (amount + (amount* (fees / 100))) / months
  \- Islamic:
    (((months * (fees / 100)) + 1) * amount) / months

- **Rate Reducing:**
    PMT (excel function)



- **Fixed Fees:** Installments fees in fixed amount charged to the customer by the bank.

  (amount + fees) / months

------

### Get Installments Plans API - Response

Response Sample

The following is sample of a response of an Get Installments Plans API request:

```json
{
“response_code”: “62000”,
“response_message”: “Success”,
“signature”: “9b02960d319318256efbc17cf57dbc1f7e7fd046e20e49215d0bed32a065c3ae”,
“merchant_identifier”: “bxgOIxIz”,
“access_code”: “Ru8n1ciSJXWm8WFHLKsR”,
“query_command”: “GET_INSTALLMENTS_PLANS”,
“issuer_code”: “fHkigRtu”,
“installment_detail”: {
  “issuer_detail”: [
  {
     “issuer_code”: “fHkigRtu”,
    “issuer_name_ar”: “بنك الامارات دبي الوطني”,
    “issuer_name_en”: “Emirates NBD Egypt”,
    “terms_and_condition_ar”: “http://www.emiratesnbd.com.eg/egypt-en/index.cfm/retail-banking/cards/special-offers/”,
    “terms_and_condition_en”: “http://www.emiratesnbd.com.eg/egypt-en/index.cfm/retail-banking/cards/special-offers/”,
    “country_code”: “EGY”,
    “issuer_logo_ar”: “https://stgstatic.payfort.com/frontend/files/logos/issuer/logo_ar_7.jpeg”,
     “issuer_logo_en”: “https://stgstatic.payfort.com/frontend/files/logos/issuer/logo_en_7.jpg”,
    “banking_system”: “Non Islamic”,
    “formula”: “((amount + ((amount * (effective rate/100)) * period))) / period”,
  “plan_details”: [
  {
    “plan_code”: “zAS4XyG2”,
    “currency_code”: “USD”,
    “number_of_installment”: 33,
    “fees_type”: “Percentage”,
    “fees_amount”: 300,
     “processing_fees_type”: null,
    “processing_fees_amount”: null,
    “rate_type”: “Flat”,
    “plan_merchant_type”: “Non Partner”,
    “plan_type”: “Cross-Border”,
    “fee_display_value”: 400,
    “minimum_amount”: 300,
    “maximum_amount”: 33333300,
    “amountPerMonth”: “3.00”
    }
    ],
“bins”: [
{
  “bin”: “427838”,
  “country_code”: “EGY”,
  “currency_code”: “EGP”,
  “card_brand_code”: “VISA”
},
{
  “bin”: “522025”,
  “country_code”: “EGY”,
  “currency_code”: “EGP”,
  “card_brand_code”: “Master Card”
},
{
  “bin”: “543173”,
  “country_code”: “EGY”,
  “currency_code”: “EGP”,
  “card_brand_code”: “Master Card”
},
],
  “confirmation_message_ar”: null,
  “disclaimer_message_ar”: null,
  “processing_fees_message_ar”: null,
  “confirmation_message_en”: null,
  “disclaimer_message_en”: null,
  “processing_fees_message_en”: null
}
]
},
“status”: “62”
}
```

------





### Merchant Page 2.0 Operations

------



### Endpoints

**Sandbox**

```http
POST https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

**Live**

```http
POST https://paymentservices.payfort.com/FortAPI/paymentApi
```



------

## Parameters Submission Type

REST POST request using JSON.

------



## Installment Service For Merchant Page 2.0 Operations - Request

You can use the endpoints to integrate and send request for Merchant Page 2.0 operations.



Placeholder: Provide sample code for merchant page 2.0 operations for installment service.

Please visit the section Installment Service for Merchant Page 2.0 Operations - Request under the [link](installmentsparameters.md) for input parameters to be sent in the request.

 Remember - Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.

------



## Installment Service For Merchant Page 2.0 Operations - Response

------

Placeholder: Provide sample JSON response for merchant page 2.0 operations for installments.



For more details on response parameters please visit the section Installment Service for merchant page 2.0 operations- response in the [link](installmentsparameters.md)

 Remember - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.

------



## Installments Hosted for Trusted Channel

------

If you are a trusted channel partner or already a PCI compliant partner you can use the attributes provided in this section to integrate your installment service. For more details on the trusted channel partners please visit this [link](trusted.md)

------



### Installments Hosted for Trusted – Request

Placeholder: Please provide sample code for trusted channel partner request for installment.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>First, you need to send a [Get Instalments Plans API](https://docs.payfort.com/docs/api/build/index.html?shell#get-installments-plans-api) request; to get the instalments details.

Include the [input parameters](installmentsparameters.md) under the section Installments Hosted for Trusted - Request in addition to the [Trusted Channel – Request](trustedchannelparameters.md) Parameters you will send to PayFort:</div>



------



### Installments Hosted for Trusted – Response

------



Placeholder : Provide sample JSON response for Hosted for trusted channel 

For details on parameters of the response visit the section Installments Hosted for Trusted- Response in the [link](installmentsparameters.md)



------



## Installments Merchant Page - Style Sheet

------

This is a list with all customizable CSS classes for Installments Merchant Page. You can use these css classes to style and design your installments merchant page.

- The **`installments-container`** class - responsible for the total width of the form container and the background.
- The **`receipt-container`** class - responsible for the receipt section you can customize / hide it by changing the CSS values
- The **`full-width`** class - responsible for the plans and switching the view from dropdown to a table.
- The **`credit-card-container`** class - responsible for the credit card form`s shape look.
- The **`error`** class - responsible for the error messages.
- The **`half1, half2`** class - used to merge the date and CVV fields into one block or each one on block if needed.
- The **`bank`** class - is responsible for the bank agreement section.
- The **`floatl`** class - is the container of each single input field.
- The **`Pay`** class - responsible for the submit button.
- The **`Visa/ MasterCard`** classes - used to change the color of the Visa/ MasterCard colors.

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>- You can always create multiple theme files that will enable you to switch freely and easily between them when necessary.<br/>
- “Theme” files can be uploaded from the back-office using the Payment Page template screen.</div>





## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).