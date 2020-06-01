# In Common Services

------



## Query Operations

A type of query that can be requested through our system, which includes the “Check Status” query.

### Check Status

**Check Status** allows the Merchant to check the status of a specific order and the status of the latest operation performed on that order.

### Endpoints

------

**Sandbox**

```http
POST https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

**Live**

```http
POST https://paymentservices.payfort.com/FortAPI/paymentApi
```



### Parameters Submission Type

REST POST request using JSON.

### Check Status - Request

(Please take a look at the *Check Status Request Example* on the right side of the page.)

> Check Status Request Example

```
String jsonRequestString = "{\"query_command\" : \"CHECK_STATUS\" \"access_code\" : \"zx0IPmPy5jp1vAz8Kpg7\", \"merchant_identifier\" : \"CycHZxVj\","
        + "\"merchant_reference\" : \"XYZ9239-yu898\", \"language\" : \"en\", "
        + "\"signature\" : \"7cad05f0212ed933c9a5d5dffa31661acf2c827a\"}";

// Define and Initialize HttpClient
HttpClient httpClient = HttpClientBuilder.create().build();
// Intialize HttpPOST with FORT Payment services URL
HttpPost request = new HttpPost("https://sbpaymentservices.payfort.com/FortAPI/paymentApi");
// Setup Http POST entity with JSON String
StringEntity params = new StringEntity(jsonRequestString);
// Setup request type as JSON
request.addHeader("content-type", "application/json");
request.setEntity(params);
// Post request to FORT
HttpResponse response = httpClient.execute(request);
// Read response using StringBuilder
StringBuilder sb = new StringBuilder();
BufferedReader reader = new BufferedReader(new InputStreamReader(
    response.getEntity().getContent()), 65728);
String line = null;
while ((line = reader.readLine()) != null) {
  sb.append(line);
}
// Print response
System.out.println(sb.toString());
```

**Include the following parameters in the Request you will send to PayFort:**

|                                                  ATTRIBUTES | Description                                                  |
| ----------------------------------------------------------: | :----------------------------------------------------------- |
|                   **query_command** Alpha Mandatory max: 50 | The query operations command. Possible/ expected values: CHECK_STATUS Special characters: _ |
|              **access_code** Alphanumeric Mandatory Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
|      **merchant_identifier** Alphanumeric Mandatory Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|       **merchant_reference** Alphanumeric Mandatory Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898 Special characters: - _ . |
|                         **language** Alpha Mandatory Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|               **signature** Alphanumeric Mandatory max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                        **fort_id** Numeric Optional Max: 20 | The order’s unique reference returned by our system. Example: 149295435400084008 |
| **return_third_party_response_codes** Alpha Optional Max: 3 | This parameter allows you to return the 3rd party response codes in the transaction’s response. Possible/ expected values: - YES - NO |

 You can send “merchant_reference” and/ or “fort_id” in the CHECK_STATUS request.

### Check Status - Response

(Please take a look at the *Check Status Example Response* on the right side of the page.)

> Check Status Response Example

```
{"query_command":"CHECK_STATUS","access_code":"s31bpM1ebfNnwqo","merchant_identifier":"FD1Ptq","merchant_reference":"141127176","language":"en","signature":"90f7092923c9eea8b0df6d509453a1791a36e2cd4a80eaef366e235b169a40e0","fort_id":"21722423333","response_message":"Success","response_code":"12000","status":"12","transaction_status":"12","transaction_code":"12000","transaction_message":"Success"}
```

**The following parameters will be returned in PayFort’s Response:**

|                                        ATTRIBUTES | Description                                                  |
| ------------------------------------------------: | :----------------------------------------------------------- |
|                   **query_command** Alpha max: 50 | The query operations command. Possible/ expected values: CHECK_STATUS |
|              **access_code** Alphanumeric Max: 20 | Access code. Example: zx0IPmPy5jp1vAz8Kpg7                   |
|      **merchant_identifier** Alphanumeric Max: 20 | The ID of the Merchant. Example: CycHZxVj                    |
|       **merchant_reference** Alphanumeric Max: 40 | The Merchant’s unique order number. Example: XYZ9239-yu898   |
|                         **language** Alpha Max: 2 | The checkout page and messages language. Possible/ expected values: en/ ar |
|               **signature** Alphanumeric Max: 200 | A string hashed using the Secure Hash Algorithm. Please refer to section [Signature](https://docs.payfort.com/docs/api/build/index.html?java#signature) Example: 7cad05f0212ed933c9a5d5dffa31661acf2c827a |
|                       **fort_id** Numeric Max: 20 | The order’s unique reference returned by our system. Example: 149295435400084008 |
|        **response_message** Alphanumeric Max: 150 | Message description of the response code; it returns according to the request language. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages) |
|                  **response_code** Numeric Max: 5 | Response Code carries the value of our system’s response. *The code consists of five digits, the first 2 digits represent the response [status](https://docs.payfort.com/docs/api/build/index.html?java#statuses), and the last 3 digits represent the response [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages). Example: 20064 |
|                         **status** Numeric Max: 2 | A two-digit numeric value that indicates the status of the transaction. Possible/ expected values: Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses) |
|             **transaction_status** Numeric Max: 2 | The status of the last operation performed on a specific order. Possible/ expected values: Please refer to section [statuses](https://docs.payfort.com/docs/api/build/index.html?java#statuses) |
|               **transaction_code** Numeric Max: 5 | The message code returned for the last operation performed on a specific order. Possible/ expected values: Please refer to section [messages](https://docs.payfort.com/docs/api/build/index.html?java#messages) |
|     **transaction_message** Alphanumeric Max: 150 | The message returned for the last operation performed on a specific order. Example: Success |
|               **refunded_amount** Numeric Max: 10 | The total refunded amount for the order. Example: 10000      |
|               **captured_amount** Numeric Max: 10 | The total captured amount for the order. Example: 10000      |
|             **authorized_amount** Numeric Max: 10 | The total authorized amount for the order. Example: 10000    |
|      **authorization_code** Alphanumeric Max: 100 | Authorization Code returned from the 3rd party. Example: 017201 |
| **processor_response_code** Alphanumeric Max: 100 | Response code returns from the Processor. Example: APPROVED  |
|   **acquirer_response_code** Alphanumeric Max: 10 | Response code returns from the Acquirer. Example: 00         |

 Remember - Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones-.

## Services Activation

Services are activated for our Merchants by our back-office team. Once you open your Merchant account and click “Payment Stack” under the Services tab. The services provided by PayFort are:

- Fraud Prevention.
- 3-D Secure.
- Installments.
- Tokenization.
- Batch service.

 Remember - If you wish to activate extra services for your Merchant account, you need to contact PayFort’s Back-office team. For detailed information, please download our [Merchant Integration Guide](https://docs.payfort.com/pdf/PAYFORT_Merchant_Integration_Guide_V_10.0.pdf) and read the “Services Activation” section to guide you through this process.

## Signature

The **Signature** is a parameter that holds the digital signature value calculated by the SHA algorithm. The digital signature is used to authenticate the sender and receiver of the message and allows the receiver to verify the integrity of the message.

### Message Digest

|                Name | Description                                                  |
| ------------------: | :----------------------------------------------------------- |
|            SHA Type | The Secure Hash Algorithm is a family of cryptographic hash functions published by the National Institute of Standards as a US Federal information processing standard (FIPS) including: SHA-0, SHA-2, and SHA-3. Values: SHA-256, SHA 512, and SHA-128 (not recommended). |
|  SHA Request Phrase | This value is used when the Merchant generates the request signature. Values: Dynamic value defined by the Merchant. |
| SHA Response Phrase | This value is used by our system to generate the response signature for the Merchant’s Request. Values: Dynamic value defined by the Merchant. |

### Signature Pattern

The below steps describe the signature pattern:

1. Sort all PayFort requests parameters (both mandatory and optional) in an ascending alphabetical order based on the parameters names.
2. Concatenate the parameter name with the value separated by ’=’ (param_name=param_value).
3. Concatenate all the parameters directly without any separator. (param_name1=param_value1param_name2=param_value2).
4. Add the Merchant’s Passphrase at the beginning and end of the parameters string. (REQUESTPHRASEparam_name1=param_value1param_name2=param_value2RE QUESTPHRASE).
5. Use the SHA function to generate the SHA value of the resulted string depending on the type of SHA selected by the Merchant.

### Create Signature Value

```
Map<String, Object>requestMap = new HashedMap();
    requestMap.put("command", "PURCHASE");
    requestMap.put("merchant_reference", "Test010");
    requestMap.put("amount", "1000");
    requestMap.put("access_code", "SILgpo7pWbmzuURp2qri");
    requestMap.put("merchant_identifier", "MxvOupuG");
    requestMap.put("currency", "USD");
    requestMap.put("language", "en");
    requestMap.put("customer_email", "test@gmail.com");

//order by key
requestMap = requestMap.entrySet().stream().sorted(Map.Entry.comparingByKey())
          .collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue,
          (oldValue, newValue) -> oldValue, LinkedHashMap::new));

String requestString = "PASS";
for(Entry<String, Object> entry: requestMap.entrySet())
    requestString += entry.getKey() + "=" + entry.getValue();  
requestString+= "PASS";

MessageDigest digest = MessageDigest.getInstance("SHA-256");
byte[] hashed = digest.digest(requestString.getBytes(StandardCharsets.UTF_8));
String signature = javax.xml.bind.DatatypeConverter.printHexBinary(hashed);
```

In this section, you can find examples on how to create the signature value for request and response messages. Please note that all values mentioned in the examples are fictitious.

**The following is an example of the Request Parameters:**

- signature = b88db48baaa600c3fadac502c75a832e3470029f
- command = PURCHASE
- merchant_reference = Test010
- amount = 1000
- access_code = SILgpo7pWbmzuURp2qri
- merchant_identifier = MxvOupuG
- currency = USD
- language = en
- customer_email = test@gmail.com

**Below are the Merchant signature settings from the back-office:**

- **SHA Request Phrase:** PASS.
- **SHA-Type:** SHA-256.

After sorting the parameters and completing **step 4** of the [Signature Pattern](https://docs.payfort.com/docs/api/build/index.html?java#signature-pattern), the result will be the following concatenated string:



PASSaccess_code=SILgpo7pWbmzuURp2qriamount=1000command=PURCHASEcurrenc
y=USDcustomer_email=test@gmail.comlanguage=enmerchant_identifier=MxvOupuGmerch
ant_reference=Test010PASS



After applying **step 5** of the [Signature Pattern](https://docs.payfort.com/docs/api/build/index.html?java#signature-pattern), the result will be as follows:



Signature = 94C38AFC7BDAE0114FC8C740EDF12416F22998241CE4B4EA70D5521233A2C882



**The following is an example for the Merchant Page 2.0 request signature calculations:**

 Remember - The calculations for the Merchant Page 2.0 require you to calculate the signature without including the following parameters in the signature even if these parameters included in the request of Merchant Page 2.0: card_security_code, card_number, expiry_date, card_holder_name, remember_me.

**Assume you have the below parameters included in the request of Merchant Page 2.0:**

- service_command = TOKENIZATION
- language = en
- merchant_identifier = MxvOupuG
- access_code = SILgpo7pWbmzuURp2qri
- merchant_reference = MyReference0001
- card_security_code = 123
- card_number = 4005550000000001
- expiry_date = 2105
- remember_me = YES
- card_holder_name = John Smith

**Below are the Merchant signature settings from the back-office:**

- **SHA Request Phrase:** PASS.
- **SHA-Type:** SHA-256.

The string to hash should be prepared for the above request is the following **step 4** of the [Signature Pattern](https://docs.payfort.com/docs/api/build/index.html?java#signature-pattern):

PASSaccess_code=SILgpo7pWbmzuURp2qrilanguage=enmerchant_identifier=MxvOupuG
merchant_reference=MyReference0001service_command=TOKENIZATIONPASS

After applying **step 5** of the [Signature Pattern](https://docs.payfort.com/docs/api/build/index.html?java#signature-pattern), the result will be as follows:

signature = 7EE560CCD621DA61BFC772F2F1B5849BABDA768F5EE36D4DE67EFA88403E4B99

**The following is an example for the Reporting API request signature calculations: **

**Assume you have the below parameters included in the request of Reporting API: **

• query_command = GENERATE_REPORT • access_code = zx0IPmPy5jp1vAz8Kpg7 • merchant_identifier = CycHZxVj • merchant_reference = XYZ9239-yu898 • columns = [order_description, customer_ip, eci, geolocation_ip, merchant_reference, card_holder_name, currency, amount, payment_option, fort_id, customer_email, customer_name, operation] • filters = [{key=currency, value=USD}, {key=payment_option, value= VISA}] • from_date = 2017-08-03T00:00:01+03:00 • to_date = 2017-08-03T23:59:59+03:00 • response_format = JSON • language = en

**Below are the Merchant signature settings from the back-office:**

- **SHA Request Phrase:** PASS.
- **SHA-Type:** SHA-256.

The string to hash should be prepared for the above request is the following **step 4** of the [Signature Pattern](https://docs.payfort.com/docs/api/build/index.html?java#signature-pattern):

**Remember:**
\* In the columns parameter; you should:
  \1. Open brackets.
  \2. Put a “comma” then a “space” between the columns value.
Example: columns=[ order_description, customer_ip, eci, geolocation_ip, merchant_reference]
\* In the filters parameter; you should:
  \1. Open brackets.
  \2. Then open a curly brackets {}.
  \3. Write the “key”.
  \4. Put a “comma” then a “space.
  \5. Write the “value” of the key.
Example: filters=[{key=currency, value=USD}, {key=payment_option, value= VISA}]

PASSaccess_code=zx0IPmPy5jp1vAz8Kpg7columns=[order_description, customer_ip, eci, geolocation_ip, merchant_reference, card_holder_name, currency, amount, payment_option, fort_id, customer_email, customer_name]filters=[{key=currency, value=USD}, {key=payment_option, value=VISA}]from_date=2017-08-03T00:00:01+03:00language=enmerchant_identifier=CycHZxVjmerchant_reference=XYZ9239-yu898query_command=GENERATE_REPORTresponse_format=JSONto_date=2017-08-03T23:59:59+03:00PASS

After applying **step 5** of the [Signature Pattern](https://docs.payfort.com/docs/api/build/index.html?java#signature-pattern), the result will be as follows:

Signature = 6750d396772be7df79347306324b1ad20320b31522583346e79b2ae8a5bc8970

**PayFort Gateway** includes the signature in the Response so you can check the integrity of the received data. You do this by calculating the secure hash using the above method, then comparing your calculation with the value you received from PayFort Gateway. If the values match, then you can be assured that we received the data you sent, and you received the data we sent.

### Try It Yourself

```
Map<String, Object>requestMap = new HashedMap();
    requestMap.put("command", "PURCHASE");
    requestMap.put("merchant_reference", "Test010");
    requestMap.put("amount", "1000");
    requestMap.put("access_code", "SILgpo7pWbmzuURp2qri");
    requestMap.put("merchant_identifier", "MxvOupuG");
    requestMap.put("currency", "USD");
    requestMap.put("language", "en");
    requestMap.put("customer_email", "test@gmail.com");

//order by key
requestMap = requestMap.entrySet().stream().sorted(Map.Entry.comparingByKey())
          .collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue,
          (oldValue, newValue) -> oldValue, LinkedHashMap::new));

String requestString = "PASS";
for(Entry<String, Object> entry: requestMap.entrySet())
    requestString += entry.getKey() + "=" + entry.getValue();  
requestString+= "PASS";

MessageDigest digest = MessageDigest.getInstance("SHA-256");
byte[] hashed = digest.digest(requestString.getBytes(StandardCharsets.UTF_8));
String signature = javax.xml.bind.DatatypeConverter.printHexBinary(hashed);
```

In this section, you can create the concatenated string to calculate signature value for request and response messages. Please note that you need to replace “PASS” phrase with yours.

**Choose input type:**

JSONKey/Value



Was this helpful? Yes No

## FORT XML Response Builder

Through this section you can discover one of the FORT services that enables you to receive the FORT response in XML format.

### Structure



<response><FORT_PARAMETER_NAME_1>VALUE</FORT_PARAMETER_NAME_1><FORT_PARAMETER_NAME_2_list><FORT_PARAMETER_NAME_2><FORT_PARAMETER_NAME_3>VALUE</FORT_PARAMETER_NAME_3><FORT_PARAMETER_NAME_4>VALUE</FORT_PARAMETER_NAME_4><FORT_PARAMETER_NAME_5>VALUE</FORT_PARAMETER_NAME_5></FORT_PARAMETER_NAME_2><FORT_PARAMETER_NAME_2><FORT_PARAMETER_NAME_3>VALUE</FORT_PARAMETER_NAME_3><FORT_PARAMETER_NAME_4>VALUE</FORT_PARAMETER_NAME_4><FORT_PARAMETER_NAME_5>VALUE</FORT_PARAMETER_NAME_5></FORT_PARAMETER_NAME_2></FORT_PARAMETER_NAME_2_list></FORT_PARAMETER_NAME_1>VALUE</FORT_PARAMETER_NAME_1></response>



The XML response builder results specifications are:
**1.** The root node name is ‘response’.
**2.** The FORT_PARAMETER of type “List” has a special tag name format; where the parent node tag name format is:
<FORT_PARAMETER + “_list”>
**3.** The list child nodes tag name’s is the name of the parameter name itself.

### Sample Code

```xml
<response><response_code>54000</response_code><from_date>2017-01-19T12:20:00+02:00</from_date><data_list>   <data>   <card_number>455701******8902</card_number>   <expiry_date>2105</expiry_date>   <token_name>466E93413AB648DEE053320A10AC5986</token_name>   <card_brand>VISA</card_brand>   <card_bin>455701</card_bin>   <token_status>ACTIVE</token_status>   <creation_date>2017-01-20T08:25:37+13:00</creation_date>   </data>   <data>   <card_number>400555******0001</card_number>   <expiry_date>1705</expiry_date>   <token_name>tkn001</token_name>   <card_brand>VISA</card_brand>   <card_bin>455701</card_bin>   <token_status>ACTIVE</token_status>   <creation_date>2016-05-13T14:34:09+13:00</creation_date>   </data></data_list><signature>4b6b1f0219169b0dc77f7ceac83b930cf71995ab7a4fcc435a</signature><merchant_identifier>uZOJfKqb</merchant_identifier><access_code>AwvucffCjzibl0eZYTB3</access_code><language>en</language><response_format>XML</response_format><response_message>Success</response_message><to_date>2017-01-19T12:30:00+02:00</to_date><query_command>GET_TOKENS</query_command><data_count>1</data_count><status>54</status></response>
```

