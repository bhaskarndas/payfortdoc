# PayFORT Fraud Protection Service

------

These days it is very common to get lured into various scams and expose any application and device to the scamsters. The scamsters use various novel techniques such as phishing, etc to scam. PayFORT helps to protect against  online frauds. This service protects you being lured into a scam over the Internet, and as a result minimizes chargebacks.  

It's light fraud check rules can be enabled on the merchant account if the merchant business is not that risky or have complex fraud rules. Its limited number of fraud rules can be permitted to monitor the merchant transactions online during the transaction processing.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>This service can be used in both <a href="../docs/redirections.md">Authorization and Purchase </a>operations. The Fraud service must be activated by PayFort’s Operations team.
    \- Please note that PayFort’s operations team must activate the fraud service.</div>
PayFORT fraud management consists of two layers first one is the basic fraud management service and another is [ACI ReD Fraud Service](aciredfraud.md). This section covers fraud management service API and basic fraud management through the back office.



------

## How it Works?

------

The PayFORT service helps your application or site to detect customer's IP Geolocation and helps track the payment transactions.



Placeholder: Explain the working process for the PayFORT fraud protection service.



## Integration Flow

------

Workflow Diagram required here to explain the Integration flow as well.



## PayFORT Fraud prevention services Request

**The Request**

Placeholder: Provide a sample code for sending the request.



**Request Parameters**

|                                                  ATTRIBUTES | Description                                                  |
| ----------------------------------------------------------: | :----------------------------------------------------------- |
| **customer_ip**<sup>( Alphanumeric Mandatory max: 45)</sup> | Refers to the customer’s IP Geolocation. *We support IPv4 and IPv6 as shown in the example below. Example: 192.178.1.10 Example: IPv4 → 192.178.1.10 IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf Special characters: . : |

------

## PayFORT Fraud prevention services Response

PayFORT will send back the customer_ip details in the response

|                                 ATTRIBUTES | Description                                                  |
| -----------------------------------------: | :----------------------------------------------------------- |
| **customer_ip**<sup>( Alphanumeric )</sup> | Refers to the customer’s IP Geolocation. *We support IPv4 and IPv6 as shown in the example below. Example: 192.178.1.10 Example: IPv4 → 192.178.1.10 IPv6 → 2001:0db8:3042:0002:5a55:caff:fef6:bdbf Special characters: . : |

------

## Fraud Management (Back Office)

------

You can also manage fraud management service from the Back Office portal. 

You can follow the steps mentioned in this section to configure fraud management services

1. On the left hand side under the services menu you will find fraud management screen
2. Once you click on fraud management screen, a window as shown below will open.
3. You can configure Velocity check, hotlist, combination rules.



![](img/fraudmanagementbackoffice.jpg)



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>It is advisable to use default PayFORT settings unless your business requirements are different.</div>

You can also check out the video tutorial below



<div class="embed-responsive embed-responsive-16by9">
<iframe width="734" height="413" src="https://www.youtube.com/embed/L_mE9GqCA-8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>



## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

