> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Fund Account Validation

> Validate your customer's fund account to ensure it is the right account number.

Available in
🇮🇳 India

It is important to validate your customer's fund account to ensure it is the account number where the user wants to receive the amount. Fund account validation is possible only for RazorpayX Lite.

Know more about [Account Validation](https://razorpay.com/docs/api/x/account-validation.md).

> [!WARNING]
>
> **Watch Out!**
>
> * If your user provides an account number by mistake which is not where the user wants the amount, the payout gets processed if the account number exists. Hence, we recommend you to validate the Fund accounts before making a payout.
> * Fund Account Validation is possible only for RazorpayX Lite.
> * Fund accounts once created can not be deleted.

## Workflow

Below is a high-level diagrammatic overview of how to validate a contact's fund account in RazorpayX.

![Fund Account Validation Transaction Workflow. To do so, refer to the steps below.](https://razorpay.com/docs/build/browser/assets/images/RZPX-RZPX-account-validation-flow.jpg)

The process to validate a fund account is similar to making a regular payout.

1. Create a contact.
2. Create a fund account using the bank account details or VPA you want to validate.
3. Create an account validation transaction to validate the account.

## Account Validation States

Here is an illustration of life cycle of a fund account validation transaction.

![Fund Account Validation Transaction States. Fund account validation, once created, can either be completed successfully, or it could fail.](https://razorpay.com/docs/build/browser/assets/images/RZPX-fav.jpg)

### Created

This state is assigned to an account validation transaction after Razorpay receives the API request. At this stage, we are awaiting a response from the beneficiary's bank. The account details have not been validated. We do not recommend making payouts to the account while the account validation transaction is still in this status.

### Completed

This state indicates that the account validation transaction was completed.

> [!WARNING]
>
> **Watch Out!**
>
> The `completed` status does not mean the bank account or VPA is valid. It just means the account validation transaction was completed and results are available to you via the API response and webhooks payloads. \
> &#x20;Based on the response, you can decide if you should make a payout to the account.

### Failed

This state indicates that the account validation transaction has failed due to a technical error or if IMPS is disabled by the beneficiary bank.

## Validation Conditions

> [accordion] Validate a Bank Account
>
> You can only validate the following information for a contact's bank account:
>
> * **Bank Account Number**: When the status of the transaction changes to `completed`, the bank passes on the bank account status in the API response. If the account is active, you can transfer funds to the account.
>
> * **Beneficiary Validation**: When the status of the transaction changes to `completed`, the bank passes on the name linked to the account in the API response. By comparing the name sent by the bank to the name provided by the customer, you can successfully validate if the account belongs to the same customer.
>
> * **Amount Validation**: If you want to perform an amount validation, transfer a random amount ranging between ₹1 and ₹2, for example, ₹1.27. Ask your contact to enter the amount received on your website. This acts as an additional check to validate that the customer has access to the account.

> [accordion] Validate a VPA
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > It is not possible to perform an amount validation for your contact's VPA.
>
> You can only validate the following information for a contact's VPA:
>
> * **Address Validation (VPA)**: When the status of the transaction changes to `completed`, the bank passes on the status of the VPA in the API response. If the VPA is active, you can transfer funds to the VPA.
>
> * **Beneficiary Validation**: When the status of the transaction changes to `completed`, the bank passes on the name linked to the VPA in the API response. By comparing the name sent by the bank to the name provided by the customer, you can successfully validate if the account belongs to the same customer.

### Related Information

* [Fund Account Validation FAQs](https://razorpay.com/docs/x/fund-accounts/faqs.md#fund-account-validation)
* [Fund Account Validation APIs](https://razorpay.com/docs/x/fund-account-validation/api.md)
