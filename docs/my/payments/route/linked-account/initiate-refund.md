> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Initiate Refund - Linked Account Dashboard

> Initiate a refund from the Linked Account Dashboard.

Available in
🇮🇳 India
🇲🇾 Malaysia

The Linked Account users can initiate a refund for individual transaction levels or in batches from the Linked Account Dashboard. They can also make full and partial refunds to the customers.

You can initiate the following types of refunds from the Linked Account: [Individual Refund](https://razorpay.com/docs/my/payments/route/linked-account/initiate-refund.md#individual-refund), [Full Refund](https://razorpay.com/docs/my/payments/route/linked-account/initiate-refund.md#full-refund), [Partial Refund](https://razorpay.com/docs/my/payments/route/linked-account/initiate-refund.md#partial-refund) and [Batch Refund](https://razorpay.com/docs/my/payments/route/linked-account/initiate-refund.md#batch-refund).

## Refund Checklist

* Ensure you have sufficient nodal balance to create a refund.
* To allow refund capability for an existing account, go to the **Accounts** tab and enable the **Allow Refunds** option against the relevant account.

![Refund checklist page](https://razorpay.com/docs/build/browser/assets/images/route_allow_refund.jpg)

## Initiate Refund

See how you can initiate the following types of refunds from your Dashboard.

> [accordion] Individual Refund
>
> To issue an individual refund:
>
> 1. Log in to the Dashboard and click **Route** under **PAYMENT PRODUCTS**.
> 2. Go to the **Transfers** tab.
> 3. Select the **Refund to Customer** option.
> 4. Enter the refund amount and add a description in the **Notes** field.

> [accordion] Full Refund
>
> To initiate a full refund:
>
> 1. Enter the full transaction amount.
> 2. Click **Create Full Refund**.
>
> The screen appears as shown below:
>
> ![Full refund page](https://razorpay.com/docs/build/browser/assets/images/Route-Full-Refund.jpg)

> [accordion] Partial Refund
>
> To initiate a partial refund:
>
> 1. Enter an amount lower than the total transaction value.
> 2. Click **Create Partial Refund**.
>
> The screen appears as shown below:
>
> ![Partial refund page](https://razorpay.com/docs/build/browser/assets/images/Route-Partial-Refund.jpg)

> [accordion] Batch Refund
>
> Using Batch refund, you can process a large volume of refund from the Linked Accounts Dashboard.
>
> To initiate batch refund:
>
> 1. Download the Batch Refund Format - Click the download button to obtain the .csv format, wherein the transaction details can be entered.
> 2. Enter the necessary information in the file.
> 3. Upload the Batch Refund Format - After entering all the necessary details, upload the file.
>
> Once uploaded, if the funds are sufficient, the batch file is processed.
>
> #### Process Batch Refund
>
> After the batch refund is processed, you can download the output file to view the reversals. In case some of the batch records were not processed, an error is displayed for such records. You may then attempt a repeat refund after handling the errors.

### Related Information

* [Route](https://razorpay.com/docs/my/payments/route)
* [Linked Accounts](https://razorpay.com/docs/my/payments/route/linked-account.md)
* [Reversals and Settlements](https://razorpay.com/docs/my/payments/route/linked-account/reversals-settlements.md)
* [Manage Profile and Team](https://razorpay.com/docs/my/payments/route/linked-account/manage-profile.md)
