# PayFORT Transaction Feedback

------

## Overview

Transaction feedback keeps you updated regarding a transaction.

The PayFORT transaction Feedback system provides you with two types of configurable notifications:

**1.** **Direct Transaction Feedback**

PayFort sends you HTTPs notifications that informs the transaction’s final status whenever a transaction is processed.
**2. Notification Transaction Feedback** 

PayFort sends you HTTPs notifications that inform the transaction’s final status whenever a transaction status is updated.

------



## Registering Transaction Feedback URLs

**1.** Log in to your back-office account.
**2.** Select the active channel under Integration Settings > Technical Settings.
**3.** Enter your Direct Transaction Feedback URL and Notification Transaction Feedback URL.
**4.** Click “Save Changes” button.



## Transaction Feedback implementation

------

The Transaction Feedback URL is required to send you the response parameters after processing the transaction on the your side.



For the Direct Transaction Feedback, it sends the immediate payments response in all cases , like if the user closed the browser before getting redirected to the Redirection URL due to a drop in the internet connection or he closed the browser during the Redirection , you will create an endpoint which accepts the notifications received from PayFort side as POST Method.



For the Notification Transaction Feedback , it’s required to provide you the transaction final status update whenever received , like if the Transaction was pending due to the unavailability for any party , the final update will be pushed to the Notification Feedback URL as POST Method.



Beyond whatever your Transaction Feedback URL does with the data received, it must also return a 2xx (like 200 , 201 , etc…) or 302 HTTP status code to update the PayFORT system that the notification was received. If your URL does not return 2xx or 302, the PayFORT will continue to retry the notification for 10 times with 10 seconds in between until it’s properly acknowledged.



<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>You can check the Direct and Notification Feedback logs in your PayFort back-office Account to check the details related to the submission like the Transaction Feedback URL which was triggered, The response which our FORT system pushed , The response Code and Status retuned from your Transaction Feedback URL.
The specifics of the data will differ based upon the financial operation that has been processed. Please refer to the FORT integration guide for more details.
If you want to change the submission type to JSON or XML, you can contact us on **integration@payfort.com**.
If you want to change the grace period or the time interval between the retries please contact us on **integration@payfort.com**.</div>

