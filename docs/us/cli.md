> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# About CLI

> Learn about the Razorpay CLI, a command-line tool to interact with Razorpay APIs directly from your terminal.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Razorpay CLI is a command-line tool that lets you interact with Razorpay APIs directly from your terminal. Instead of writing code or using the Dashboard, you can manage resources, test integrations and automate workflows with simple commands.

## What You Can Do with the CLI

* **Create and manage resources**: Create orders, fetch payments, issue refunds and more using straightforward commands.
* **Test your integration**: Quickly make API calls in Test Mode to validate your integration without writing additional code.
* **Debug faster**: Inspect API responses directly in your terminal to troubleshoot issues.

## How It Works

The CLI wraps Razorpay's REST APIs into terminal commands. After installing and configuring it with your API credentials, you can run commands like:

```bash Bash theme={null}
razorpay orders create --amount 50000 --currency INR
```

This is equivalent to making a `POST /v1/orders` API call with the specified parameters.

## Prerequisites

Before you start, ensure you have:

* A [Razorpay account](https://dashboard.razorpay.com/signup).
* API keys generated from the [Razorpay Dashboard](https://dashboard.razorpay.com/app/keys).

## Supported APIs

The Razorpay CLI provides access to the following APIs:

* **Orders**: Create and manage orders
* **Payments**: Fetch and manage payment transactions
* **Downtime**: Check payment downtime status
* **Settlement**: Access settlement data
* **Instant Settlement**: Manage on-demand instant settlements
* **Refunds**: Process and track refunds
* **Disputes**: View and manage payment disputes
* **Documents**: Upload and manage documents
* **Customers**: Create and manage customers
* **Payment Links**: Generate and share Payment Links
* **QR Code**: Create and manage QR code payments
* **Invoices**: Create and manage invoices
* **Subscriptions**: Manage subscription plans and billing
* **Route**: Manage transfers and linked accounts
* **Smart Collect**: Create and manage virtual accounts

## Supported Platforms

The CLI is available for the following operating systems:

| Platform | Architectures |
| - | - |
| macOS | Apple Silicon, Intel |
| Linux | x86-64, ARM64 |
| Windows | x86-64, x86 (32-bit) |

## Next Steps

> [card] [Install the Razorpay CLI](https://razorpay.com/docs/us/cli/install-cli.md)
>
> Download, install and configure the CLI on macOS, Linux or Windows.
