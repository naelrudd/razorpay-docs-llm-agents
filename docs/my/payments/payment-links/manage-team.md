> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Manage Team

> Mange your team, add or remove users and provide appropriate role to control access for Payment Links.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

You can manage your team of users who can access the Dashboard. You can provide specific access to a user or a set of users for Payment Links.

**Example** \

You need someone in your organisation to perform day-to-day operations such as creating a Payment Link or a webhook. In this case, you can give access of your Dashboard to a person and assign the **Operations** role. This limits the access to actions related to refunds and settlements only.

## Standard User Roles

Following are the predefined user roles that you can assign to your team members:

> [card] [Owner](https://razorpay.com/docs/my/payments/payment-links/manage-team.md#owner)
>
> The Owner can perform all the actions.

> [card] [Admin](https://razorpay.com/docs/my/payments/payment-links/manage-team.md#admin)
>
> The Admin can perform all the actions.

> [card] [Manager](https://razorpay.com/docs/my/payments/payment-links/manage-team.md#manager)
>
> Check all the actions that a Manager can perform.

> [card] [Operations](https://razorpay.com/docs/my/payments/payment-links/manage-team.md#operations)
>
> Check all the actions that a team member with Operations role can/cannot perform.

> [card] [Finance](https://razorpay.com/docs/my/payments/payment-links/manage-team.md#finance)
>
> Check all the actions that a team member with Finance role can/cannot perform.

> [card] [ePOS](https://razorpay.com/docs/my/payments/payment-links/manage-team.md#epos)
>
> Check all the actions that a a team member with ePOS role can/cannot perform.

> [card] [Support](https://razorpay.com/docs/my/payments/payment-links/manage-team.md#support)
>
> Check all the actions that a team member with Support role can/cannot perform.

> [!NOTE]
>
> **Handy Tips**
>
> * Assign a role to your team member.
> * Each role is tied to an email address.
> * Assign multiple roles to a team member using multiple email addresses.
> * Limit a user's access to the Dashboard using these roles.

### Owner

| Actions Allowed |
| - |
| ✔ Generate API Keys |
| ✔ Create and manage webhooks |
| ✔ View all transactions |
| ✔ Capture transactions |
| ✔ Create and manage Payment Links |
| ✔ Create and upload batch files |
| ✔ Download and email reports |
| ✔ Add Funds/Balance |
| ✔ Install OAuth Apps |

### Admin

| Actions Allowed |
| - |
| ✔ Generate API Keys |
| ✔ Create and manage webhooks |
| ✔ View all transactions |
| ✔ Capture transactions |
| ✔ Create and manage Payment Links |
| ✔ Create and upload batch files |
| ✔ Download and email reports |

### Manager

| Actions Allowed/Not Allowed |
| - |
| ✔ Create and manage webhooks |
| ✔ View all transactions |
| ✔ Capture transactions |
| ✔ Create and manage Payment Links |
| ✔ Create and upload batch files |
| ✔ Download and email reports |
| ✖ Generate API Keys |

### Operations

| Actions Allowed/Not Allowed |
| - |
| ✔ Create and manage webhooks |
| ✔ View all transactions |
| ✔ Capture transactions |
| ✔ Create and manage Payment Links |
| ✔ Create and upload batch files |
| ✔ Download and email reports |
| ✖ Generate API Keys |

### Finance

| Actions Allowed/Not Allowed |
| - |
| ✔ View all transactions |
| ✔ Create and upload batch files |
| ✔ Download and email reports |
| ✖ Generate API Keys |
| ✖ Create and manage webhooks |
| ✖ Capture transactions |
| ✖ Create and manage Payment Links |

### ePOS

| Actions Allowed/Not Allowed |
| - |
| ✔ Create Invoices and Payment Links in MYR only |
| ✖ Generate API Keys |
| ✖ Create and manage webhooks |
| ✖ Manage Teams |
| ✖ View all transactions |
| ✖ Capture transactions |
| ✖ Create and upload batch files |
| ✖ Download and email reports |
| ✖ View Payment Links created by other users |

### Support

| Actions Allowed/Not Allowed |
| - |
| ✔ View all transactions |
| ✖ Generate API Keys |
| ✖ Create and manage webhooks |
| ✖ Capture transactions |
| ✖ Create and manage Invoices, Payment Pages, Payment Links, and Customers |
| ✖ Create and upload batch files |
