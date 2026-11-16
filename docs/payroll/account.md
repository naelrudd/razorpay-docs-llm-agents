> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Account Setup

> Checklist to set up the RazorpayX Payroll Dashboard for your organisation.

Available in
🇮🇳 India

After you sign up with [Payroll](https://payroll.razorpay.com/login), you can begin to set up your account and Dashboard.

## Set Up Payroll Account

The following guide provides a checklist of prerequisite steps and best practices to set up your organisation's payroll account and system.

> [!WARNING]
>
> **Watch Out!**
>
> Automated Professional Tax (PT) payments for employees in Karnataka are temporarily unavailable on Payroll. Know more about the [PT rule change](https://razorpay.com/docs/payroll/faqs#professional-tax).

> [accordion] Add All Employees
>
> You can add employees individually or in bulk on the Payroll Dashboard to set up the payroll recipients.
>
> To add employees:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Navigate to **ADMIN OPTIONS** → **People**.
> 3. Click **Add One** to add an individual employee, or **Add Multiple** to add multiple employees. You can also invite your employees using their email ids using **Invite many**.
>
>    ![Add employees on RazorpayX Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-xpayroll-add-emp.jpg)
> 4. Enter the employees' information such as joining date, authorised email id, salary information and more.
> 5. Click **CONTINUE**.
>
> You have successfully added employees/contractors to the Dashboard. Your employees can complete their [onboarding and profile set up](https://razorpay.com/docs/payroll/employees#onboarding) using the welcome mail they receive at their registered email id.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Sometimes your employees may not be added to your system due to operational discrepancies like [not receiving the welcome mail](https://razorpay.com/docs/payroll/administrator#mail-not-received). Re-trigger a welcome mail or invite them to your company and payroll system.

> [accordion] Enable Compliances
>
> Update your organisation's compliance details as applicable. We support and automate many monthly [statutory compliance](https://razorpay.com/docs/payroll/statutory-compliance) payments.
>
> To enable compliances applicable:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Navigate to **ADMIN OPTIONS** → **Company Details** in the left menu.
> 3. Click **Provident Fund / ESIC / Professional Tax / LWF** → **EDIT** and enable compliances from the respective drop-down menu as applicable.
> 4. Click **CONTINUE** to save the changes.
>
>    ![Changing compliance settings like PF and external credentials in Payroll](https://razorpay.com/docs/build/browser/assets/images/x-payroll-enable-compliances.jpg)
>
> If you want us to handle your external compliances, connect your Payroll account to your compliance portals as applicable.
>
> 1. Go to **External Credentials** in **Company Details** → **EDIT**.
> 2. Enter the user ids and passwords to authenticate your credentials.
> 3. Click **CONTINUE** to save the changes.
>
> You have successfully enabled the applicable compliances. Know more about [compliance payments and automation](https://razorpay.com/docs/payroll/statutory-compliance).

> [accordion] Upload Company Logo
>
> You can upload your company logo to reflect on both the Dashboard and the payslips. Ensure you meet the following conditions for the logo:
>
> * Must be a PNG file.
> * Must have a 5:1 aspect ratio or be rectangular shaped.
> * Must have a transparent background.
>
> To upload the logo:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Navigate to **Company Details** → **Name & Address** → **EDIT**.
> 3. Upload the photograph and click **PREVIEW**.
>
>    ![Upload Company Logo under Company Details in Payroll](https://razorpay.com/docs/build/browser/assets/images/xpayroll-upload-logo.jpg)

> [accordion] Setup Default Salary Structure
>
> To set up a default salary structure for your organisation:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Navigate to **Settings** from the left menu.
> 3. Locate the **Default Salary Structure** section and click **Edit Structure**.
> 4. On the setup page, you'll see the components that can be included in the default structure:
>    * **Basic Salary**: Usually set at 50% of CTC as per best practices.
>    * **House Rent Allowance (HRA)**: Typically 25% of basic salary.
>    * **Leave Travel Allowance (LTA)**: Usually 15% of basic salary.
>    * **Special Allowance**: Set as a residual component to balance the CTC.
>
> ![Edit Default Salary Structure](https://razorpay.com/docs/build/browser/assets/images/payroll-default-salary-structure-edit.jpg)
>
> 5. For each component, configure:
>    * **% age of CTC or Amount**: Set either a percentage of total CTC or a fixed amount.
>    * **Percentage or Fixed?**: Choose whether the component is calculated as a percentage or a fixed amount.
>    * **Taxable?**: Specify if the component is taxable (Yes, No or Partially).
> 6. Click **Save & Continue** to apply the changes.
>
> The default salary structure is now set and is applied to all new employees added to the system. To offer tax-friendly benefits such as Meal Allowance or Employer NPS Contribution on top of this structure, configure them separately in the [Flexi Component Library](https://razorpay.com/docs/payroll/component-library/flexible-benefits.md).

> [accordion] Modify Existing Default Structure
>
> If you need to update your organisation's default salary structure:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
>
> 2. Navigate to **Settings** from the left menu.
>
> 3. Locate the **Default Salary Structure** section and click **Edit Structure**.
>
> 4. Make the necessary changes to the existing components:
>    * Adjust percentages or amounts
>    * Change calculation methods (percentage vs. fixed)
>    * Update taxability status
>
> 5. To remove a component, you can set its value to 0 or completely remove it.
>
> 6. To add new components, follow the steps outlined in the "Add Custom Components" section.
>
> 7. Click **Save & Continue** to apply the changes.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Remember that changes to the default salary structure affect only new employees added after the changes are made. The salary structures of existing employees remain unchanged.
>
> The updated default structure is applied to all new employees onboarded after the changes are saved.

> [accordion] Add Custom Components
>
> You can add components to your default salary structure to better match your organisation's compensation philosophy:
>
> 1. Follow steps 1-3 above to access the Default Salary Structure setup.
> 2. Scroll to the bottom of the components list, where you'll see dropdown fields labelled **Add component**.
> 3. Click on the dropdown and select an existing component from your [Salary Component Library](https://razorpay.com/docs/payroll/component-library.md). To define a brand-new component (Earnings, Deduction, Non-Payable Benefit or Perquisite), create it in the Component Library first, then return here to add it.
> 4. For the selected component (for example, Conveyance Allowance):
>    * Set the **Amount** value or percentage.
>    * Choose **Fixed** or **Percentage** from the dropdown.
>    * Set the taxability status.
> 5. You can add multiple components by repeating steps 3-4 for each additional component.
> 6. Click **Save & Continue** to apply the changes.

> [accordion] Check for Missing Information
>
> Before you [execute payroll](https://razorpay.com/docs/payroll/execute-payroll.md), ensure you your employees' data is available and up-to-date.
>
> To check for missing information:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Go to **ADMIN OPTIONS** → **Reports** → **Missing Information**. This opens the **Missing Information** page with a list of employees and their missing information.
> 3. Select the checkboxes against the employees' names and click **SEND EMAILS**. You can also select all employees using the checkbox against **Employee Name**.
> 4. Click **SEND EMAILS** to re-confirm.
>
> Your employee/s receive an email at their registered email address to update their missing information.
>
> ![Missing Information settings in Payroll](https://razorpay.com/docs/build/browser/assets/images/xpayroll-missing-info.jpg)

> [accordion] Confirm Salary Components
>
> You should re-check the salary components and net salary calculations.
>
> To re-check salary information:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard)
> 2. Navigate to **ADMIN OPTIONS** → **Reports**.
> 3. Select **Salary Register** and select the relevant month. You can filter the information, download the payslips for that month and download the data as a .CSV file to process the data better.
>
> ![Salary Register in Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/xpayroll-check-salary-register.jpg)

> [accordion] Employee Tax Declarations
>
> You must ask your employees to update their tax deductions and declarations on the [Employee Dashboard](https://razorpay.com/docs/payroll/employees/declarations.md).
>
> Employees must navigate to **Tax Deductions** on their Dashboard to update their tax details and minimise their deductible taxes.

> [accordion] Add RazorpayX Payroll as Beneficiary
>
> To enable fund transfers, you need to add your Payroll Account as a beneficiary. You can find your account details in the Payroll [Money Transfer page](https://payroll.razorpay.com/moneyTransfer).

> [accordion] Update UAN
>
> Update your employees' Universal Account Number (UAN) if applicable.
>
> To update UAN:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Navigate to **ADMIN OPTIONS** → **People**.
> 3. Select the employee From the list of employees and open their profile.
> 4. Update their PF details in **Provident Fund** → **Professional Tax & ESI**.

> [accordion] Enable Resignation
>
> You can enable employee resignations and allow employees to submit resignation requests.
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
> 2. Go to **Settings** → **Employee Resignation Setup** → **EDIT**.
> 3. Select the **Enable resignations feature** check box.

With all of the above done, your account is completely set up to process payroll.

### Related Information

* [Execute Payroll](https://razorpay.com/docs/payroll/execute-payroll.md)
* [Statutory Compliance](https://razorpay.com/docs/payroll/statutory-compliance)
* [Administrative Role](https://razorpay.com/docs/payroll/administrator)
* [Salary](https://razorpay.com/docs/payroll/salary)
