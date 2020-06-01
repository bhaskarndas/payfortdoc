With PayFort you can accept card payments from all major global providers and many local payment methods 

------

## Endpoints

**Sandbox**

```http
POST https://sbpaymentservices.PayFort.com/FortAPI/paymentApi
```

**Live**

```http
POST https://paymentservices.PayFort.com/FortAPI/paymentApi
```

------



## Supported card schemes

We support the following international and domestic card schemes:

### International

------



- Visa
- Mastercard
- American Express
- Discover
- Diners Club
- JCB
- UnionPay

### Local

------

Capture the opportunity to expand your business reach by accepting Mada cards to enhance the customer experience on your checkout page. Payfort has partnered with MADA under the supervision of SAMA in taking a strategic initiative to enable all MADA cards for online buyers to enjoy a convenient way to digitalize cash and increase the spend through their existing MADA cards through various KSA e-commerce merchants. There are around 30 million MADA debit cards being issued by 16 member banks in KSA.

PAYFORT gateway also supports Sadad for Merchants residing in the Kingdom of Saudi Arabia (KSA). More and more Saudi businesses are beginning to rely on online payment processes that’s why the addition of SADAD account to PAYFORT will provide businesses with the means to accept payments. At the moment Payfort supports following local payment methods:

<div class="container">


  <ul class="nav nav-tabs">
    <li class="active"><a data-toggle="tab" href="#sadad">Sadad</a></li>
    <li><a data-toggle="tab" href="#knet">KNET</a></li>
    <li><a data-toggle="tab" href="#mada">Mada</a></li>
    <li><a data-toggle="tab" href="#naps">NAPS</a></li>
    <li><a data-toggle="tab" href="#omannet">Oman NET</a></li>
     <li><a data-toggle="tab" href="#meeza">MEEZA</a></li>
  </ul>

  <div class="tab-content">
    <div id="sadad" class="tab-pane fade in active">
    <h1></h1>
    <div class="table">
    <div class="tr">
    <div class="td">
    <b>User Countries</b>
    </div>

    </div>
    <div class="tr">
    <div class="td">
    <b>Middle East/North Africa:</b>
    </div>
    <div class="td">
    <ul><li>Saudi Arabia</li></ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Clearing and settlement:</b>
    </div>
    <div class="td"><ul><li>Instant</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Processing currencies:</b>
    </div>
    <div class="td"><ul><li>Saudi Riyal</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Default settlement currency:</b>
    </div>
    <div class="td"><ul><li>Saudi Riyal</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Partial refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    </div>
    
    </div>
    <!--KNET code-->
    <div id="knet" class="tab-pane fade in active">
    <h1></h1>
    <div class="table">
    <div class="tr">
    <div class="td">
    <b>User Countries</b>
    </div>
    
    </div>
    <div class="tr">
    <div class="td">
    <b>Middle East/North Africa:</b>
    </div>
    <div class="td">
    <ul><li>Kuwait</li></ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Clearing and settlement:</b>
    </div>
    <div class="td"><ul><li>Instant</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Processing currencies:</b>
    </div>
    <div class="td"><ul><li>KWD</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Default settlement currency:</b>
    </div>
    <div class="td"><ul><li>KWD</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Partial refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    </div>
    </div>
    
    <!-- MADA Code-->
    <div id="mada" class="tab-pane fade in active">
    <h1></h1>
    <div class="table">
    <div class="tr">
    <div class="td">
    <b>User Countries</b>
    </div>
    
    </div>
    <div class="tr">
    <div class="td">
    <b>Middle East/North Africa:</b>
    </div>
    <div class="td">
    <ul><li>Saudi Arabia</li></ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Clearing and settlement:</b>
    </div>
    <div class="td"><ul><li>Instant</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Processing currencies:</b>
    </div>
    <div class="td"><ul><li>SAR</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Default settlement currency:</b>
    </div>
    <div class="td"><ul><li>SAR</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Partial refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    </div>
    </div>
    <!--Code for NAPS-->
    <div id="naps" class="tab-pane fade in active">
    <h1></h1>
    <div class="table">
    <div class="tr">
    <div class="td">
    <b>User Countries</b>
    </div>
    
    </div>
    <div class="tr">
    <div class="td">
    <b>Middle East/North Africa:</b>
    </div>
    <div class="td">
    <ul><li>Qatar</li></ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Clearing and settlement:</b>
    </div>
    <div class="td"><ul><li>Instant</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Processing currencies:</b>
    </div>
    <div class="td"><ul><li>Qatari Riyal</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Default settlement currency:</b>
    </div>
    <div class="td"><ul><li>Qatari Riyal</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Partial refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    </div>
    </div>
    
    <!--Code for omannet-->
    <div id="omannet" class="tab-pane fade in active">
    <h1></h1>
    <div class="table">
    <div class="tr">
    <div class="td">
    <b>User Countries</b>
    </div>
    
    </div>
    <div class="tr">
    <div class="td">
    <b>Middle East/North Africa:</b>
    </div>
    <div class="td">
    <ul><li>Oman</li></ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Clearing and settlement:</b>
    </div>
    <div class="td"><ul><li>Instant</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Processing currencies:</b>
    </div>
    <div class="td"><ul><li>Oman Riyal</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Default settlement currency:</b>
    </div>
    <div class="td"><ul><li>Oman Riyal</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Partial refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    </div>
    </div>
    
    <!--Code for Meeza-->
    <div id="meeza" class="tab-pane fade in active">
    <h1></h1>
    <div class="table">
    <div class="tr">
    <div class="td">
    <b>User Countries</b>
    </div>
    
    </div>
    <div class="tr">
    <div class="td">
    <b>Middle East/North Africa:</b>
    </div>
    <div class="td">
    <ul><li>Egypt</li></ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Clearing and settlement:</b>
    </div>
    <div class="td"><ul><li>Instant</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Processing currencies:</b>
    </div>
    <div class="td"><ul><li>EGP</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Default settlement currency:</b>
    </div>
    <div class="td"><ul><li>EGP</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    <div class="tr">
    <div class="td">
    <b>Partial refunds:</b>
    </div>
    <div class="td"><ul><li>YES</li> </ul></div>
    </div>
    </div>
    </div>
    </div></div>

------







#### SADAD

------

Start accepting payments using SADAD, the payment method in Saudi Arabia.

**The request**

Placeholder: Input Parameters to be added here for SADAD

**The Response**

Placeholder: The response sample

------

#### KNET

------

Start accepting payments using KNET, the leading payment method in Kuwait.

**The request**

Placeholder: Input Parameters to be added here for KNET

**The Response**

Placeholder: The response sample

------

#### MADA

------

Start accepting payments using Mada, the leading payment method in Saudi Arabia.

**The request**

Placeholder: Input Parameters to be added here for MADA

**The Response**

Placeholder: The response sample

------

#### NAPS

------

Start accepting payments using NAPS, the leading payment method in QATAR.

**The request**

Placeholder: Input Parameters to be added here for NAPS

**The Response**

Placeholder: The response sample

------

#### OMAN NET

------

Start accepting payments using OMAN NET, the leading payment method in OMAN.

**The request**

Placeholder: Input Parameters to be added here for OMAN

**The Response**

Placeholder: The response sample

------

#### MEEZA

------

Start accepting payments using MEEZA, the leading payment method in EGYPT.

**The request**

Placeholder: Input Parameters to be added here for OMAN

**The Response**

Placeholder: The response sample

------

## Test Your Card Integration

------

You can checkout this [link](testing.md) for testing your card integration.



## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

------



## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).