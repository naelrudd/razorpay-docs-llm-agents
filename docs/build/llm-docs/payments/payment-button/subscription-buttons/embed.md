# Create and Embed Subscription Button

You can create a Subscription Button via Dashboard and embed it on your website to accept payments from customers. This is useful in cases where you want to provide subscription plans.

**Example** 

Suppose you are an Internet Service Provider who wants to provide subscription plans to your customers. You can use the Subscription Button on your site to accept payments based on subscription plans.

## Prerequisites

- Sign up for a Razorpay account.
- Log in to the Dashboard.
- The Dashboard has [test and live modes](https://razorpay.com/docs/build/llm-docs/payments/dashboard/test-live-modes.md). Subscription Buttons created in the test mode do not appear in the live environment. **You must create a new Subscription Button in live mode**.

## Create a Subscription Button

1. Log in to the Dashboard and navigate to **Payment Button**.

2. Click **Subscription Buttons** tab, and then click **+ Create Subscription Button**.
     
3. Follow these steps to create the button:

    
### Button Details

         In **Button Details**, enter the relevant information:
         1. **Title**: Provide a name for the button. This name is for your internal reference and will appear on the Dashboard. It **will not be visible** to your customers. For example, **Acme Inc**.
         2. **Button Label**: Text on button to be displayed to customers. Please enter alphanumeric characters only. The maximum character limit is 20. For example, your button label can be **Subscribe Now**.
         3. **Button Theme**: You can choose between the following themes:
                - Razorpay Dark
                - Razorpay Light
                - Razorpay Outline
                - Brand Color (This is the color configured by you on the Dashboard)
         4. Click **Next**.
             
        
 
    
### Recurring Payments

         In the **Recurring Plans**, add Plans and No. of Billing Cycles.

         1. Click **+ Add Plan Item**.
         1. To create a new plan, click **Add New Plan**.
         1. Enter the following details:
                - Plan Name
                - Plan Description
                - Billing Frequency: The time interval at which you want to charge your customer. For example, once in a week.
                - Billing Amount: The amount you want to charge for every payment.
                - Internal Notes.
         1. Click **Create Plan**.
                
         1. Select a Plan from the list, add **No. of Billing Cycles** and click **Save**.
                
**INFO**

**Handy Tips**

You can add a maximum of 5 Plans.

                

         1. Click **+ Add Plan Item** to add more plans.
         1. Click **Next**.
            

        

    
### One-Time Payments

         This is an optional step. If you want to provide one time payment option, follow these steps:
         1. Click the slide-bar.
         1. Enter the name of label in the **Label** text box.
         1. Enter the one time payment amount in the **Value** text box.
         1. Add a description.
         1. Click **+ Add One-time Item** to add more options.
         1. Click **Next**.
             
        

    
### Customer Details

         In the **Customer Details**, configure the information that must be entered by the customer while making the payment. By default, `Email` and `Phone` must be entered. However, you can edit the labels of these fields.

         
         Additionally, if you want to collect more information from the customer, you can add more custom fields:
         1. Click **+ Add Another Input Field**.
         2. Enter the following details in the modal:
             1. Select the relevant field type. For example, if you want the customer to enter their name, select **Single Line Text**.
             1. Enter the label for the custom field.  For example, `Name`.
             2. If required, click more and add a description for the field.
             3. Select **Optional Field**.
             4. Click **Save**.
                 
         3. To proceed, click **Next**.
        

    
### Review and Create

         1. Review the details entered in the previous sections.
         1. Click **Back** to navigate to the previous steps for any changes.
         1. Click **Create Button**.
            
         1. A button is created successfully. Copy the HTML Code and embed it in your webpage. Once this is done, the Subscription button will appear on your website.

            
        

## Test Payment Buttons

You can test the Payment Button by [adding the code to this page](https://cdn.razorpay.com/static/widget/test-payment-button.html).

## Embed Subscription Button Code in Website

Copy the HTML Code and embed it in your webpage or one built on platforms such as WordPress, Wix or Google Sites. Once this is done, the Subscription button will appear on your website.

Customers can click this button to:
1. Open Razorpay Checkout.
2. Select the Recurring Plan.
3. Add their name and address.
4. Complete the payment.

### Customer Interaction

    
### Subscribe a Plan

         The short animation below shows you how to subscribe a plan.

         
        

    
### One-time Payment

         The short animation below shows you how to make a one time payment.
         
         
**INFO**

**Handy Tips**

One-Time payment option is shown only if you enabled **Add one-time payment options** while creating the payment button.

        

## View Subscription Details

You can [View Subscriptions and One-time Payments](https://razorpay.com/docs/build/llm-docs/payments/payment-button/subscription-buttons/download-reports.md). To download reports, refer to the [Download Report](https://razorpay.com/docs/build/llm-docs/payments/payment-button/subscription-buttons/download-reports.md) section.

### Settlement

You will receive the payments in your bank account as per the settlement cycle agreed upon at the time of Razorpay account setup. Usually, this is T+2 days. In case of international payments, the settlement cycle is T+7 days.

### Related Information

- [Manage Subscription Buttons](https://razorpay.com/docs/build/llm-docs/payments/payment-button/subscription-buttons/manage.md)
- [View Notifications using Webhooks](https://razorpay.com/docs/build/llm-docs/payments/payment-button/subscription-buttons/subscribe-to-webhooks.md)
- [Subscription Button FAQs](https://razorpay.com/docs/build/llm-docs/payments/payment-button/subscription-buttons/faqs.md)
