# Void Authorization

------

After a card payment has been authorized, the payment is not complete until it has been [captured](capturepayment.md). If you do not wish to capture the payment, you can void it using the void API as described.

## The Request

------

Use the details below to set up your request.

## Endpoints

### Live

```http
POST  https://paymentservices.payfort.com/FortAPI/paymentApi
```

### Sandbox

```http
POST https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>You can send “merchant_reference” and/or “fort_id” in the VOID_AUTHORIZATION request.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response even the optional ones.</div>

### The Request Example

------

Check out the request parameters by visiting this [link](maintenanceparameters.md)

<div class="container">
  <h2>Sample Request</h2>
  <p>Here are the sample request you are required to send authorizing a purchase.</p>


  <ul class="nav nav-tabs">
    <li class="active"><a data-toggle="tab" href="#php">Php</a></li>
    <li><a data-toggle="tab" href="#python">Python</a></li>
    <li><a data-toggle="tab" href="#ruby">Ruby</a></li>
    <li><a data-toggle="tab" href="#java">Java</a></li>
    <li><a data-toggle="tab" href="#curl">cURL</a></li>
  </ul>

  <div class="tab-content">
    <div id="php" class="tab-pane fade in active">
```
error_reporting(E_ALL);
ini_set('display_errors', '1');

$url = 'https://sbpaymentservices.payfort.com/FortAPI/paymentApi';

$arrData = array(
'command' => 'VOID_AUTHORIZATION',
'access_code' => 'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier' => 'CycHZxVj',
'merchant_reference' => 'XYZ9239-yu898',
'language' => 'en',
'signature' => '7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'order_description' => 'iPhone 6-S',
);


$ch = curl_init( $url );
# Setup request to send json via POST.
$data = json_encode($arrData);
curl_setopt( $ch, CURLOPT_POSTFIELDS, $data );
curl_setopt( $ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));
# Return response instead of printing.
curl_setopt( $ch, CURLOPT_RETURNTRANSFER, true );
# Send request.
$result = curl_exec($ch);
curl_close($ch);
# Print response.
echo "<pre>$result</pre>";

```
    </div>
    <div id="python" class="tab-pane fade">
```
import urllib
import urllib2
import json

url = 'https://sbpaymentservices.payfort.com/FortAPI/paymentApi';
arrData = {
'command':'VOID_AUTHORIZATION',
'access_code':'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier':'CycHZxVj',
'merchant_reference':'XYZ9239-yu898',
'language':'en',
'signature':'7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'order_description':'iPhone 6-S',
};

values = json.dumps(arrData)
data = urllib.urlencode(values)
req = urllib2.Request(url, data)
response = urllib2.urlopen(req)
page = response.read()
print page + '\n\n'
```
    </div><div id="ruby" class="tab-pane fade">
```
require 'json'
require 'net/http'
require 'net/https'
require 'uri'
require 'openssl'

arrData = {
'command' => 'VOID_AUTHORIZATION',
'access_code' => 'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier' => 'CycHZxVj',
'merchant_reference' => 'XYZ9239-yu898',
'language' => 'en',
'signature' => '7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'order_description' => 'iPhone 6-S',
};

arrData = arrData.to_json
uri = URI.parse("https://sbpaymentservices.payfort.com/FortAPI/paymentApi")
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE
request = Net::HTTP::Post.new("/v1.1/auth")
request.add_field('Content-Type', 'application/json')
request.body = arrData
response = http.request(request)
```
    </div><div id="java" class="tab-pane fade">
```
String jsonRequestString = "{\"command\" : \"VOID_AUTHORIZATION\" , "
      + "\"access_code\" : \"zx0IPmPy5jp1vAz8Kpg7\", \"merchant_identifier\" : \"CycHZxVj\", \"merchant_reference\" : \"XYZ9239-yu898\","
      + "\"language\" : \"en\", \"signature\" : \"7cad05f0212ed933c9a5d5dffa31661acf2c827a\", "
      + "\"order_description\" : \"iPhone 6-S\"}";

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
    
    </div><div id="curl" class="tab-pane fade">
```
curl -H "Content-Type: application/json" -d 

'{"command":"VOID_AUTHORIZATION",

"access_code":"zx0IPmPy5jp1vAz8Kpg7",

"merchant_identifier":"CycHZxVj",

merchant_reference":"XYZ9239-yu898",

"language":"en",

"signature":"7cad05f0212ed933c9a5d5dffa31661acf2c827a",

"order_description":"iPhone6-S"}'

 https://sbpaymentservices.payfort.com/FortAPI/paymentApi

```
    </div></div></div>

## The Response

------

If you receive response code `20064` with status code `04` it means that your request to void authorization has been accepted by PayFort server.

### Response Example

------



​```json
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

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

