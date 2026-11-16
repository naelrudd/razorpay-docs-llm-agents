> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create Bulk Payout Links

> Create and process bulk Payout Links and know about the bulk Payout Links' status.

Available in
🇮🇳 India

Create Payout Links in bulk using the **Bulk Payout Links** feature. You can create Payout Links for:

* Recipients whose contact details you do not know.
* Recipients whose contact details you know.

You need your recipients' contact details to send the link. Once they receive the Payout Link, they can enter their account details. RazorpayX then creates a [Contact](https://razorpay.com/docs/x/contacts) and the respective [Fund Account](https://razorpay.com/docs/x/fund-accounts).

To create Bulk Payout Links from the RazorpayX Dashboard:

1. Download the [sample template](#sample-template).
2. Add data to the template as per the [required fields](#requested-fields-in-template).
3. Upload the template on the [Dashboard](https://x.razorpay.com/).

![Create Bulk Payout Links Process from uploaded → created → processed](https://razorpay.com/docs/build/browser/assets/images/RZPX-bulk-upload.jpg)

## Sample Template

Download the sample template in `.csv` format. Check the fields you must populate to create corresponding Payout Links.

[Download .csv](https://razorpay.com/docs/build/browser/assets/images/sample_batch_payout_links.csv)

### Requested Fields in Template

The table below lists the requested fields listed in the [sample template](#sample-template) and describes each field.

`Name of Contact` *mandatory*
: `string` The contact's name. This field is case-sensitive. Has a minimum of 3 characters. and a maximum of 50 characters is allowed. The name cannot end with a special character, except `.`. Supported characters: `a-z`, `A-Z`, `0-9`, `space`, `’` , `-` , `_` , `/` , `(` , `)` and , `.`. For example, `Gaurav Kumar`.

`Payout Link Amount` *mandatory*
: `number` The amount, in paise, to be transferred to the contact. For example, `1000`. The minimum value is `100`.

`Contact Phone Number` *mandatory*
: `string` The contact's phone number. For example, `9000090000`.

`Contact Email ID` *mandatory*
: `string` The contact's email address. For example, `gaurav.kumar@example.com`.

`Send Link to Phone Number` *mandatory*
: `string` Determines who sends the Payout Link to the contact via SMS. Possible values:

* `Yes`: Razorpay sends the Payout Link to the contact via SMS.
* `No`: You send the Payout Link to the contact via SMS.

The possible values are case-sensitive.

`Send Link to Mail ID` *mandatory*
: `string` Determines who sends the Payout Link to the contact via email. Possible values:

* `Yes`: Razorpay sends the Payout Link to the contact via email.
* `No`: You send the Payout Link to the contact via email.

The possible values are case-sensitive.

`Contact Type` *mandatory*
: `string` The classification of contact that is being created. For example, `employee`. The following classifications are available by default:

* `vendor`
* `customer`
* `employee`
* `self`\
  \


> [!NOTE]
>
> **Handy Tips**\
> Additional classifications can be created from the Dashboard if required.

`Payout Purpose` *mandatory*
: `string` The purpose of the payout that is being created. The following classifications are available in the system by default:

* `refund`
* `cashback`
* `payout`
* `salary`
* `utility bill`
* `vendor bill`\
  \


> [!NOTE]
>
> **Handy Tips**
>
> * Additional purposes for payouts can be created from the Dashboard if required.
> * This field is case-sensitive.

`Payout Description` *mandatory*
: `string` The description for the Payout Link you have created. This appears on the Payout Link hosted page.

`Reference ID` *optional*
: `string` A user-generated reference given to the payout. For example, `Acme Transaction ID 12345`. You can use this field to store your own transaction id, if any.

`Internal notes: Title` *optional*
: `string` You can enter custom notes for your reference. Enter the note title in this column. Notes are not visible to the contact. For example, `Refund 08 Feb 2021`.

`Internal notes: Description` *optional*
: `string` You can enter custom notes for your reference. Enter the note description in this column. Description is not visible to the contact. For example, `Evening Batch`.

`Expiry Date` *optional*
: `string` After you [enable expiry](https://razorpay.com/docs/x/payout-links/set-expiry.md#enable-expiry), you can set the expiry date for the payout link. For example, `22/07/2021`.

`Expiry Time` *optional*
: `string` After you [enable expiry](https://razorpay.com/docs/x/payout-links/set-expiry.md#enable-expiry), you can enter the expiry time for the payout link. Input should be in the 24-hour format. For example, `14:52`.

## Process Bulk Payout Links

To upload and process a bulk file using the RazorpayX Dashboard:

1. Log in to your [RazorpayX Dashboard](https://x.razorpay.com/).
2. Navigate to **Payout Links** → **Bulk Payout Links** → **+ BULK PAYOUT LINK**.

   ![Navigating to uploading bulk Payout Links file on the X Dashboard.](https://razorpay.com/docs/build/browser/assets/images/RZPX-upload-payoutlink-bulkfile.jpg)
3. Download or upload the file.
   * You can download the [.csv file sample template](#sample-template) from the Dashboard.
   * Or if your template is ready, use **Click to Upload** and upload the file.
4. Click **NEXT**.
5. Select the account from which you want to process the amount. This can either be your:
   * RazorpayX Lite
   * RazorpayX powered Current Account

> [!WARNING]
>
> **Watch Out!**
>
> RazorpayX Lite is currently not available for new merchants. To set up a new RazorpayX account, refer to [Current Account](https://razorpay.com/docs/x/account-types/current-account.md).

1. Enter the OTP sent to your registered mobile number/email address.
2. Click **CREATE PAYOUT LINK**.

> [!NOTE]
>
> **Handy Tips**
>
> You can also [set expiry on Payout Links](https://razorpay.com/docs/x/payout-links/set-expiry.md).

## Bulk Upload Status

After you upload the Payout Links Bulk Upload file, it moves through the following statuses:

> [!WARNING]
>
> **Watch Out!**
>
> The processed state means the bulk file was fully processed. To check the status of the individual Payout Links, download the [Bulk Payout Links Report](https://razorpay.com/docs/x/payout-links/report-and-errors.md).

![Bulk Payout Links Statuses](https://razorpay.com/docs/build/browser/assets/images/RZPX-bulk-upload.jpg)

* `created`: \

  This is the initial status of the bulk upload and indicates that the bulk upload was created in the RazorpayX database and is ready to be processed. No processing is done at this point.
* `processed`: \

  This is the final status of a bulk upload where the uploaded details are processed.

## Bulk Payout Link Statuses

A Payout Link created using the bulk upload feature can have the following statuses during its life cycle:

* `issued`
* `processing`
* `processed`
* `cancelled`
* `expired`

![Payout Links States and Life Cycle](https://razorpay.com/docs/build/browser/assets/images/RZPX-payout_links_states.jpg)

Know more about [Payout Links Statuses](https://razorpay.com/docs/x/payout-links/life-cycle.md) and [Payout Statuses](https://razorpay.com/docs/x/payouts/states-life-cycle.md#payout-states).

### Related Information

* [About Payout Links](https://razorpay.com/docs/x/payout-links)
* [Set Expiry for Payout Links](https://razorpay.com/docs/x/payout-links/set-expiry.md)
* [Shopify Payout Links](https://razorpay.com/docs/x/payout-links/shopify.md)
