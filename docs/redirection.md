------

Once the customer's payment details are verified, the next payment process is the <mark>Redirection</mark> process. [Integration](index.md) process enables you to capture the payment details of the customer and then validating the same with the PayFORT server whereas the redirection process enables you to <mark> Authorize</mark>  a <mark>Purchase</mark>. 

## How it works?

------

The <mark>**Authorization**</mark> operation holds the amount from the Customer’s credit card for a period of time until you capture or void the transaction. If no capture or void transaction is processed during this period, the transaction will be voided automatically. In <mark>**Purchase**</mark> you will send one single request to the PayFORT server in order to authorize and capture the transaction amount.

We offer you to <mark>**Redirect**</mark> your customer from your website to PayFORT’s gateway page to fill out his credit card details during these operations.

**Looking to void a payment?**
You can [void](voidauthorization.md) an authorized payment at any time. However, captured payments can only be [refunded](refund.md).

## Endpoints

------

You can use the sandbox endpoint to test your payment processing page for redirection or you can use the production endpoint if you want to go live.

**SandBox**

```http
POST https://sbcheckout.payfort.com/FortAPI/paymentPage
```

**Live**

```http
POST https://checkout.payfort.com/FortAPI/paymentPage
```

------

## Parameters Submission Type

When you design your form(html page ) you have to provide the <mark>Endpoints</mark>&nbsp;&nbsp;[<i class="fa fa-anchor"></i>](#endpoints) in the form method. Providing these endpoints in your page will redirect your request to the PayFORT server. The page can be designed in the programming language of your choice. But you have to include the below mentioned code in your html based form. 

Form Post Request.

```html
<form method=“post” action=“https://sbcheckout.payfort.com/FortAPI/paymentPage” id=“form1” name=“form1”> </form>
```

The above code snippet is an HTML based form that will post a request to PayFORT serverand  you are also required to submit parameters in the form so that PayFORT server can understand your request and process the same. However, If you are not familiar with HTML tags and forms then you can checkout this [site](https://www.w3schools.com/).

<div class="alert alert-info">&nbsp;&nbsp;<i class="fa fa-info">&nbsp;&nbsp;</i>The parameters are mandatory and are required by PayFORT server to validate, authenticate and provide the tokens for processing of payment</div>

Visit the [link](redirectionsparameters.md) to check the different parameters to be sent in a redirection request.



<div class="container">
  <h2>Sample Request</h2>
  <p>You can design your form in any programming language.Here is the sample request (written different languages) which is sent for authorizing a purchase.</p>


  <ul class="nav nav-tabs">
    <li class="active"><a data-toggle="tab" href="#php">Php</a></li>
    <li><a data-toggle="tab" href="#python">Python</a></li>
    <li><a data-toggle="tab" href="#ruby">Ruby</a></li>
    <!--<li><a data-toggle="tab" href="#java">Java</a></li>
    <li><a data-toggle="tab" href="#curl">cURL</a></li>-->
  </ul>

  <div class="tab-content">
    <div id="php" class="tab-pane fade in active">

​    
<pre>
$requestParams = array(
'command' => 'AUTHORIZATION',
'access_code' => 'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier' => 'CycHZxVj',
'merchant_reference' => 'XYZ9239-yu898',
'amount' => '10000',
'currency' => 'AED',
'language' => 'en',
'customer_email' => 'test@payfort.com',
'signature' => '7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'order_description' => 'iPhone 6-S',
);

</pre>
        
    
    </div>
    <div id="python" class="tab-pane fade">
      <pre>
import cgi
requestParams = {
'command' => 'AUTHORIZATION',
'access_code' => 'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier' => 'CycHZxVj',
'merchant_reference' => 'XYZ9239-yu898',
'amount' => '10000',
'currency' => 'AED',
'language' => 'en',
'customer_email' => 'test@payfort.com',
'signature' => '7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'order_description' => 'iPhone 6-S',
};
</pre>
     
    </div>
    <div id="ruby" class="tab-pane fade">
     <pre>
require 'cgi'
requestParams = {
'command' => 'AUTHORIZATION',
'access_code' => 'zx0IPmPy5jp1vAz8Kpg7',
'merchant_identifier' => 'CycHZxVj',
'merchant_reference' => 'XYZ9239-yu898',
'amount' => '10000',
'currency' => 'AED',
'language' => 'en',
'customer_email' => 'test@payfort.com',
'signature' => '7cad05f0212ed933c9a5d5dffa31661acf2c827a',
'order_description' => 'iPhone 6-S',
};
requestParams.each {|key, value|
  puts key +value ;
}
     </pre>
    </div>


  </div>
</div>

<!-- Code for the redirection url-->

<div class="container">
  <h2>Sample code for redirection</h2>
  <p>Here are the sample code for redirecting the request to PayFORT.</p>


  <ul class="nav nav-tabs">
    <li class="active"><a data-toggle="tab" href="#php">Php</a></li>
    <li><a data-toggle="tab" href="#python">Python</a></li>
    <li><a data-toggle="tab" href="#ruby">Ruby</a></li>
    <!--<li><a data-toggle="tab" href="#java">Java</a></li>
    <li><a data-toggle="tab" href="#curl">cURL</a></li>-->
  </ul>

  <div class="tab-content">
    <div id="php" class="tab-pane fade in active">

​    

```
$redirectUrl = 'https://sbcheckout.payfort.com/FortAPI/paymentPage';
echo "<html xmlns='http://www.w3.org/1999/xhtml'>\n<head></head>\n<body>\n";
echo "<form action='$redirectUrl' method='post' name='frm'>\n";
foreach ($requestParams as $a => $b) {
    echo "\t<input type='hidden' name='".htmlentities($a)."' value='".htmlentities($b)."'>\n";
}
echo "\t<script type='text/javascript'>\n";
echo "\t\tdocument.frm.submit();\n";
echo "\t</script>\n";
echo "</form>\n</body>\n</html>";
```

    </div>
    <div id="python" class="tab-pane fade">
```
redirectUrl = 'https://sbcheckout.payfort.com/FortAPI/paymentPage';
print "<html xmlns='http://www.w3.org/1999/xhtml'>\n<head></head>\n<body>\n";
print "<form action='redirectUrl' method='post' name='frm'>\n";
for (slug, title) in requestParams.items():
    print "\t<input type='hidden' name='"+ cgi.escape(slug)+"' value='"+ cgi.escape(title)+"'>\n";

print "</form>";
print "\t<script type='text/javascript'>\n";
print "\t\tdocument.frm.submit();\n";
print "\t</script>\n";
print "\n</body>\n</html>";
```

    </div>
    <div id="ruby" class="tab-pane fade">
```
redirectUrl = 'https://sbcheckout.payfort.com/FortAPI/paymentPage';
puts "<html xmlns='http://www.w3.org/1999/xhtml'>\n<head></head>\n<body>\n";
puts "<form action='redirectUrl' method='post' name='frm'>\n";
requestParams.each {|key, value|
    puts "\t<input type='hidden' name='"+ CGI.escapeHTML(key)+"' value='"+ CGI.escapeHTML(value)+"'>\n";
}
puts "</form>\n";
puts "\t<script type='text/javascript'>\n";
puts "\t\tdocument.frm.submit();\n";
puts "\t</script>\n";
puts "</body>\n</html>";
```
    </div>


  </div>
</div>

------



## Go to Full API

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)



------



## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).