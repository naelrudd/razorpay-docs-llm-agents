> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create Payout Links

> Create Payout Links via the Dashboard, API and explore the other Payout Links Dashboard actions available in RazorpayX.

Available in
🇮🇳 India

You can create Payout Links in two ways:

* [Via the Dashboard](#create-a-payout-link).
* [Via Payout Links APIs](https://razorpay.com/docs/x/payout-links/api.md).

You can also [create Payout Links in bulk](https://razorpay.com/docs/x/payout-links/bulk.md).

> [!WARNING]
>
> **Watch Out!**
>
> You cannot create Payout Links in [Test mode](https://razorpay.com/docs/x/dashboard/test-mode.md) on the Dashboard and APIs. Switch to Live mode and use [Live API keys](https://razorpay.com/docs/x/dashboard/api-keys.md) to create a successful Payout Link.

## Create a Payout Link

Watch this video to know how to create a Payout Link or read along.

[Create a Payout Link | RazorpayX](https://www.youtube.com/embed/yGxzEFjRSSw)

To create a Payout Link:

1. Log in to your [RazorpayX Dashboard](https://x.razorpay.com/).
2. Navigate to **Payout Links** from the left menu.
3. Click **+PAYOUT LINK**.

   ![Payout Links Dashboard highlighting +PAYOUT LINK](https://razorpay.com/docs/build/browser/assets/images/create-payout-link.jpg)
4. Fill in the necessary details such as:
   * The account from which the money must be debited.

     ![Add the account from which the amount must be debited](https://razorpay.com/docs/build/browser/assets/images/x-payout-links-create1.jpg)
   * The Contact to whom you are making the payout. Or, click **Add a new contact** to [create a new Contact](https://razorpay.com/docs/x/contacts#create-a-contact).

     ![Add the Contact to whom you want to send the link or add a new contact](https://razorpay.com/docs/build/browser/assets/images/x-payout-links-create2.jpg)
   * The contact's email id and phone number. Choose where of the two you want to send the Payout Link to.

     ![. Choose email id/mobile number](https://razorpay.com/docs/build/browser/assets/images/x-payout-links-create3.jpg)
   * Mandatory details like the Payout Link Amount, Purpose and Description. [Set expiry](https://razorpay.com/docs/x/payout-links/set-expiry.md) for the link if applicable.
     * Additional optional details such as reference id and internal notes under **Add more details**.

![finalise the payout amount and other details](https://razorpay.com/docs/build/browser/assets/images/x-payout-links-create4.jpg)

1. Enter the OTP sent to your registered mobile number or email address, and confirm creation of the Payout Link.

You have successfully created a Payout Link.

> [!NOTE]
>
> **Handy Tips**
>
> When selecting a contact, you need not specify the associated fund account. If the fund account is already present then the payout amount is immediately transferred.

### When Approval Workflow is Enabled

In some use cases, you can send the Payout Link for approval from the approver and then forward the link to the contact. Given below is the Payout Link creation flow when If [Approval Workflow](https://razorpay.com/docs/x/manage-teams/approval-workflow.md) is enabled.

1. [Create a Payout Link](#create-a-payout-link) on the Dashboard.
2. The Payout Link is then sent to the **Approver** for approval.
3. Once approved, the Payout Link is sent to the Contact on the number and email provided.

> [!NOTE]
>
> **Handy Tips**
>
> You can set [expiry on Payout Links](https://razorpay.com/docs/x/payout-links/set-expiry.md).

## Other Actions

From the Overview page, click on the specific Payout Link and view its details. In the summary pop-up page, you can also:

* Copy the Payout Link.
* Resend the Payout Link to the same contact and repeat the transaction.
* Cancel the Payout Link.

  You can also hover over the Payout Link row and access the copy, resend and cancel Payout Link options.

![Summary pop-up page showing the Payout Link details on RazorpayX Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-payout-links-summary.jpg)

* Using the **Quick Filters** menu, filter out the Payout Links and transactions based on their status and other details.
* As an [Owner/Approver](https://razorpay.com/docs/x/manage-teams/approval-workflow.md), view the Payout Links pending on you from the same menu. Also view the Payout Links pending on a specific [user role](https://razorpay.com/docs/x/manage-teams.md).
* Click the download icon to download the Payout Links report for a specific time range. Download as a `CSV` or an `XLS` file or email it.

![Quick filters menu on Payout Links Dashboard](https://razorpay.com/docs/build/browser/assets/images/payout-links-quick-filters.jpg)

### Related Information

* [Payout Links API](https://razorpay.com/docs/api/x/payout-links.md)
* [Create Bulk Payout Links](https://razorpay.com/docs/x/payout-links/bulk.md)
* [Shopify Payout Links](https://razorpay.com/docs/x/payout-links/shopify.md)
