# Mobile SDKs

------

The **PayFORT Mobile SDK** allows you to securely integrate the payment functions. It also allows you to easily accept In-App payments. Instead of the traditional, time-consuming, and complex way of being redirected to the mobile browser to complete the payment, In-App payments can be completed through our **FORT Mobile SDK**. In turn, this gives the your customers a smooth, pleasing user-experience by using In-App payment functions through the native applications.

## Features of PayFort SDKs

------



- Native in-app payment.
- Fully secure.
- Fully customized.

------

## Mobile SDK Libraries

------



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



<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>A Mobile SDK Token is required to authenticate every request sent to the SDK. The Token is also significant to process payment operations in the FORT through our FORT Mobile SDK.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>A unique Token should be created for each transaction. Each Token has a life-time of only one hour if no new request from the same device is sent.</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>The creation and initiation of a Mobile SDK Token happens on the Merchant’s server side.</div>

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

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Every parameter the Merchant sends in the Request should be received by the Merchant in the Response -even the optional ones.</div>



## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

