> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Tax Payment Life Cycle

> Check the states of a tax payment and their significance.

Available in
🇮🇳 India

Following are the 2 life cycles in tax payments:

* [Tax Payment Life Cycle](https://razorpay.com/docs/x/tax-payments/life-cycle.md)
* [Payout Life Cycle](https://razorpay.com/docs/x/payouts/states-life-cycle.md)

Following is the tax payment life cycle.

![tax payment life cycle](https://razorpay.com/docs/build/browser/assets/images/RZPX-tax-payments-tax-payments-life-cycle.jpg)

## Unpaid

The TDS payment is uploaded to our system. A payout may have been created, but not successfully made against the TDS payment.

Possible payout states:

* Payout not yet created.
* `rejected`
* `cancelled`
* `failed`
* `reversed`

## Processing

The TDS payment is being processed. A payout is created and is being processed.

Possible payout states:

* `pending`
* `queued`
* `processing`

From the `processing` states, the payout can go back to the `unpaid` state if:

* If you cancel or reject the payout.
* If the payout fails or is reversed.

## Paid

The TDS payment was successful. Possible payout state: `processed`.

After the TDS is successfully paid, you can download the challan from the Dashboard and file the TDS as per your convenience.

## Cancelled

You have manually cancelled the TDS payment from the Dashboard.

* You can only cancel a TDS payment in the `unpaid` state.
* You cannot cancel a TDS payment after a payout is initiated for it.

### Related Information

* [Tax Payments](https://razorpay.com/docs/x/tax-payments)
* [Tax Payments - Standard User Roles](https://razorpay.com/docs/x/tax-payments#manage-teams)
* [Payout Life Cycle](https://razorpay.com/docs/x/payouts/states-life-cycle.md)
