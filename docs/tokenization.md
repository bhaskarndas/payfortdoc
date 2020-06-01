## FORT Tokenization Service

For every transaction request sent to PayFORT payment system, it will send back a Token for various transactions such as authorization, purchase, installements, etc. This section provides details about PayFORT Tokenization Service.

The **Tokenization** service allows you to store the Customer’s credit card details in a safe and secure environment substituting the Customer’s sensitive card details with a non-sensitive equivalent referred to as a Token. The Token can be used to process transactions without the use of the card details.

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i><ul>
     <li>This service can be used in both <mark><strong>Authorization</strong></mark>,<mark><strong>Purchase</strong></mark> operations.
 </li><li>PayFort’s Operations team must activate the Tokenization service.</li><li>The Customer should agree to save his/ her card details.</li><li>The Token will be stored only if the card is valid and if the transaction was processed successfully.</li>
     </ul></div>
------

## Integration Flow

------

Placeholder: Please provide Integration flow along with a diagram.

------

### Create Token in Transaction Flow

This process will create a new Token for every new Authorization/Purchase transaction. You can use the input parameters provided in this section to create a request for new Token and the same parameter will hold the Token name in PayFort’s Response:

|                                    ATTRIBUTES | Description                                                  |
| --------------------------------------------: | :----------------------------------------------------------- |
| **token_name** Alphanumeric Optional max: 100 | Holds the name of the Token to update the Token or rename it. Example: OpVmp Special characters: . @ - _ |

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

------

### Create New Token Service

This service will help you to verify and provide token's to customer's credit cards without incurring additional charge on your customer. You can use following endpoints to create a request to PayFORT for verifying and providing tokens to your customer's credit cards.

------

### Endpoints

**Sandbox**

```http
POST https://sbcheckout.PayFort.com/FortAPI/paymentPage
```

**Live**

```http
POST https://checkout.PayFort.com/FortAPI/paymentPage
```

------

## Parameters Submission Type

HTTPs Form Post Request.

------

## Create New Token Service - Request

Placeholder: Provide sample code for new token service request.

For input parameters that are required to be sent through request please visit the [link](tokenizationparameters.md)



## Create New Token Service - Response

**The following parameters will be returned in PayFort’s Response:**

Placeholder: Please provide sample JSON response sent by PayFORT system.

------

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i> Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

------

### Update Token Service

------

If in the future your customer updates his/her credit card then this service will update the tokens for the card.

This service enables you to update your card associated with a token and the status of a token via API calls.

## Endpoints

------

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

## Update Token Service – Request

------

Placeholder: Provide sample code for Update Token Service - Request.

To view more details on input parameters please visit the following [link](tokenizationparameters.md)



## Update Token Service – Response

------

**The following parameters will be returned in PayFort’s Response:**

Placeholder: Provide sample response sent by PayFORT system.

To view more details on response parameters please visit the following [link](tokenizationparameters.md)

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

 

------



## Currency Exchange Service

------

This service allows to convert customer's transaction amount from one currency into another currency using live currency exchange rate.



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before start implementing this service please make sure to contact support@payfort.com to activate it in your account</div>

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



------

### Parameters Submission Type

REST POST request using JSON.

------



### Currency Exchange - Request

------

You can use the above endpoints to create and request to PayFORT system to use the currency exchange service. Before that you are required to contact support@payfort.com to activate this service.



Placeholder: Please provide sample code for Currency exchange request .



Please visit the [link](tokenizationparameters.md) to view the details of various input parameters.



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Before sending the amount value of any transaction, you have to multiply the value with the currency decimal code according to ISO code 3.
For example: If the amount value was 500 AED; according to ISO code 3, you should multiply the value with 100 (2 decimal points); so it will be sent in the request as 50000.
Another example: If the amount value was 100 JOD; according to ISO code 3, you should multiply the value with 1000 (3 decimal points); so it will be sent in the request as 100000.</div>
------



### Currency Exchange - Response

Placeholder: Please provide sample JSON response sent by PayFORT system.

Please visit the [link](tokenizationparameters.md) to view the details of various response parameters.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>

---------------------



## Installment Service tokenization

------

This is a separate tokenization service when Installment service is activated on your merchant site. For more details on the Installment service please visit this [link](installments.md)

------



### Merchant Page 2.0 Tokenization

------



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>First, you need to send a [Get Instalments Plans API] request; to get the instalments details.</div>




### Endpoints

**Sandbox**

```http
POST https://sbcheckout.payfort.com/FortAPI/paymentPage
```

**Live**

```http
POST https://checkout.payfort.com/FortAPI/paymentPage
```

------



## Parameters Submission Type

HTTPs Form Post Request

------



## Merchant Page 2.0 Tokenization - Request

Placeholder: Sample code for Merchant Page 2.0 installments request.





Please visit the [link](tokenizationparameters.md) to view the details of various input parameters for Merchant Page 2.0 Tokenization - Request.

 <div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Please don’t include the following parameters in calculating the signature if you are using Merchant Page 2.0 tokenization request: <mark>card_security_code</mark>,<mark>card number</mark> ,<mark>expiry_date</mark> , <mark>card_holder_name</mark>,<mark>remember_me</mark> .</div>





------



## Merchant Page 2.0 Tokenization - Response

Placeholder: Provide sample json response.



Please visit the [link](tokenizationparameters.md) to view the details of various response parameters for Merchant Page 2.0 Tokenization - Response.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones</div>





------

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).