> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create Approval Workflow

> Check how to set up and operate approval workflows for RazorpayX Payroll.

Available in
🇮🇳 India

You can set up Approval Workflows for processes on the [Payroll Dashboard](https://payroll.razorpay.com/dashboard) to ensure compliance, security and accuracy in critical decision-making.

> [accordion] Advantages of Approval Workflows
>
> With approval workflows, you can:
>
> * Segregate duties, enforce smoother collaboration and manage teams better.
> * Promote autonomy, accountability and efficiency.
> * Mitigate risks associated with critical business decisions.
> * Ensure compliance and transparency.
> * Audit financial transactions and ownership to reduce fraud and conflicts of interest.

> [accordion] Approval Workflow Use Cases
>
> Approval Workflow enables multiple teams to collaborate smoothly with the allowed permissions. It is useful in the following ways:
>
> * Approvers can check critical information changes such as updating bank details, salary revision, bonuses, contractor payments and more.
> * Administrator/s can assign roles and ensure there are approvers to review and audit the request when another user is unavailable in the organisation.
> * Approvers can verify the payouts made to employees and contractors.

## How it Works

1. Set up [user roles](https://razorpay.com/docs/payroll/user-roles-workflows.md) in Payroll.
2. Create and save approval workflows and assign one or two levels of approvers on the Dashboard.
3. Your team/[collaborators](https://razorpay.com/docs/payroll/user-roles-workflows.md#view-collaborators)/user roles make a request and send it for the approvers' review.
4. The approvers receive and approve/reject the request from the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).

## Available Workflows

You can create approval workflows for the following Payroll actions:

* [Edit Payroll](https://razorpay.com/docs/payroll/run-payroll.md#additions-and-deductions)
* [Finalise Payroll](https://razorpay.com/docs/payroll/run-payroll.md#execute-payroll)
* [Salary Revision](https://razorpay.com/docs/payroll/run-payroll.md#revise-salary)

Know more about the [Approver Checklist](https://razorpay.com/docs/payroll/approval-workflow/checklist.md).

> [!WARNING]
>
> **Watch Out!**
>
> You must set up [user roles](https://razorpay.com/docs/payroll/user-roles-workflows.md) before creating approval workflows. Go to **Settings** → **User Roles & Workflows** → **User Roles** → **EDIT** on the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).

## Set Up Workflow

To set up the workflow:

1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard) as the admin.
2. Navigate to **Settings** → **User Roles & Workflows** → **Workflows** → **EDIT**.
3. On the **Workflows** page, choose a Payroll process from the left menu to set up an approval workflow.

   ![Approval Workflow Set Up on the Razorpay Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/payroll-approval-workflow-setup.jpg)

## Create Workflow

To create an Approval Workflow:

1. Navigate to the **Workflows** page as shown in [set up](#set-up-workflow).
2. Select the Payroll action from the left menu.
3. Click **Set-up workflow**. For example, **Edit Payroll**.
4. On the **Workflows** page:
   1. Enter the names of all the users you want to assign as approvers in the text box. For example, two finance role users, Gauri Kumari and Gaurav Kumar.

      ![Add Approvers on Payroll Dashboard for Approval Workflow](https://razorpay.com/docs/build/browser/assets/images/payroll-approval-workflow-add-approvers.jpg)

      Ensure the users have the appropriate permissions to approve/reject as defined in the [user roles](https://razorpay.com/docs/payroll/user-roles-workflows.md).

   2. Select the minimum number of approvals required at this level from the drop-down list.

> [!NOTE]
>
> **Handy Tips**
>
> If you assign five approvers and choose the minimum number of approvals required as two, then any two of the five approvers can approve the request.

1. Click **Done**. You can add a second level of approvers if required.

> [accordion] To add Second Level Approvers:
>
> For some payroll actions like providing loans or salary advances, you need approvals from a senior level or cross-functional managers. In such cases, you can add another level of approvers to review the request on the [Payroll Dashboard](https://payroll.razorpay.com/dashboard).
>
> To add a second level of approvers:
>
> 1. Click **+ Add Level 2 Approvers**.
>
>    ![Add Approvers on Payroll Dashboard for Approval Workflow](https://razorpay.com/docs/build/browser/assets/images/payroll-approval-workflow-add-approvers.jpg)
> 2. Enter the names of user roles in the text box. Ensure the approvers have user roles assigned to them.
> 3. Select the minimum number of approvals required from the drop-down list.
> 4. Click **Done**.
>
> You have successfully added a second level of approvers.

1. Click **End Workflow & Save**.

   ![Payroll end Approval Workflow process](https://razorpay.com/docs/build/browser/assets/images/payroll-approval-workflow-add-approvers.jpg)

You have successfully set up an Approval Workflow.

## Manage Workflows

You can manage the approval workflows in the following ways:

> [accordion] Edit Workflow
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Editing the workflow rejects the pending requests previously created using the workflow. After saving the changes, you must [create the requests](#create-a-request) again.
>
> To edit an approval workflow:
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard) as the admin.
> 2. Navigate to [Workflow settings](#set-up-workflow).
> 3. Select the Payroll action from the left menu.
> 4. Click **Edit Workflow** on the **Workflows** page.
>
>    ![Edit Approval Workflow on the Razorpay Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-xpayroll-approval-workflow-edit.jpg)
> 5. Click **Edit** against the level of approvers and make the relevant changes.
> 6. Click **End Workflow & Save**.
>
> You have successfully edited and saved the workflow.

> [accordion] Copy Workflow
>
> You can copy an existing workflow if the new workflow matches the conditions of an older workflow.
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard) as the admin.
> 2. Navigate to [Workflow settings](#set-up-workflow).
> 3. Select the Payroll action from the left menu.
> 4. When creating the workflow, click **Copy existing workflow**.
>
>    ![Approval Workflow Set Up on the Razorpay Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/payroll-approval-workflow-copy.jpg)
> 5. Select an existing workflow from the drop-down list.
> 6. Review the workflow and click **End Workflow & Save**.
>
> You have successfully copied and saved the workflow.

> [accordion] Delete Workflow
>
> You can delete the workflow if you no longer need an approval workflow for any Payroll action. If there are pending items that require approval, the workflow rejects those requests, post which the workflow gets deleted.
>
> 1. Log in to the [Payroll Dashboard](https://payroll.razorpay.com/dashboard) as the admin.
> 2. Navigate to [Workflow settings](#set-up-workflow).
> 3. Select the Payroll action from the left menu.
> 4. Click **Delete** → **Yes, reject and delete**.
>
>    ![Delete Workflow modal on the Razorpay Payroll Dashboard](https://razorpay.com/docs/build/browser/assets/images/x-xpayroll-approval-workflow-delete.jpg)
>
> You have successfully deleted the workflow.

## Create a Request

After setting up an Approval Workflow, any member of the organisation can create requests on the Dashboard as necessary.

* Requests are successfully created only when there are no errors.
* You cannot edit requests after sending them for approval.

When a maker performs any action requiring approval on the Payroll Dashboard, the assigned approvers receive the notification via email and the Dashboard. Approvers can then view the request on the [Approvals Dashboard](https://razorpay.com/docs/payroll/approval-workflow/approvers.md).

## Related Information

* [Approvals Checklist](https://razorpay.com/docs/payroll/approval-workflow/checklist.md)
* [Approvals Dashboard](https://razorpay.com/docs/payroll/approval-workflow/approvers.md)
* [User Roles and Workflows](https://razorpay.com/docs/payroll/user-roles-workflows.md)
* [Salary Actions in Payroll](https://razorpay.com/docs/payroll/salary)
