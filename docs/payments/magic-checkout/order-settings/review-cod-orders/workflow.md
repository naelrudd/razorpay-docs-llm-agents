> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# COD Orders Review Workflow

> Configure workflows to automate the actions on the COD orders based on the RTO risk level using Razorpay Magic Checkout.

Available in
🇮🇳 India

Reviewing and acting upon COD orders manually can be time-consuming. With the automation feature, you can configure workflows to approve, hold or cancel COD orders based on the RTO risk levels.

> [!WARNING]
>
> **Watch Out!**
>
> You can access the **COD Orders Review Workflow** feature only if you opt for [manual review of COD orders](https://razorpay.com/docs/payments/magic-checkout/order-settings/review-cod-orders.md).

## How it Works

Follow the steps given below to configure the COD review workflow:

1. Log in to the Dashboard.
2. Navigate to **Magic Checkout** → **Orders**.
3. In the **Manual Review of COD Orders** tab, click **Automate now**. This redirects you to the **COD Review Workflow** field in the **Setup & Settings** section.

> [!NOTE]
>
> **Handy Tips**
>
> **COD Review Workflow** section appears only if you opt for the manual review of COD orders.

4. Select the **Type of RTO risk** and its corresponding action from the drop-down list.

   ![Add risk and the corresponding action](https://razorpay.com/docs/build/browser/assets/images/magic-automate-config.jpg)

> [!WARNING]
>
> **Watch Out!**
>
> * You can only assign one action to each specific **Type of RTO risk**. For example, if you identify a risk as **High** and choose the action to **Cancel the order** to handle that risk, you cannot add any additional actions for that specific type of risk.
> * However, you can use the same action, such as **Cancel the order** for multiple types of RTO risks, such as **Medium risk**.

5. Click **+ Add more conditions** to add more types of RTO risk and its corresponding action if required.
6. Click **Save settings**.

> [accordion] Edit Workflow Conditions *(Optional)*
>
> Follow the steps given below to edit the conditions:
>
> 1. Log in to the Dashboard.
>
> 2. Navigate to **Magic Checkout**.
>
> 3. Select the platform of your ecommerce website from the drop-down list and click **Next**.
>
> > [!NOTE]
> >
> > **Handy Tips**
> >
> > This feature is available for your Custom ecommerce platform, [WooCommerce website](https://razorpay.com/docs/payments/payment-pages) and [Shopify store](https://razorpay.com/docs/payments/payment-pages).
>
> 3. Click **COD Review Workflow**.
> 4. Click **Edit** to modify the conditions based on your requirement.
>
>    ![Edit automation conditions based on your requirement](https://razorpay.com/docs/build/browser/assets/images/magic-automate-edit.jpg)
> 5. Click **Save settings**.

> [accordion] Remove a Workflow
>
> Follow the steps given below to remove the review workflow conditions:
>
> 1. In the **COD Review Workflow** section, click the cancel icon.
>
>    ![Remove Automation](https://razorpay.com/docs/build/browser/assets/images/magic-remove-automation.jpg)
> 2. Click **Yes, Remove** to remove all the the COD review workflow conditions.
