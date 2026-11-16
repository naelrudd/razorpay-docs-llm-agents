> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Resgination Setup

> Set up and handle resignations on the Payroll Dashboard.

Available in
🇮🇳 India

On the Payroll Dashboard, you can dismiss employees at the end of their tenure at your organisation, or allow them to resign. After receiving a resignation request, you can process the [Full and final settlement](#process-full-&-final-settlement) and successfully dismiss the employee.

> [!NOTE]
>
> **Handy Tips**
>
> Both the administrator and the employee's manager can approve resignations.

## Enable Resignation

To allow employees to resign, you must enable it.

1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
2. Go to **Settings** → **Employee Resignation Setup** → **EDIT**.

   ![Scroll to Enable Resignation set up. Click EDIT on RazorpayX Payroll](https://razorpay.com/docs/build/browser/assets/images/payroll-enable-resignation.jpg)
3. Select the **Enable resignations feature** check box.

This enables resignation submission for employees.

## Pending Requests

After an employee submits their resignation, you can view the request and take action on it.

1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
2. Click either of the following. The Resignation reports page opens.

> [tab] Resignation Report
>
> 1. Navigate to ADMIN OPTIONS → Reports.
> 2. Click **Resignations**.
>
>    ![Resignation report in Settings on the Razorpay Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/payroll-resignation-report.jpg)

> [tab] Dashboard Reminders
>
> In the reminders tab, click **resignations**.
>
> ![Resignation reminders on the RazorpayX Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/payroll-resignations-reminders.jpg)

1. View the resignation requests pending your review. Select the employee and click **REVIEW RESIGNATION**. You can only review one request at a time.
2. In the Update Resignation Request pop-up modal, you can:
   * Change the employee's **Last Working Day**.
   * Provide **Remarks** on the resignation request.
3. Click **UPDATE** to make changes to the employee's resignation. Then, click **APPROVE**.

   ![Approve or Reject resignations on Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/payroll-resignation-modal-approve-reject.jpg)

This successfully approves the employee's resignation.

* To reject the request, click **REJECT**.
* Click View Resignation History on the right pane to view older requests.
  * You can filter the older requests using the **Resignation Status** and duration.
  * Click DOWNLOAD CSV to download the resignation data.

> [!WARNING]
>
> **Watch Out!**
>
> You cannot undo an approved resignation request.

## Process Full & Final Settlement

Once you approve the resignation request, you can process the employee's full and final settlement.

1. On the Resignations report page, select the employee to process the FnF for. Click **PROCESS FNF SETTLEMENT**. This opens the **Full and final settlement** page.
2. On the Full and final settlement page:
   1. Provide the leave encashment details. You can either enter the number of leaves to encash or the total leave encashment amount.
   2. Enter any additions or deductions to the employee's salary. You can also enter the [Loss of Pay](https://razorpay.com/docs/payroll/run-payroll.md#loss-of-pay) days, or the [Jibble Integration](https://razorpay.com/docs/payroll/integrations/jibble.md)  to sync the LOP data automatically.

      ![Payroll Dashboard make additions deductions FNF](https://razorpay.com/docs/build/browser/assets/images/payroll-fnf-additions-deductions.jpg)

> [!WARNING]
>
> **Watch Out!**
>
> Ensure you do not include loan recovery, bonus clawback, gratuity payments and other salary components or deductions here.

1. Select whether the deductions happen from the employee's gross or net pay.

> [accordion] What is the difference between Gross Pay and Net Pay?
>
> > [tab] Gross Pay
> >
> > Gross pay is the total amount an employee earns before any relevant deductions, including taxes, benefits, bonuses, reimbursements and more. This also includes the basic, ad hoc and the allowance components of an employee's salary.
> >
> > Examples of gross pay deductions include loss of pay, bonus recovery after clawback and more, depending on the employee's performance. Gross pay deductions are mandatory and affect compliance payments (TDS, PF).
>
> > [tab] Net Pay
> >
> > Net pay is the employee's take-home salary after all applicable deductions such as benefits, taxes and compliances. Net pay = Gross pay - TDS - PF - PT - ad hoc deductions.
> >
> > Examples of net pay deductions include laptop repair recovery charges, penalties, insurance payments and more.

1. Enter the employee's personal email address for further communication.

   If Payroll had been handling the employee's [Form 16s](https://razorpay.com/docs/payroll/faqs#form-16), the employee receives it on their personal email address at the end of the financial year.
2. Click **Add to Payment**.

You have successfully modified the full and final settlement for the employee. The employee receives the settlement payment after you [execute payroll](https://razorpay.com/docs/payroll/run-payroll.md#execute-payroll) for the month.

### Maintain Employee Directory

After dismissing employees, you can choose to:

* **DELETE EMPLOYEE** from the employee directory.
* **DISABLE LOGIN** for the employee during the notice period, if necessary.

The above options are available on the employee's **User Profile**.

## Reports

You can access the following reports:

| Report Name | Description |
| - | - |
| Resignation | View the resignation requests initiated and approved so far. |
| Full and final settlement | View the details of full and final settlements processed month-wise. You can refresh the data and download it in a CSV file. |

### Related Information

* [Dismiss Employees on the Payroll Dashboard](https://razorpay.com/docs/payroll/run-payroll.md#terminate-and-run-last-payroll)
* [About Full and Final Settlement](https://razorpay.com/payroll/learn/full-and-final-settlement-fnf/)
