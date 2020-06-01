# Mobile SDKs

------

The **PayFORT Mobile SDK** allows you to securely integrate the payment functions. It also allows you to easily accept In-App payments. Instead of the traditional, time-consuming, and complex way of being redirected to the mobile browser to complete the payment, In-App payments can be completed through our **FORT Mobile SDK**. In turn, this gives the your customers a smooth, pleasing user-experience by using In-App payment functions through the native applications.

## Features of PayFort SDKs

------

- Native in-app payment.
- Fully secure.
- Fully customized.

------

## Mobile SDK Integration Workflow

![mobilesdk workflow](img\mobilesdkworkflow.JPG)

When your customer initiates the payment on your merchant app, your app requests Payfort server for a new token every time, then process the customer's payment. When PayFort server sends a successful response to your site your backend is notified of successful payment and your backend server confirms the same with Payfort server.

Here is the description of mobile sdk integration workflow:

1. The Merchant’s application initiates the FORT Mobile SDK and passes the parameters to the FORT Mobile SDK.
2. The FORT Mobile SDK starts a secure connection and passes the received parameters to the FORT API to be validated. 
3. The FORT API returns the validation response. 
4. The FORT Mobile SDK submits the cardholder’s data to the FORT API to process the order. 
5. The FORT API validates and processes the order with the third parties. 
6. The FORT API returns the FORT response. 
7. The FORT Mobile SDK returns the response to the corresponding callback method.

For more details on PayFORT Android SDK Integration visit this [link](androidsdk.md)

For more details on PayFORT iOS SDK Integration visit this [link](iossdk.md)



## Mobile SDK Libraries

------

You can download the two available FORT mobile sdk libraries from this section.

<div class="row">
  <div class="col-sm-6">
    <div class="card">
      <div class="card-block text-center">
        <h3 class="card-title ">iOS</h3>
          <i class="fa fa-apple fa-5x " aria-hidden="true" ></i>
        <p class="card-text">The FORT Mobile SDK supports all devices running iOS 8+
</p>

        <div class="row">
  			<div class="col-sm-6">
    			<div class="card">
      				<div class="card-block">
        			 <i class="fa fa-book fa-2x btn btn-primary" aria-hidden="true " href="https://docs.payfort.com/pdf/FORT_Mobile-SDK_iOS_Integration_Guide_v_3.7.pdf"></i>
        			 <p class="card-text"><small class="text-muted">Get Started</small></p>

      				</div>
    			</div>
  		</div>
  		
  <div class="col-sm-6">
    			<div class="card">
      				<div class="card-block">
        				 <i class="fa fa-apple fa-2x btn btn-primary" aria-hidden="true " href="https://docs.payfort.com/docs/api/build/lib/PayFortSDK2.1.zip">							</i>
        					 <p class="card-text">
        			 		<small class="text-muted">SDK 2.1 for iOS						</small>
        			 		</p>

      					</div>
    				</div>
  				</div>
  			</div>
        
      </div>
    </div>
  </div>
  <div class="col-sm-6">
    <div class="card">
      <div class="card-block text-center">
        <h3 class="card-title">Android</h3>
        <i class="fa fa-android fa-5x" aria-hidden="true" ></i>
        <p class="card-text">The FORT Mobile SDK supports all devices running Android 4.1.x (API level 16).</p>

            <div class="row">
  			<div class="col-sm-6">
    			<div class="card">
      				<div class="card-block">
        			 <i class="fa fa-book fa-2x btn btn-primary" aria-hidden="true " href="https://docs.payfort.com/pdf/FORT_Mobile-SDK_Android_Integration_Guide_v_3.3.pdf" ></i>
        			 <p class="card-text"><small class="text-muted">Get Started</small></p>

      				</div>
    			</div>
  		</div>
  		<div class="col-sm-6">
    			<div class="card">
      				<div class="card-block">
        			 <i class="fa fa-android fa-2x btn btn-primary" aria-hidden="true " href="https://docs.payfort.com/docs/api/build/lib/FORTSDKv1.5.zip"></i>
        			 <p class="card-text"><small class="text-muted">SDK 1.5 for Android</small></p>

      				</div>
    			</div>
  		</div>
  		</div>
      </div>
    </div>
  </div>
</div>

------

## Mobile SDK Token

------



<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>A Mobile SDK Token is required to authenticate every request sent to the SDK. The Token is also important to process payment operations in the FORT through our FORT Mobile SDK.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>A unique Token should be created for each transaction. Each Token has a life-time of only one hour if no new request from the same device is sent.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>The creation and initiation of a Mobile SDK Token happens on your server side.</div>

------

## SDK Token Endpoints

### Sandbox

```
POST  https://sbpaymentservices.payfort.com/FortAPI/paymentApi
```

### Live

```
POST  https://paymentservices.payfort.com/FortAPI/paymentApi
```

### SDK Token Request

------

Placeholder for sample code.

You can check out the full list of parameters that are required for SDK Token request by visiting this [link](sdktokenparameters.md)

### SDK Response

------

Placeholder for sample JSON response.

## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

Check out iOS integrations by visiting this [link](iossdk.md)

Check out Android integrations by visiting this [link](androidsdk.md)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

