------

Redirection process enables you to capture payments.

PayFort Redirection consists of Authorization and Purchase processing.

# How it works?

------

The **Authorization** operation hold an amount from the Customer’s credit card account for a period of time until you capture or void the transaction. If no capture or void is processed during this period, the transaction will be voided automatically. In **Purchase** you will send one single request in order to authorize and capture the transaction amount.

We offer you to **Redirect** your Customer from your website to PayFort’s gateway page to fill out his credit card details during these operations.

**
Looking to void a payment?**
You can [void](voidauthorization.md) an authorized payment at any time. However, captured payments can only be [refunded](refund.md).



# Before you Start

------

You are required to signup for test account by visiting this [link]("https://www.payfort.com/test-account/") for testing your sample integrations. You can also directly get started by signing up for the live account by visiting this [link](https://www.payfort.com/get-started/)

# Try it out

------

You can use the below URLS to test the redirection methods.

### Endpoints

**SandBox:**

```
POST https://sbcheckout.payfort.com/FortAPI/paymentPage
```

**Live:**

```
POST https://checkout.payfort.com/FortAPI/paymentPage
```



# How to add the Tokenization service on the Redirection channel?

------

The Tokenization service is applicable to be integrated through the Redirection Channel through the below steps:

1. The Customer enables the remember_me option displayed in the payment page.
2. Processes the first PURCHASE/ AUTHORIZATION payment successfully.
3. The Merchant will receive a token_name in the response. This token_name should be considered as a permanent token name, and it can be used in the future customer’s payments by submitting the token_name in the next PURCHASE/ AUTHORIZATION payment.

If the Customer wants to update/ delete his card, you should check [Update Token](https://docs.payfort.com/docs/api/build/index.html#update-token-service) section.



# Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).