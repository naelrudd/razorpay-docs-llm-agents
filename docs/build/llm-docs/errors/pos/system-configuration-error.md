# Razorpay POS System and Configuration Errors

Below are the system and configuration-related error codes associated with POS payments, along with their details, error objects and current status.

**INFO**

For generic API errors such as invalid parameters, missing fields, authentication failures and server errors, refer to [Common Errors](https://razorpay.com/docs/build/llm-docs/errors/common.md).

    
### Merchant and terminal configuration

         
Error | Error Code | Description | Next Steps
---
Pricing not configured for merchant (for payment combination) | PGIP000012 | Pricing is not configured for this payment method. | Configure pricing for all supported payment methods and contact merchant support if needed.
---
Multiple conflicting pricing rules | PGIP000013 | Multiple conflicting pricing rules are configured. | Review and resolve conflicting pricing rules in configuration.
---
No active terminal found for payment | PGIP000014 | The terminal was not found or is not configured properly. | Verify terminal configuration and mapping.
---
Extra pricing rules found | - | Extra pricing rules were found in the configuration. | Review pricing rules and remove conflicts.
---
Pricing rule missing | - | The pricing rule is missing for this payment method. | Configure the pricing rule and retry.
         
        

    
### Gateway setup issues

         
Error | Error Code | Description | Next Steps
---
Gateway setup not correct or configuration error | PGIP000022 | The gateway setup is incorrect or has configuration errors. | Verify gateway configuration and credentials.
---
Terminal not configured at gateway | - | The terminal is not configured at the gateway. | Configure the terminal at the gateway and retry the transaction.
---
Gateway authentication failed | - | Gateway authentication failed. | Verify gateway credentials and retry the transaction.
         
        

    
### PGR errors

         
Error | Error Code | Description | Next Steps
---
POS not activated for merchant | PGPR000158 | POS is not activated for this merchant. | Activate POS for the merchant before retrying.
---
Method not enabled for the merchant | PGPR000033 | The payment method is not enabled for this merchant. | Enable the payment method for the merchant and retry.
---
PGR service unavailable or exception errors (500 errors) | PGPR000052 | PGR service is unavailable or encountered an internal error. | Retry after some time. If it persists, contact support.
---
Missing source_channel or method parameters | PGPR000101 | Required parameters such as `source_channel` or `method` are missing. | Provide the required parameters and retry.
---
Omni flags misconfigured | PGPR000101 | Omni flags are misconfigured. | Correct the omni flag configuration and retry.
---
Omni feature not enabled | PGPR000101 | Omni feature is not enabled for this merchant. | Enable the Omni feature for the merchant and retry.
