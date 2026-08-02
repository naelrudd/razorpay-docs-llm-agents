# Razorpay POS Device and Hardware Errors

Below are the device and hardware-related error codes associated with POS payments, along with their details, error objects and current status.

**INFO**

For generic API errors such as invalid parameters, missing fields, authentication failures and server errors, refer to [Common Errors](https://razorpay.com/docs/build/llm-docs/errors/common.md).

    
### Device interaction

         
Error | Description | Next Steps
---
Card read failure | Card data could not be read from tap, swipe or insert. | Ask the customer to retry the transaction and re-tap, swipe or insert the card.
---
Card read but found as invalid | Card data was read but found invalid. | Retry the transaction or use a different card.
         
        

    
### Device hardware issues

         
Error | Description | Next Steps
---
Card data could not be read because of reader malfunction | Card data could not be read because of a reader malfunction. | Check the reader and retry, or use another device.
---
Device offline or not connected | The device is offline or not connected. | Ensure the device is powered on and connected before retrying.
         
        

    
### Invalid card type

         
Error | Description | Next Steps
---
Card type not supported on device (for example, Amex on D180) | The card type is not supported on the device. | Use a supported card or a compatible device.
---
Wrong entry mode for card type (for example, chip card swiped when chip is available) | The card was presented in the wrong entry mode. | Use the correct entry mode and retry the transaction.
         
        

    
### User action issues

         
Error | Description | Next Steps
---
Transaction cancelled by user | The customer cancelled the transaction. | Ask the customer to initiate the transaction again.
---
Card removed too early | The card was removed too early. | Ask the customer to keep the card inserted until prompted and retry.
---
Multiple cards detected | Multiple cards were detected. | Ask the customer to present only one card and retry.
         
        

    
### Device authentication and session management

         
Error | Description | Next Steps
---
Device authentication failed (user or device mapping) | Device authentication failed for the user or device mapping. | Verify the device-user mapping and re-authenticate the device.
---
Device inactive or blocked in production mode or whitelisted for test mode | The device is inactive or blocked in production mode or whitelisted only for test mode. | Activate or unblock the device, or use a production-enabled device.
---
Session expired or invalid | The session expired or is invalid. | Start a new session and retry the transaction.
---
RKI required on device for data encryption | RKI is required on the device for data encryption. | Complete RKI on the device before retrying.
         
        

    
### Card reading errors from production

         
Error | Error Code | Description | Next Steps
---
Bad Track2 data | PGIP000035 | Track 2 data on the card's magnetic stripe is invalid or corrupted. | Ask the customer to retry swiping the card or use chip/contactless. If it persists, use another card.
---
Card read error. Please retry | PGIP000043 | The card could not be read by the terminal. | Ask the customer to retry reading the card using chip, swipe or contactless.
         
        

    
### Security and encryption errors

         
Error | Error Code | Description | Next Steps
---
Card decryption failed | PGIP000009 | Card data received from the device could not be decrypted. | Retry the transaction. If the issue persists, contact Razorpay support.
---
Invalid card data post decryption | PGIP000010 | Card data is invalid after decryption. | Retry the transaction. If the issue persists, contact support.
---
Encryption key not found or expired | PGIP000011 | The encryption key required for secure communication is not found or has expired. | Retry the transaction. If the issue persists, perform remote key injection.
---
Key exchange failure | PGIP000015 | Key exchange with the terminal failed. | Retry the transaction. If the issue persists, perform remote key injection.
---
Key exchange failure with terminals (internal) | PGIP000016 | Internal key exchange failed with the terminal. | Retry the transaction. If the issue persists, perform remote key injection.
---
Key change required (TSS) | PGIP000017 | Key change is required before processing the payment. | Perform remote key injection and retry the transaction.
---
No security module | PGIP000032 | The security module required for encryption or decryption is not available. | Retry the transaction. If the issue persists, check the terminal security module configuration.
---
Invalid message in TLE or UKPT | PGIP000026 | The encryption message format is invalid in TLE or UKPT communication. | Retry the transaction. If the issue persists, contact technical support.
---
TLE track decryption error | PGIP000009 | Track data decryption failed in TLE. | Retry the transaction. If the issue persists, contact support.
         
        

    
### Translation layer errors

         
Error | Description | Next Steps
---
Missing mandatory fields in translated request | The translated request is missing mandatory fields. | Ensure all required fields are included and retry the request.
---
Invalid data types or formats | The translated request contains invalid data types or formats. | Correct the data types or formats and retry the request.
---
Encryption or decryption failure | Encryption or decryption failed during translation. | Retry the request. If the issue persists, contact Razorpay support.
         
        

    
### Other device-related errors

         
Error | Description | Next Steps
---
Invalid card number. Resolution = RKI | The card number is invalid and requires key exchange. | Perform remote key injection and retry the transaction.
---
No terminal mapped to device | No terminal is mapped to the device. | Map a terminal to the device and retry.
