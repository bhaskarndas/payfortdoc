# Redirections

## Authorization and Purchase

Operations that help the Merchant to complete the payment process. The **Authorization** operation hold an amount from the Customer’s credit card account for a period of time until the Merchant capture or void the transaction. If no capture or void was processed during this period, the transaction will be voided automatically. In **Purchase** you will send one single request in order to authorize and capture the transaction amount.
We offer the Merchant to **Redirect** the Customer from his website to PayFort’s gateway page to fill out his credit card details during these operations.

------

## Authorization/ Purchase URLs

**Test Environment URL:**

https://sbcheckout.payfort.com/FortAPI/paymentPage

**Production Environment URL:**

https://checkout.payfort.com/FortAPI/paymentPage

------

## Parameters Submission Type

HTTPs Form Post Request.



```html
<form method="post" action="https://sbcheckout.payfort.com/FortAPI/paymentPage" id="form1" name="form1"> </form>
```



------

## Authorization/ Purchase - Request

Please take a look at the **Authorization/ Purchase Request Example** on the right side of the page.