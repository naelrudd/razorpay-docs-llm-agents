> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About Razorpay n8n Community Node

> Set up and use the Razorpay n8n Community Node to integrate Razorpay payment APIs with your n8n workflows for automated payment processing.

Available in
🇮🇳 India

> [card] [Razorpay n8n Node Repository](https://github.com/razorpay/n8n-nodes-razorpay)
>
> View source code, report issues, and contribute to the Razorpay n8n Community Node.

> [card] [Razorpay n8n Node NPM Package](https://www.npmjs.com/package/@razorpay/n8n-nodes-razorpay)
>
> Official npm package for the Razorpay n8n Community Node.

The [Razorpay n8n Community Node](https://www.npmjs.com/package/@razorpay/n8n-nodes-razorpay) provides seamless integration between Razorpay payment APIs and [n8n workflow automation platform](https://n8n.io/). This node enables developers, operations teams, and business owners to automate payment operations, process transactions, manage refunds, and build sophisticated payment workflows without writing code.

## Features

1. **No-Code Automation** \

   Build complex payment workflows visually with drag-and-drop interface.

2. **400+ App Integrations** \

   Connect Razorpay with Google Sheets, Slack, WhatsApp, Gmail, Shopify and 400+ other services instantly.

3. **Test & Live Modes** \

   Develop and test workflows safely with test mode API keys before deploying to production.

4. **Real-Time Processing** \

   Process payments, refunds and settlements with minimal latency using efficient API operations.

5. **Flexible Data Handling** \

   Transform, filter and enrich payment data using built-in n8n nodes and custom functions.

6. **Secure & Compliant** \

   Enterprise-grade security with encrypted credential storage and PCI DSS-compliant operations.

## Available Operations

The Razorpay n8n Node provides comprehensive access to Razorpay APIs through **10 core operations**:

| Category | Operations | Key Use Cases |
| - | - | - |
| **Orders** | Fetch All | Order management, payment tracking |
| **Payment Links** | Create, Fetch | Instant payment collection, WhatsApp automation |
| **Payments** | Fetch, Fetch All | Payment verification, reconciliation |
| **Refunds** | Fetch All | Fetch refund information |
| **Settlements** | Fetch, Fetch All | Daily settlement sync, accounting |
| **Invoices** | Fetch Invoices for for Subscription | Subscription billing automation |
| **Disputes** | Fetch All | Dispute monitoring and alerts |

View [Complete Operations Reference](https://razorpay.com/docs/razorpay-n8n-node/operations-reference.md).

> [!NOTE]
>
> **Extended Operations Available**
>
> Access **28 additional operations** via [Razorpay MCP Server](https://razorpay.com/docs/mcp-server) integration.

## Use Cases

Explore real-world automation scenarios:

* **WhatsApp Booking Automation**: Chat-to-order-to-payment workflow.
* **Daily Settlement Reconciliation**: Automated sync to Google Sheets.
* **High-Value Payment Alerts**: Real-time Slack notifications.
* **Refund Processing**: Automated refund creation based on rules.
* **Customer Payment Lookup**: Internal tool for support teams.

View [Use Cases](https://razorpay.com/docs/razorpay-n8n-node/use-cases.md).

## Prerequisites

Ensure you have the following before starting:

> [accordion] n8n Platform
>
> * **n8n Version**: v1.104.2 or higher (minimum required).
> * **Deployment**: n8n Cloud or self-hosted instance.
> * **Admin Access**: Permission to install community nodes.

> [accordion] For Self-Hosted n8n
>
> * **Node.js**: Version 14.x or higher.
> * **npm**: Version 6.x or higher.
> * **Network Access**: HTTPS access to `api.razorpay.com`.

> [accordion] Razorpay Account
>
> * **Active Account**: Sign up at [razorpay.com](https://razorpay.com).
>
> * **KYC Completed**: Required for live mode (not needed for test mode).
>
> * **API Keys**: Generate [API keys](https://razorpay.com/docs/payments/dashboard/account-settings/api-keys.md) from the Razorpay Dashboard.
>
> > [!NOTE]
> >
> > **Start with Test Mode**
> >
> > Use test mode API keys (`rzp_test_*`) for development and testing. No real money transactions, no KYC required. Switch to live mode (`rzp_live_*`) after thorough testing.

## Next Steps

1. **[Install the Node](https://razorpay.com/docs/razorpay-n8n-node/installation.md)**: Add Razorpay node to your n8n instance.
2. **Configure Credentials**: Generate and add your API keys.
3. **[Explore Use Cases](https://razorpay.com/docs/razorpay-n8n-node/use-cases.md)**: Learn from real-world examples.
4. **Build Your Workflow**: Start with a simple automation.
5. **[Troubleshoot Issues](https://razorpay.com/docs/razorpay-n8n-node/troubleshooting-faqs.md)**: Resolve common problems.

### Related Documentation

* [Razorpay API Reference](https://razorpay.com/docs/api)
* [Webhook Integration Guide](https://razorpay.com/docs/webhooks)
* [Test Card Details](https://razorpay.com/docs/payments/payments/test-card-details.md)
* [MCP Server Documentation](https://razorpay.com/docs/mcp-server)
* [n8n Documentation](https://docs.n8n.io/)
