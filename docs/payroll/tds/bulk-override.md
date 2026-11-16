> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# RazorpayX Payroll Bulk TDS Override

> Learn how to override the TDS amount for unfinalised payroll for multiple employees for a specific payroll month using RazorpayX Payroll's bulk TDS override feature.

Available in
🇮🇳 India

The Bulk TDS Override feature in RazorpayX Payroll enables you to override the TDS (Tax Deducted at Source) amount for multiple employees for a specific payroll month at once. Instead of overriding the TDS for each employee individually, you upload a single template and apply the overrides for your entire workforce in one operation, saving time and ensuring consistency. Bulk TDS Override is allowed only for unfinalised payroll. It is not allowed for finalised or executed payroll.

> [!NOTE]
>
> **Handy Tips**
>
> Bulk TDS Override is available for organisations on Payroll Engine 2.0 and needs to be enabled for your organisation. [Contact Payroll Support](mailto:xpayroll@razorpay.com) for assistance.

## Use Cases

Bulk TDS override is beneficial when you want to set a specific TDS amount for a group of employees for a payroll month, such as:

* Adjusting the TDS to account for tax computed outside the system or for prior employment income.
* Correcting the TDS for a group of employees for a particular payroll month.

> [!WARNING]
>
> **Watch Out!**
>
> * The override applies only to the payroll month you select and only one override per employee per payroll month is allowed.
> * Enter the TDS amount in rupees using whole numbers only.

## Step-by-Step Bulk TDS Override Process

> [accordion] Step 1: Access the Bulk TDS Override Feature
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Navigate to the **Bulk Actions** section from the left navigation menu.
> 3. Under **Select bulk action**, select **TDS Override** from the drop-down menu.
> 4. Click **Next**.
>
>    ![Select TDS Override from the bulk action drop-down](https://razorpay.com/docs/build/browser/assets/images/bulk-tds-override-action.jpg)

> [accordion] Step 2: Download the Template
>
> In the **Bulk TDS Override** modal, on the **Upload Template** step:
>
> 1. Under **Select payroll month**, choose the payroll month for which you want to override the TDS.
> 2. Click the **Download Template** button to download the template.
> 3. Save the template to your local system.
>
>    ![Download the bulk TDS override template for the selected payroll month](https://razorpay.com/docs/build/browser/assets/images/bulk-tds-override-template.jpg)
>
>    > [!NOTE]
>    >
>    > **Handy Tips**
>    >
>    > The TDS override applies to the payroll month you select here.

> [accordion] Step 3: Fill the Template
>
> Open the downloaded template in Microsoft Excel or a compatible spreadsheet application and fill in the employee email and TDS amount in rupees as per the instructions:
>
> 1. Enter the TDS amount in rupees using whole numbers only.
> 2. Only one override per employee per payroll month is allowed.
> 3. Do not add or remove any columns.
> 4. You can upload a maximum of 500 employees per upload.
> 5. Mandatory fields are marked with a \* sign.
> 6. Save the file in .xlsx format.

> [accordion] Step 4: Upload the Template
>
> 1. Return to the **Bulk TDS Override** modal.
> 2. Under **Upload the updated sheet below**, click **Browse files to upload** and select your updated file.
> 3. Only the .xlsx file format is allowed, with a maximum size of 5MB.
> 4. Click **Upload & Preview** to proceed to the preview step.

> [accordion] Step 5: Preview and Confirm
>
> 1. On the **Preview Details** step, the system displays a preview of all the TDS overrides to be applied.
> 2. Review the employee emails and TDS amounts for any errors or discrepancies.
> 3. After carefully reviewing all entries, confirm to apply the overrides.
> 4. Upon successful processing, a confirmation message appears.
>
>    > [!NOTE]
>    >
>    > **Handy Tips**
>    >
>    > The preview stage is crucial for catching potential errors. Review all records carefully, especially when overriding TDS for a large number of employees.

After completing the bulk TDS override, you can finalise the payroll.

1. The overridden TDS amounts are applied to the payroll month you selected.
2. The overrides reflect in the selected month's payroll for each employee.

### Related Information

* [Tax Deducted at Source (TDS)](https://razorpay.com/docs/payroll/tds.md)
* [Bulk One-Time Payment](https://razorpay.com/docs/payroll/bulk-one-time-payment.md)
* [Run Payroll](https://razorpay.com/docs/payroll/run-payroll.md)
* [Statutory Compliance](https://razorpay.com/docs/payroll/statutory-compliance)
