## Transaction Response Codes

------

The Response code is made up of 5 digits; a combination of a 2-digit Status (Please see section Status Codes[<i class="fa fa-link"></i>](#status-codes)  ) and a 3-digit Message (Please see section message codes[<i class="fa fa-link"></i>](#message-codes)  )

### Status Codes

------



| Status Code | Description                                  |
| ----------: | :------------------------------------------- |
|          00 | Invalid Request.                             |
|          01 | Order Stored.                                |
|          02 | Authorization Success.                       |
|          03 | Authorization Failed.                        |
|          04 | Capture Success.                             |
|          05 | Capture failed.                              |
|          06 | Refund Success.                              |
|          07 | Refund Failed.                               |
|          08 | Authorization Voided Successfully.           |
|          09 | Authorization Void Failed.                   |
|          10 | Incomplete.                                  |
|          11 | Check status Failed.                         |
|          12 | Check status success.                        |
|          13 | Purchase Failure.                            |
|          14 | Purchase Success.                            |
|          15 | Uncertain Transaction.                       |
|          17 | Tokenization failed.                         |
|          18 | Tokenization success.                        |
|          19 | Transaction pending.                         |
|          20 | On hold.                                     |
|          21 | SDK Token creation failure.                  |
|          22 | SDK Token creation success.                  |
|          23 | Failed to process Digital Wallet service.    |
|          24 | Digital wallet order processed successfully. |
|          27 | Check card balance failed.                   |
|          28 | Check card balance success.                  |
|          29 | Redemption failed.                           |
|          30 | Redemption success.                          |
|          31 | Reverse Redemption transaction failed.       |
|          32 | Reverse Redemption transaction success.      |
|          40 | Transaction In review.                       |
|          42 | Currency conversion success.                 |
|          43 | Currency conversion failed.                  |
|          44 | 3ds success.                                 |
|          45 | 3ds failed.                                  |
|          46 | Bill creation success.                       |
|          47 | Bill creation failed.                        |
|          48 | Generating invoice payment link success.     |
|          49 | Generating invoice payment link failed.      |
|          50 | Batch file upload successfully.              |
|          51 | Upload batch file failed.                    |
|          52 | Token created successfully.                  |
|          53 | Token creation failed.                       |
|          54 | Get Tokens Success.                          |
|          55 | Get Tokens Failed.                           |
|          56 | Reporting Request Success.                   |
|          57 | Reporting Request Failed.                    |
|          58 | Token updated successfully.                  |
|          59 | Token updated failed.                        |
|          62 | Get Installment Plans Successfully.          |
|          63 | Get Installment plans Failed.                |
|          66 | Delete Token Success.                        |
|          70 | Get batch results successfully.              |
|          71 | Get batch results failed.                    |
|          72 | Batch processing success.                    |
|          73 | Batch processing failed.                     |
|          74 | Bank transfer successfully.                  |
|          75 | Bank transfer failed.                        |
|          76 | Batch validation successfully.               |
|          77 | Batch validation failed.                     |
|          80 | Credit card verified successfully.           |
|          81 | Failed to verify credit card.                |
|          88 | ValU OTP Generate Success.                   |
|          89 | ValU OTP Generate Failure Status             |
|          90 | Customer Verify Success.                     |
|          91 | Customer Verify Failed.                      |
|          92 | Verify OTP success.                          |
|          93 | Failed OTP verify.                           |

### Message Codes

------



| Message Code | Message Value                                                |
| -----------: | :----------------------------------------------------------- |
|          000 | Success.                                                     |
|          001 | Missing parameter.                                           |
|          002 | Invalid parameter format.                                    |
|          003 | Payment option is not available for this merchant’s account. |
|          004 | Invalid command.                                             |
|          005 | Invalid amount.                                              |
|          006 | Technical problem.                                           |
|          007 | Duplicate order number.                                      |
|          008 | Signature mismatch.                                          |
|          009 | Invalid merchant identifier.                                 |
|          010 | Invalid access code.                                         |
|          011 | Order not saved.                                             |
|          012 | Card expired.                                                |
|          013 | Invalid currency.                                            |
|          014 | Inactive payment option.                                     |
|          015 | Inactive merchant account.                                   |
|          016 | Invalid card number.                                         |
|          017 | Operation not allowed by the acquirer.                       |
|          018 | Operation not allowed by processor.                          |
|          019 | Inactive acquirer.                                           |
|          020 | Processor is inactive.                                       |
|          021 | Payment option deactivated by acquirer.                      |
|          023 | Currency not accepted by acquirer.                           |
|          024 | Currency not accepted by processor.                          |
|          025 | Processor integration settings are missing.                  |
|          026 | Acquirer integration settings are missing.                   |
|          027 | Invalid extra parameters.                                    |
|          029 | Insufficient funds.                                          |
|          030 | Authentication failed.                                       |
|          031 | Invalid issuer.                                              |
|          032 | Invalid parameter length.                                    |
|          033 | Parameter value not allowed.                                 |
|          034 | Operation not allowed.                                       |
|          035 | Order created successfully.                                  |
|          036 | Order not found.                                             |
|          037 | Missing return URL.                                          |
|          038 | Token service inactive.                                      |
|          039 | No active payment option found.                              |
|          040 | Invalid transaction source.                                  |
|          042 | Operation amount exceeds the authorized amount.              |
|          043 | Inactive Operation.                                          |
|          044 | Token name does not exist.                                   |
|          046 | Channel is not configured for the selected payment option.   |
|          047 | Order already processed.                                     |
|          048 | Operation amount exceeds captured amount.                    |
|          049 | Operation not valid for this payment option.                 |
|          050 | Merchant per transaction limit exceeded.                     |
|          051 | Technical error.                                             |
|          052 | Consumer is not in OLP database.                             |
|          053 | Merchant is not found in OLP Engine DB.                      |
|          054 | Transaction cannot be processed at this moment.              |
|          055 | OLP ID Alias is not valid. Please contact your bank.         |
|          056 | OLP ID Alias does not exist. Please enter a valid OLP ID Alias. |
|          057 | Transaction amount exceeds the daily transaction limit.      |
|          058 | Transaction amount exceeds the per transaction limit.        |
|          059 | Merchant Name and SADAD Merchant ID do not match.            |
|          060 | The entered OLP password is incorrect. Please provide a valid password. |
|          062 | Token has been created.                                      |
|          063 | Token has been updated.                                      |
|          064 | 3-D Secure check requested.                                  |
|          065 | Transaction waiting for customer’s action.                   |
|          066 | Merchant reference already exists.                           |
|          067 | Dynamic Descriptor not configured for selected payment option. |
|          068 | SDK service is inactive.                                     |
|          069 | Mapping not found for the given error code.                  |
|          070 | device_id mismatch.                                          |
|          071 | Failed to initiate connection.                               |
|          072 | Transaction has been cancelled by the consumer.              |
|          073 | Invalid request format.                                      |
|          074 | Transaction failed.                                          |
|          075 | Transaction failed.                                          |
|          076 | Transaction not found in OLP.                                |
|          077 | Error transaction code not found.                            |
|          078 | Failed to check fraud screen.                                |
|          079 | Transaction challenged by fraud rules.                       |
|          080 | Invalid payment option.                                      |
|          082 | Inactive fraud service.                                      |
|          083 | Unexpected user behavior.                                    |
|          084 | Transaction amount is either bigger than maximum or less than minimum amount accepted for the selected plan. |
|          086 | Installment plan is not configured for Merchant account.     |
|          087 | Card BIN does not match accepted issuer bank.                |
|          088 | Token name was not created for this transaction.             |
|          089 | Failed to retrieve digital wallet details.                   |
|          090 | Transaction in review.                                       |
|          092 | Invalid issuer code.                                         |
|          093 | service inactive.                                            |
|          094 | Invalid Plan Code.                                           |
|          095 | Inactive Issuer.                                             |
|          096 | Inactive Plan.                                               |
|          097 | Operation not allowed for service.                           |
|          098 | Invalid or expired call_id.                                  |
|          099 | Failed to execute service.                                   |
|          100 | Invalid expiry date.                                         |
|          101 | Bill number not found.                                       |
|          102 | Apple Pay order has been expired.                            |
|          103 | Duplicate subscription ID.                                   |
|          104 | No plans valid for request.                                  |
|          105 | Invalid bank code.                                           |
|          106 | Inactive bank.                                               |
|          107 | Invalid transfer_date.                                       |
|          110 | Contradicting parameters, please refer to the integration guide. |
|          111 | Service not applicable for payment option.                   |
|          112 | Service not applicable for payment operation.                |
|          113 | Service not applicable for e-commerce indicator.             |
|          114 | Token already exist.                                         |
|          115 | Expired invoice payment link.                                |
|          116 | Inactive notification type.                                  |
|          117 | Invoice payment link already processed.                      |
|          118 | Order bounced.                                               |
|          119 | Request dropped.                                             |
|          120 | Payment link terms and conditions not found.                 |
|          121 | Card number is not verified.                                 |
|          122 | Invalid date interval.                                       |
|          123 | You have exceeded the maximum number of attempts.            |
|          124 | Account successfully created.                                |
|          125 | Invoice already paid.                                        |
|          126 | Duplicate invoice ID.                                        |
|          127 | Merchant reference is not generated yet.                     |
|          128 | The generated report is still pending, you can’t download it now. |
|          129 | “Downloaded report” queue is full. Wait till its empty again. |
|          134 | Your search results have exceeded the maximum number of records. |
|          136 | The Batch file validation is failed.                         |
|          137 | Invalid Batch file execution date.                           |
|          138 | The Batch file still under validation.                       |
|          140 | The Batch file still under processing.                       |
|          141 | The Batch reference does not exist.                          |
|          142 | The Batch file header is invalid.                            |
|          144 | Invalid Batch file.                                          |
|          146 | The Batch reference is already exist.                        |
|          147 | The Batch process request has been received.                 |
|          148 | Batch file will be processed.                                |
|          149 | Payment link request id not found.                           |
|          150 | Payment link is already open.                                |
|          151 | 3ds_id does not exist.                                       |
|          152 | 3Ds verification doesn’t match the request details.          |
|          154 | You have reached the maximum number of upload retries.       |
|          155 | The upload retries is not configured.                        |
|          662 | Operation not allowed. The specified order is not confirmed yet. |
|          666 | Transaction declined.                                        |
|          773 | Transaction closed.                                          |
|          777 | The transaction has been processed, but failed to receive confirmation. |
|          778 | Session timed-out.                                           |
|          779 | Transformation error.                                        |
|          780 | Transaction number transformation error.                     |
|          781 | Message or response code transformation error.               |
|          783 | Installments service inactive.                               |
|          784 | Transaction still processing you can’t make another transaction. |
|          785 | Transaction blocked by fraud check.                          |
|          787 | Failed to authenticate the user.                             |
|          788 | Invalid bill number.                                         |
|          789 | Expired bill number.                                         |
|          790 | Invalid bill type code.                                      |

## Need further help?

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).