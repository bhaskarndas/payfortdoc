### ACI ReD Fraud - Request

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>The <mark><strong>fraud_extra</strong></mark> fields are custom fields as their values depend on the sector.</div>

 





**Include the following parameters in the Request you will send to PayFort:**

|                                              ATTRIBUTES | Description                                                  |
| ------------------------------------------------------: | :----------------------------------------------------------- |
|                 **customer_type** Alpha Optional max: 1 | This parameter is required if any customer detail is present. Example: B |
|           **customer_id** Alphanumeric Optional max: 16 | The Customer’s ID/ account number. Example: Au8vJ9HxLo Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|          **customer_first_name** Alpha Optional max: 30 | The Customer’s first name. Example: Osama Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|       **customer_middle_initial** Alpha Optional max: 1 | The Customer’s middle name’s initial. Example: M Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|           **customer_last_name** Alpha Optional max: 30 | The Customer’s last name. Example: Kamal Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|     **customer_address1** Alphanumeric Optional max: 30 | The Customer/ Billing address line 1. Example: Amman - Khalda Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|     **customer_address2** Alphanumeric Optional max: 30 | The Customer/ Billing address line 2 (for extra details). Example: Al Sati St. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
| **customer_apartment_no** Alphanumeric Optional max: 30 | The Customer/ Billing apartment number. Example: 12 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **customer_city** Alphanumeric Optional max: 20 | The Customer/ Billing city. Example: Amman Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|               **customer_state** Alpha Optional max: 10 | The Customer/ Billing state code. Example: Jordan            |
|      **customer_zip_code** Alphanumeric Optional max: 9 | The Customer/ Billing post/ zip code. Example: 11183 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **customer_country_code** Alpha Optional max: 3 | The Customer’s country code; ISO 3-digit country code. Example: JOR |
|             **customer_phone** Numeric Optional max: 19 | The Customer’s home phone number. Example: 00962797219966    |
|         **customer_alt_phone** Numeric Optional max: 19 | The Customer’s alternative phone. * For the Telecommunications sector, send: MSISDN. Example: 00962797256645 |
|   **customer_date_birth** Alphanumeric Optional max: 10 | The Customer’s date of birth. Format: YYYY-MM- DD. Example: 1977-10-03 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|                     **ship_type** Alpha Optional max: 1 | Shipping details present flag. * This parameter is not applicable for the Gaming sector. Example: S |
|              **ship_first_name** Alpha Optional max: 30 | Ship to first name. * This parameter is not applicable for the Gaming sector. Example: Rana Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|              **ship_middle_name** Alpha Optional max: 1 | Ship to middle initial. * This parameter is not applicable for the Gaming sector. Example: A Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|               **ship_last_name** Alpha Optional max: 30 | Ship to last name. * This parameter is not applicable for the Gaming sector. Example: Rashdan Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **ship_address1** Alphanumeric Optional max: 30 | Ship to address line 1. * This parameter is not applicable for the Gaming sector. Example: Cairo - Egypt Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ , **Space** |
|         **ship_address2** Alphanumeric Optional max: 30 | Ship to address line 2. * This parameter is not applicable for the Gaming sector. Example: Garden City Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ , **Space** |
|     **ship_apartment_no** Alphanumeric Optional max: 30 | Ship to appartment number. * This parameter is not applicable for the Gaming sector. Example: 22 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|     **ship_address_city** Alphanumeric Optional max: 20 | Ship to address city. * This parameter is not applicable for the Gaming sector. Example: Dubai Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|            **ship_address_state** Alpha Optional max: 3 | Ship to address state. * This parameter is not applicable for the Gaming sector. Example: UAE |
|          **ship_zip_code** Alphanumeric Optional max: 9 | Ship to post/ zip code. * This parameter is not applicable for the Gaming sector. Example: 11183 |
|             **ship_country_code** Alpha Optional max: 3 | Ship to country code; ISO 3-Digit country code. * This parameter is not applicable for the Gaming sector. Example: JOR |
|                 **ship_phone** Numeric Optional max: 19 | Ship to home phone number. * This parameter is not applicable for the Gaming sector. Example: 0096265534256 |
|             **ship_alt_phone** Numeric Optional max: 12 | Ship To alternative phone. * This parameter is not applicable for the Gaming sector. Example: 0797334465 |
|           **ship_email** Alphanumeric Optional max: 254 | Ship to email address. * For the Gaming sector, send: Player Email Address. Example: ship@gmail.com Special characters: @ - . _ **Space** |
|        **ship_comments** Alphanumeric Optional max: 160 | Any shipping comments. * For the Gaming sector, send: Player Email Address. Example: (Any shipping comments can be entered) Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|                   **ship_method** Alpha Optional max: 1 | The shipping method. * This parameter is not applicable for the Gaming sector. Possible/ expected values: - N (Next Day Service) - T (Two-Day Service) - W (Three- Day Service) - C (Low-Cost Carrier) - D (Customer Choice) - I (International) - M (Military) - P (Collect at Store) - O (Other) |
|         **fraud_extra1** Alphanumeric Optional max: 256 | If the sector is Retail, Gaming, Travel, or Telecommunications, then the field value must contain the “Concatenated Billing Address”. * For the Gaming sector, send: Player Email Address. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra2** Alphanumeric Optional max: 256 | If the sector is Retail, Travel, or Telecommunications, the value of the field must be the “Concatenated Shipping Address” as follows: street + + shipzip if the address is particularly long and space is lim ited then truncate the first portion of the address and send the postcode/Zip code in full. * This parameter is not applicable for the Gaming sector. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra3** Alphanumeric Optional max: 256 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Address Verification (PayPal)”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra4** Alphanumeric Optional max: 256 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Account Status (PayPal)”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra5** Alphanumeric Optional max: 256 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Eligibility Status (PayPal)”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra6** Alphanumeric Optional max: 256 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Outstanding Balance on the Account (PayPal)”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra7** Alphanumeric Optional max: 256 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Credit Score (PayPal)”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra8** Alphanumeric Optional max: 256 | If the sector is Telecommunications, the value must be the “Account Number” (if multiple MSISDN per account). Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra9** Alphanumeric Optional max: 265 | If the sector is Telecommunications, the value must be the “MSISDN Age in days”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|        **fraud_extra10** Alphanumeric Optional max: 256 | - If the sector is Travel, the value must be the “Full Travel Itinerary”. - If the sector is Telecommunications, the value must be the “Earliest Account Activity/ First Call Date”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra11** Alphanumeric Optional max: 30 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Account Age”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra12** Alphanumeric Optional max: 30 | If the sector is Retail, Travel, or Telecommunications, the value must be the “Number of Previous Orders Sent to the Shipping Address”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra13** Alphanumeric Optional max: 30 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Number of Days Since the Email Attached to the Account has Changed”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra14** Alphanumeric Optional max: 30 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Number of Days Since the Password was Changed”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra16** Alphanumeric Optional max: 30 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Number of Previous Orders Associated with the Card and Email”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra17** Alphanumeric Optional max: 30 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Event/ Promotion Flag”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra18** Alphanumeric Optional max: 30 | - If the sector is Retail, Gaming, or Telecommunications, the value must be the “Sales Channel”. - If the sector is Travel, the value must be the “Third Party Booking Flag, Yes or No”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra19** Alphanumeric Optional max: 30 | - If the sector is Retail, Travel, or Telecommunications, the value must be the “Private/ Business/ Trade” (customerType). - If the sector is Gaming, the value must be the “Customer Gaming ID”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra20** Alphanumeric Optional max: 30 | - If the sector is Retail, Gaming, or Telecommunications, the value must be the “Number of Previous Successful Transactions”. - If the sector is Travel, the value must be the “Number of Previous Successful Bookings”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra21** Alphanumeric Optional max: 30 | - If the sector is Gaming, the values must be the “Gift for Other Player Flag”. - If the sector is Travel, the value must be the “Booking Type”. - If the sector is Telecommunications, the value must be the “Payment Type”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra22** Alphanumeric Optional max: 30 | - If the sector is Gaming, the values must be the “Playing Time”. - If the sector is Travel, the value must be the “Time to First Departure in Hours”. - If the sector is Telecommunications, the value must be the “Number of Previous Successful Top-ups”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra23** Alphanumeric Optional max: 30 | If the sector is Retail, Gaming, Travel, or Telecommunications, the value must be the “Channel (IVR vs. Web vs. Mobile Application, etc.). Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra24** Alphanumeric Optional max: 30 | - If the sector is Gaming, the values must be the "Premium Account Balance”. - If the sector is Travel, the value must be the “Loyalty Scheme”. - If the sector is Telecommunications, the value must be the “Sim IMSI (International Mobile Subscriber Identity)”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **fraud_extra25** Alphanumeric Optional max: 30 | - If the sector is Gaming, the values must be the “Game Account Balance”. - If the sector is Travel, the value must be the “Loyalty Scheme Member Number”. - If the sector is Telecommunications, the value must be the “IMEI (International Mobile Equipment Identity)”. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **cart_details** Alphanumeric Optional max: 999 | This parameter is a parent parameter for other parameters that contain the details of the shopping cart created by the Merchant. Example: (Please refer to section [Cart Details Example Value](https://docs.payfort.com/docs/api/build/index.html?java#cart-details-example-value) Special characters: $ |
|           **device_fingerprint** Alphanumeric max: 4000 | Unique device ID generated by [Script](https://docs.payfort.com/docs/api/build/index.html?java#device-fingerprint-script). please refer to [Fraud Native Mobile SDK Guide](https://docs.payfort.com/pdf/PAYFORT_Fraud_Native_Mobile_SDK_V_1.2.pdf) to generate device fingerprint. Example: 04003hQUMXGB0po… Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ % + ! **Space** |

------

### ACI ReD Cart Fraud - Request

**Include the following parameters in the Request you will send to PayFort:**

|                                                ATTRIBUTES | Description                                                  |
| --------------------------------------------------------: | :----------------------------------------------------------- |
|           **item_quantity** Alphanumeric Optional max: 10 | The item’s quantity. * For the Gaming sector, send: Clan. Example: 4 |
|                **item_sku** Alphanumeric Optional max: 12 | The item’s commodity or “Stock Keeping Unit” code. * For the Gaming sector, send: Gold balance. Example: 1ShirtBlueM Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|          **item_prod_code** Alphanumeric Optional max: 12 | The item’s product code. * For the Gaming sector, send: Silver balance. Example: MOB111 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|            **item_part_no** Alphanumeric Optional max: 30 | The item’s Manufacturers Part or EAN number. * For the Gaming sector, send: Exp balance. * For the Travel sector, send: Flight/ Train/ Bus Number. Example: TSR-1002 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|       **item_description** Alphanumeric Optional max: 256 | The item’s description. * For the Gaming sector, send: Date of first credit. * For the Travel sector, send: Ticket Delivery Method. Example: iPhone 6-S Special characters: - _ `' `, . **Space** |
|                   **item_price** Numeric Optional max: 10 | The item’s unit price (lowest denomination). * For the Travel sector, send: Ticket Price. Example: 700 |
|        **item_shipping_no** Alphanumeric Optional max: 19 | The item’s shipping/ tracking number. * For the Travel sector, send: Ticket Departure Date And Time. Example: AB586985609GB Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|            **item_shipping_method** Alpha Optional max: 1 | The item’s shipping method. * For the Retail, Travel, Telecommunications sectors, send: New Shipping Address Flag. * This parameter is not applicable for the Gaming sector. Possible/ expected values: - N (Next Day Service) - T (Two-Day Service) - W (Three- Day Service) - C (Low-Cost Carrier) - D (Customer Choice) - I (International) - M (Military) - P (Collect at Store) - O (Other) |
| **item_shipping_comments** Alphanumeric Optional max: 160 | The item’s shipping comments. * For the Travel sector, send: Ticket Itinerary. Example: (Any shipping comments can be entered). Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|          **item_gift_msg** Alphanumeric Optional max: 160 | The item’s gift message. * For the Retail and Telecommunications sectors, send: High Risk Product Flag. Example: Congrats! Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|               **rcpt_title** Alphanumeric Optional max: 5 | The Recipient’s title. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Adult/Child/Infant flag. Example: Mr. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|         **rcpt_first_name** Alphanumeric Optional max: 30 | The Recipient’s first name. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Passenger First Name. Example: Mohammad Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|      **rcpt_middle_initial** Alphanumeric Optional max: 1 | The Recipient’s middle initial. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Passenger Middle Initial. Example: R Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|          **rcpt_last_name** Alphanumeric Optional max: 30 | The Recipient’s last name. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Passenger Last Name. Example: Tawfeeq Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|       **rcpt_apartment_no** Alphanumeric Optional max: 30 | The Recipient’s apartment number. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Travel Class; i.e.: Standard/ Economy etc. Example: 12 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|           **rcpt_address1** Alphanumeric Optional max: 30 | The Recipient’s address line 1. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Departure Airport/ Station Code/ City. Example: Amman - Khalda Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|           **rcpt_address2** Alphanumeric Optional max: 30 | The Recipient’s address line 2 (for extra details). * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Arrival Airport/ Station Code/ City. Example: Al Sati St. Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|               **rcpt_city** Alphanumeric Optional max: 30 | The Recipient’s city. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Booking Type. Example: Sharjah Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|              **rcpt_state** Alphanumeric Optional max: 10 | The Recipient’s state. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Departure Country 3 Digit ISO Code. Example: Qatar Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|           **rcpt_zip_code** Alphanumeric Optional max: 10 | The Recipient’s post/ zip code. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Ticket Type; i.e.: One Way/ Return etc. Example: 11183 Special characters: @ - . _ `' `/ # \ : = ? & ; ( ) $ **Space** |
|               **rcpt_country_code** Alpha Optional max: 3 | The Recipient’s country code; ISO 3-Digit country code. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Arrival Country. Example: JOR |
|                   **rcpt_phone** Numeric Optional max: 19 | The Recipient’s phone number. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. Example: 00962797675543 |
|              **rcpt_email** Alphanumeric Optional max: 45 | The Recipient’s email address. * For the Retail and Telecommunications sectors, this parameter should be sent if multiple shipping addresses are available. * For the Travel sector, send: Passenger Name Record. Example: recipient@hotmail.com Special characters: @ - . _ **Space** |

------

### ACI ReD Fraud - Response

**The following parameter will be returned in the Response:**

|                               ATTRIBUTES | Description                                                  |
| ---------------------------------------: | :----------------------------------------------------------- |
| **fraud_comment** Alphanumeric max: 1000 | “fraud_comment” this value represents the feedback of the agent reviewing “in review” transaction. This parameter is part of the Authorization/ Purchase response parameters returned on the notification URL after the In review transaction is updated. Example: Close |