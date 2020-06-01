# What is it?

------

You can safeguard your customer's payments from digital frauds by using basic [fraud management service](fraudbasic.md) and ACI Red Fraud Screening. ACI ReD service adds additional layer of fraud prevention and can be used in combination of the basic fraud management service.



**ACI ReD** is a reliable Fraud Screening and Prevention service that will further help safeguard your online payments and minimize chargebacks. It is designed to meet the needs of e-commerce Merchants as well as PSPs. ReD focuses on protecting the Merchant’s revenues and support the growth of their business, not to mention enhancing their Customer experience and boosting Customer satisfaction.

------

## Integration Flow

------

Placeholder: Provide description and Integration flow, process flow diagram.

------



### ACI ReD Fraud - Request

You can take help of PayFORT API to create ACI ReD Fraud management and prevention. Just create a Request and provide input parameters. Send the request to the PayFORT system which will return a response. You can check out the details about the input parameters by visiting the [link](aciredfraudparameters.md)

Placeholder: Please provide sample code for ACI ReD Fraud - Request





<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>The <mark><strong>fraud_extra</strong></mark> fields are custom fields as their values depend on the sector.</div>

 





------

### ACI ReD Cart Fraud - Request

Placeholder: Provide sample ACI ReD Cart Fraud- Request code.



You can check out the details about the input parameters by visiting the [link](aciredfraudparameters.md)

------

### ACI ReD Fraud - Response

Placeholder: Provide sample response sent by PayFORT server.

You can check out the details about the response parameters by visiting the [link](aciredfraudparameters.md)

------

### Cart Details Example Value

You can also fetch Cart details and the value of the cart

Placeholder: Provide sample code for fetching cart details and cart value.

The following is an example value of the <mark><strong>cart_details</strong></mark>:



```json
{cart_items:
 [{item_quantity:1,
   item_description:‘item desc’,
   item_price:50},
  {item_quantity:2,
   item_description:'item desc’, 
   item_price:50}]}
```

------

### Device fingerprint script

Through this service you can also generate device fingerprint from which transaction is being taken place. This helps to detect any fraud.

The following is the script you should use to generate the device fingerprint:

```html

 <input type=“hidden” id="device_fingerprint” name=“device_fingerprint”/>
```

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>The value of the device fingerprint hidden field will be calculated from the above script, you should take this value and send it to PayFort.</div>

 Please don’t edit on the values in the script below.

```javascript
<script type=“text/javascript”>var io_bbout_element_id = 'device_fingerprint’;//the input id will be used to collect the device fingerprint valuevar io_install_stm = false;var io_exclude_stm = 0;//prevent the iovation Active X control from running on either Windowsvar io_install_flash = false;var io_enable_rip = true;// collect real ip information</script><script type=“text/javascript” src=“https://mpsnare.iesnare.com/snare.js”></script>
```

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

