# 1. Build Integration

Follow the steps given below to integrate Razorpay Payment Gateway with your OpenCart enabled site using the Razorpay Subscription for OpenCart plugin.

## Integration Steps

Follow these steps to complete the integration:

### On Your OpenCart Site
1. [Install the Razorpay Subscriptions for OpenCart Plugin](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/plugins/opencart/build-integration.md#step-1-install-razorpay-subscriptions-for-opencart-plugin).
1. [Configure OpenCart Settings](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/plugins/opencart/build-integration.md#step-2-configure-opencart-settings).
1. [Create a Plan for Subscriptions product](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/plugins/opencart/build-integration.md#step-3-create-a-plan-for-subscriptions-product).
1. [Test integration](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/plugins/opencart/test-integration.md).

### On Razorpay Dashboard

1. [Enable Webhooks](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/plugins/opencart/build-integration.md#subscribe-to-webhook-events).

#### Step 1: Install Razorpay Subscriptions for OpenCart Plugin

To install Razorpay Subscriptions for OpenCart plugin:
1. Download the latest source code ZIP file of the Razorpay OpenCart Subscriptions plugin from the repository on Github.
    1. [OpenCart 3](https://github.com/razorpay/razorpay-opencart/releases)
    2. [OpenCart 2](https://github.com/razorpay/razorpay-opencart/releases/tag/opencart2-3.0.0)
    3. [OpenCart 1.5](https://github.com/razorpay/razorpay-opencart/releases/tag/opencart1.5-1.0.0)

    
**WARN**

**Watch Out!**

Subscriptions is available only on [OpenCart 3](https://github.com/razorpay/razorpay-opencart/releases).

2. Copy all files/folders recursively to the OpenCart installation directory.

#### Step 2: Configure OpenCart Settings

1. Log in to  [OpenCart](https://www.opencart.com/).
2. Go to the **Admin Panel** → **Extensions** → **Payments** to install the Razorpay Payment Gateway extension.

    
3. Click the edit icon and fill in the following field details.

    
    Field | Description
    ---
    Key ID | Enter the Key ID generated from the Dashboard.
    ---
    Key Secret | Enter the API Key Secret generated from the Dashboard.
    ---
    Payment Action | To automatically capture successful payments, select `Authorize and Capture` option in the drop-down menu. Select `Authorize` if you want to capture payments manually from the [Razorpay Dashboard](https://razorpay.com/docs/build/llm-docs/payments/payments/dashboard.md#manual-capture-of-payments) or using [API](https://razorpay.com/docs/build/llm-docs/api/payments.md#capture-a-payment).
    ---
    Subscription Status | Ensure the Subscription Status is enabled.
    ---
    

    
**INFO**

**Handy Tips**

Webhook is auto-configured when you enter and save the API key ID and secret on the plugin settings page. You need to verify if webhooks are enabled on your Razorpay Dashboard.

    
4. Click **Save** to save the extension settings.
5. Go to **Admin Panel** → **Extensions** → **Modifications** and click the refresh button to rebuild your modification cache.

#### Step 3: Create a Plan for Subscriptions Product

**WARN**

**Watch Out!**

You can enable or disable plans only after creating them.

To create a Plan for Subscriptions product:
1. Go to the **Admin Panel** → **Razorpay Subscription**  → **Plans** to add a new Plan.
2. Click **Add new** to create a new Plan.
3. Enter the required details and click **Save** to save the Plan.

    

### Next Steps

[Step 2: Test Integration](https://razorpay.com/docs/build/llm-docs/payments/subscriptions/plugins/opencart/test-integration.md)
