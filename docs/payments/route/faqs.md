> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# FAQs (Frequently Asked Questions)

> Find answers to frequently asked questions about Razorpay Route.

Available in
🇮🇳 India
🇲🇾 Malaysia

## RBI Compliance Requirements for Route

> [accordion] Why is there a compliance communication about Route now?
>
> The RBI issued updated Payment Aggregator guidelines in September 2025. Razorpay's compliance and product teams needed time to design a process that makes it straightforward for you to demonstrate compliance. The information requested has been structured so you can understand what is needed and respond quickly with minimal friction.

> [accordion] What are the two eligibility criteria for using Route?
>
> The two criteria are:
>
> 1. **Minimum Financial Turnover:** Your business must have domestic turnover exceeding ₹40 Lakhs or export turnover exceeding ₹5 Lakhs in either the current (FY26) or preceding (FY25) financial year.
> 2. **Payer-Payee Transparency:** You must confirm that the linked account (third party) to which your customers' payments are routed directly interfaces with those customers to provide goods or services.

> [accordion] What documents are accepted to prove the required turnover?
>
> The accepted documents are:
>
> * **GST-3B returns** for domestic turnover. You may submit returns from multiple filing periods within a financial year. The cumulative "outward taxable supplies" value across all submitted returns must exceed ₹40 Lakhs.
> * **Bank-issued FIRC (Foreign Inward Remittance Certificate)** for export turnover. This must be a single certificate covering a date range within a financial year and must reflect INR equivalent inward remittances exceeding ₹5 Lakhs.
>
> Documents from either FY25 or FY26 are accepted.

> [accordion] My financial documents for the current year (FY26) do not show the required turnover. Can I submit documents from the previous year (FY25)?
>
> Yes. Route eligibility can be demonstrated using documents from either FY26 or FY25. Submit documents from whichever year meets the applicable threshold.

> [accordion] I do not have GST registration. Can I still apply?
>
> Yes. If your business is exempt from filing GST or if this is your first year of operation and you have not yet filed GST returns, you may submit a self-declaration confirming your turnover. This declaration will be used to assess your financial eligibility and will be recorded for audit purposes.

> [accordion] What is the Payer-Payee Transparency requirement?
>
> This requirement ensures that the third party receiving your customers' payments through Route is the one directly providing goods or services to those customers.
>
> To meet this requirement, submit a written confirmation describing your Route use case. Razorpay will review the submission and, once approved, it will be treated as a valid declaration of Payer-Payee Transparency for your account.

> [accordion] How do I submit the required compliance information?
>
> * **Unmanaged accounts:** Reply to the compliance email sent from `routepriority@razorpay.com` with the required documents and declaration.
> * **Managed accounts:** Contact your Razorpay account manager directly. You do not need to reply to the email.

> [accordion] How long does the review process take?
>
> The review process is expected to take 5 to 7 business days from the date of submission. You will be notified once the review is complete.

> [accordion] My request to continue Route has been denied. What does this mean?
>
> This means your submission did not meet either the minimum financial turnover criteria or the Payer-Payee Transparency requirement set by the RBI.
>
> All Route services on your account were discontinued effective **January 1, 2026**.
>
> Once your business meets the applicable turnover criteria in a subsequent financial year, you can reach out to reapply for Route access.

> [accordion] I want to stop using Razorpay Route. What happens next?
>
> If you would like to discontinue Route, please inform your account manager or contact [Razorpay Support](https://razorpay.com/support/). Once confirmed:
>
> * The Route page will no longer appear on your Dashboard.
> * Route API calls will not be authorised.
> * All customer payments will be settled in full to your primary Razorpay settlement account.
>
> You will then be responsible for manually transferring amounts to your vendors or linked parties. You can use Razorpay Payouts or any other suitable method for these transfers.

> [accordion] Is there an alternative to Razorpay Route?
>
> Razorpay Route automates the splitting of customer payments across multiple beneficiaries at the time of settlement. Without Route, the equivalent workflow is:
>
> 1. Customer payments are fully settled into your primary Razorpay account.
> 2. You manually transfer the relevant amounts to vendors or linked parties.
>
> For automating the second step, you can explore RazorpayX's intelligent transfer solutions.
>
> > [!NOTE]
> >
> > **Note:** RazorpayX is a separate legal entity with its own onboarding process. Please contact the RazorpayX team directly for details.

> [accordion] These RBI guidelines are making it harder for early-stage businesses to operate. Why is Razorpay enforcing this?
>
> We understand this is challenging for early-stage businesses. However, the RBI guidelines apply to all Payment Aggregators offering Route functionality and no business category has been exempted.
>
> If your business does not currently meet the turnover criteria, Route access cannot be continued. As an alternative, you can use a two-step payment flow where customer payments settle to your account and you then initiate transfers to vendors or linked accounts manually. We look forward to re-enabling Route once your business meets the applicable criteria.

> [accordion] How can I transfer money to customers?
>
> You can use Razorpay Route from the Dashboard or using APIs to transfer money to customers.
>
> **To use Route from the Dashboard**:
>
> 1. Log in to the Dashboard.
> 2. Find a payment on the Transactions panel (left column). Click on the Payment id to view its details on the right panel. Create a transfer from the payment.
> 3. Alternatively, find a payment under the Payments tab on the Route panel. Click on the Payment id to view its details and create a transfer.
>
> You can also use [Route Transfers APIs](https://razorpay.com/docs/api/payments/route.md) to transfer money.

> [accordion] How can I track the status of transactions initiated using Route?
>
> When a transfer is created from the Dashboard or using the Route APIs, you are notified if the transfer creation was successful or not.
>
> The transfer is processed asynchronously and on success, `transfer.processed` webhook is sent (if enabled). Know more about [setting up Webhooks](https://razorpay.com/docs/payments/route/subscribe-to-webhooks.md).

> [accordion] How can I track the status of funds transferred to linked accounts?
>
> The `transfer.processed` webhook is sent for every successful transfer. The webhook indicates that the requested transfer is processed, funds are debited from the business and credited to the linked account.
>
> Know more about [setting up Webhooks](https://razorpay.com/docs/payments/route/subscribe-to-webhooks.md).

> [accordion] Can you reverse a transfer?
>
> Yes, you can reverse transfers. You can initiate a reversal from the Dashboard or using APIs.
>
> **To create a reversal from the Dashboard**:
>
> 4. Log in to the Dashboard.
> 5. Go to **Route** → **Transfers**. Click on a **Transfer id** to view the details. Click on the **Create Reversal** button to reverse the transfer.
>    * You can also use the [Reverse Transfers from all Linked Accounts API](https://razorpay.com/docs/api/payments/route/reverse-a-transfer.md) to reverse money transfer.
>    * You can also [refund payment and simultaneously reverse](https://razorpay.com/docs/api/payments/route/refund-payments-and-reverse-transfer.md) all the transfers made on that payment.

> [accordion] Can I create transfers on an order for international currencies?
>
> No, you cannot create transfers on an order for international currencies. The transfer reversal is available only for **INR**.

> [accordion] When should I initiate Transfer using Payments?
>
> You should initiate Transfer using Payments when information regarding payment split is decided post customer transaction and/or has some other approval/verification dependencies on the linked accounts. For example, in life insurance, you can only transfer funds to a linked account post-approval and policy issuance.

> [accordion] When should I initiate Direct Transfers?
>
> **Direct Transfers** is an on-demand feature. Raise a request with [our Support team](https://razorpay.com/support/) to get it enabled for your account.\
> You should initiate Direct Transfers when fund transfers to a linked account is not necessarily linked to any incoming payments. You can also use this feature for payouts.

> [accordion] I have created a linked account on the Dashboard in the Test mode. Can I use it on the Live mode?
>
> You can use a linked account created in the **Test** mode on the **Live** mode and vice versa.

> [accordion] Does Razorpay Route support international currencies?
>
> Currently, we support only **INR** for Razorpay Route.

> [accordion] How do I create linked accounts using bulk upload?
>
> You can create linked accounts using bulk upload from the Dashboard. Know more about [Batch Upload](https://razorpay.com/docs/payments/route/batch-upload.md).

> [accordion] Should the linked account websites be whitelisted to use route?
>
> No. Your linked account websites do not need to be whitelisted to use Route. The only requirement is that your website, from which your customers will make the payment, must be whitelisted with Razorpay.

> [accordion] Why am I not able to create Linked Accounts from the Dashboard?
>
> If you are a Mutual Funds Distributor (MFD), Linked Accounts with Asset Management Company (AMC) details are automatically created after you get access to the Route. You do not need to create any Linked Accounts from the Dashboard. Please get in touch with our [support team](https://razorpay.com/support/) for any help on creating Linked Accounts.

> [accordion] Can I use the same Razorpay API Keys on multiple websites or domains?
>
> Yes, you can use the same set of Live Mode API Keys on multiple websites or domains.
>
> The Live Mode keys are tied to your single Razorpay account, allowing them to process live transactions from any domain where they are implemented. Using the same keys on a new website **will not impact** the live payments running on your existing, whitelisted website.
>
> **For Testing:**
>
> We strongly recommend using your **Test Mode API Keys** when integrating Razorpay on any new website. Test payments are simulated and ensure that your live payment processing on existing sites remains unaffected during development.
>
> > [!WARNING]
> >
> > **Watch Out!**
> >
> > Ensure your new website's domain is whitelisted in your Razorpay account to avoid payment disruptions once you switch to Live Mode.

> [accordion] How should I manage API Keys when working with a developer for integration?
>
> API Keys are generated and managed by the **Owner or Admin** roles in the Dashboard. Razorpay does not offer a separate Developer Access Role.
>
> To securely facilitate integration and testing (for example, for platforms like WooCommerce, where direct API key input might be required for some plugins), follow this standard workflow:
>
> * **Phase 1: Testing (Integration)**
>   The Owner or Admin must generate and securely share the **Test Mode API Keys** with the developer. The developer will use these keys to build and test the integration without affecting any live payments.
> * **Phase 2: Go-Live**
>   Once testing is complete, the Owner or Admin must generate the **Live Mode API Keys** and provide them to the developer to replace the Test Keys in the final application setup.
>
> This ensures security and maintains clear control over your live payment environment.

> [accordion] How do I transfer funds using the Route API after accepting a payment via a Razorpay Payment Link?
>
> You can transfer funds to Linked Accounts using the Route API by referencing the Payment id generated by the Payment Link transaction. This approach is called Create Transfers from Payments.
>
> You can execute the transfer in three ways:
>
> 1. **Dashboard:** Initiate a transfer directly from the specific Payment id within the Transactions or Route section of your Dashboard.
> 2. **API:** Use the **Create Transfers from Payments API**, where you specify the Payment id to be split among your Linked Accounts.
> 3. **Automatic:** If you set up an automatic split before the payment link is generated, the funds will be split instantly upon successful payment.
>
> Know more about the [Create Transfers from Payments API](https://razorpay.com/docs/api/payments/route/create-transfers-payments.md).

> [accordion] What are the different fees involved when splitting a payment using Razorpay Route?
>
> A Route transaction involves two distinct types of fees deducted from your account balance:
>
> 4. **Payment Gateway Fee:** This fee is charged on the **full Payment Amount** received from the customer, before any funds are split. This covers the cost of processing the original transaction.
> 5. **Transfer Fee:** This fee is charged on the **Amount Transferred** to each Linked Account. This covers the cost of facilitating the money transfer from your main account to the Linked Account(s).
>
> Both fees are calculated based on your agreed-upon pricing plan and are subject to GST (or local equivalent tax, where applicable). Your final commission or retained amount is the remaining balance after both fees and the transfer amount have been deducted.
>
> For detailed calculation examples, refer to our [Transfers and Related Fees Examples](https://razorpay.com/docs/payments/route/transfer-fees-example.md) page.

## VPA Settlements

> [accordion] What is VPA settlement and how does it work with Route?
>
> VPA (Virtual Payment Address) settlement allows you to pay beneficiaries using their UPI id instead of bank account details. When you create a Linked Account with a VPA, Route verifies the UPI id instantly and settles funds to the beneficiary's UPI-linked bank account within a few minutes of the payment being captured.
>
> VPA settlements are available for transactions up to ₹1 lakh per transfer (NPCI limit). For larger amounts, use bank account settlement.
>
> Know more about [VPA Settlements](https://razorpay.com/docs/payments/route/linked-account/vpa-settlements.md).

> [accordion] Can a Linked Account have both a VPA and a bank account for settlement?
>
> No. Each Linked Account can be configured with either a VPA or a bank account as the settlement destination, not both. To support both settlement methods for the same beneficiary, create two separate Linked Accounts, one with VPA and one with bank account details and route transfers accordingly.

> [accordion] What happens if a VPA payout fails?
>
> If a VPA payout fails (for example, because the beneficiary's UPI id became inactive), the settlement appears on the Dashboard under **Route** → **Settlements** → **Failed**. You should notify the beneficiary, collect an updated VPA, update the Linked Account and retry the settlement from the Dashboard under **Route** → **Settlements** → **Failed** → **Retry**.
>
> Know more about [handling VPA settlement failures](https://razorpay.com/docs/payments/route/linked-account/vpa-settlements.md#handle-vpa-settlement-failures).

## Penny Testing

> [accordion] What is Penny Testing?
>
> Penny Testing is a process of validating the bank details. Razorpay will transfer a nominal amount to the bank account details submitted to verify them. Transfers are allowed only on successful validation.

> [accordion] Is the Penny testing feature enabled for all Linked Accounts?
>
> No. The Penny Testing feature is enabled:
>
> * Only for **new** Linked Accounts.
> * Only for those accounts which have this feature enabled.

> [accordion] How long does it take for a Linked Account to get activated with the Penny Testing feature enabled?
>
> The Linked Account should get activated immediately. It should not take more than a minute to verify the bank details. Based on the verification results, it goes to the `activated` or `verification_failed` state.
>
> **Verification Failed**
>
> ![Route - Linked Account Verification Failed](https://razorpay.com/docs/build/browser/assets/images/route_la_pt_vf.jpg)
>
> **Activated**
>
> ![Route - Linked Account Activated](https://razorpay.com/docs/build/browser/assets/images/route_la_pt_act.jpg)
>
> **Verification Pending**
>
> ![Route - Linked Account Verification Pending](https://razorpay.com/docs/build/browser/assets/images/route_la_pt_vp.jpg)
>
> **Not Activated**
>
> ![Route - Linked Account Not Activated](https://razorpay.com/docs/build/browser/assets/images/route_la_pt_na.jpg)

> [accordion] What are the different activation statuses of a Linked Account?
>
> | Status | Description |
> | - | - |
> | `activated` | Linked Account bank details are successfully verified with Penny Testing and ready for transfers. |
> | `verification_pending` | Linked Account bank details are submitted for verification. It moves to the `activated` state if details are successfully verified. You cannot make transfers when Linked Accounts are in the `verification_pending` state. |
> | `verification_failed` | The Linked Account bank details are not verified successfully. You have to update the bank details to make transfers to this Linked Account by reaching out to the [Support team](https://razorpay.com/support/) [Support team](https://razorpay.com/support/#request). |
> | `not_activated` | The activation form for the Linked Account is not filled. Fill out the activation form to start the activation process. |

> [accordion] What happens to business's existing Linked Accounts when the Penny Testing feature is enabled?
>
> All the existing linked accounts are marked as **Bank Details Verified** and they will remain activated. No Penny Testing will be done for old Linked Accounts. You can operate those Linked Accounts as usual.

> [accordion] Can I create multiple Linked Accounts with the same email address?
>
> Yes, you can create multiple Linked Accounts with the same email address.
>
> * A Linked Account can have the same email address across different parent businesses.
> * At a business level, however, the email address of multiple Linked Accounts should be unique.
>
> **Example:**
> Acme Corp has Linked Account LA1 with the email address `la1@gmail.com`. Acme Corp will not be able to create more Linked Accounts with the same email address. However, other businesses such as Raftar Soft and ABC Co can still create Linked Accounts with the email `la1@gmail.com`. Further, [la1@gmail.com](mailto:la1@gmail.com) can be used to create a regular Razorpay account if it does not exist already.

> [accordion] Does  perform Penny Testing when I update a Linked Account's bank details?
>
> You should raise a support request to update the details of a Linked Account. Once they update the details, the Penny Testing will happen again and the status of the Linked Account will be automatically updated as per the result.

> [accordion] Can I modify the bank account details of the Linked Account or create another one if bank verification via Penny Testing fails?
>
> Razorpay will create the Linked Account even if the bank verification fails. Hence, creating another Linked Account will result in a duplicate check failure. You should raise a support request to update the bank account details.

> [accordion] How many Linked Accounts can I create in bulk for Penny Testing?
>
> You can upload 50,000 rows in one go with 11 MB as the max file size using the [Bulk Upload](https://razorpay.com/docs/payments/route/batch-upload.md#create-linked-accounts-via-batch-upload) feature. Below is the expected TAT:
>
> | No. of Records | TAT |
> | - | - |
> | 1,000 | 5min |
> | 10,000 | 50min |
> | 50,000 | 4h |

> [accordion] Will I receive a notification when the batch upload is completed?
>
> No. You can check the status of the upload only from the Dashboard.

> [accordion] Will I receive a notification when the Linked Account is activated?
>
> No. You do not get any notification when the Linked Account is activated.

> [accordion] Will I receive a notification when the Linked Account verification fails?
>
> No. You do not get any notification when the Linked Account verification fails.

> [accordion] Will the Penny Testing be done in the test mode?
>
> Yes. Penny Testing is supported in both the test and live modes.

> [accordion] Can I update my Linked Account's email address after they are created?
>
> Yes. You can update the email address of the created Linked Account using the Dashboard.
