PayFort supports MasterPass, Visacheckout and ApplePay

------

## MasterPass

As another move towards a cashless environment, PayFort provides **MasterPass**; a digital wallet that securely stores the buyer’s credit card details and shipping addresses and information, making shopping through thousands of online Merchants simple and convenient. This is fulfilled by enhancing and simplifying the buyer’s digital shopping experience.

<div class="alert alert-info" role="alert"><i class="fa fa-info ">&nbsp;&nbsp;</i>PAYFORT now supports MasterPass Redirect v7 in addition to v6.</div>

### Service Endpoints

------

#### Sandbox

```html
POST https://sbcheckout.payfort.com/FortAPI/paymentPage
```

#### Live

```html
POST https://checkout.payfort.com/FortAPI/paymentPage
```

### Redirection

------

#### Integration Flow

------

1. The Merchant submits a form that includes all the parameters.

   The Merchant calls the following URL to be redirected to the FORT:  

   https://checkout.payfort.com/FortAPI/paymentPage
   
   

2. 

------