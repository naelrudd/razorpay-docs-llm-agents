> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Reconcile Payouts

> Check how payouts are reconciled in TallyPrime after approval in RazorpayX.

Available in
🇮🇳 India

After you [approve the payouts](https://razorpay.com/docs/x/tally-epayments/export-approve-payouts.md#approve-payouts) on the RazorpayX Dashboard, reconcile them on TallyPrime using the **Instrument Number** and **Bank Date**.

To reconcile the payouts:

1. After the payouts are approved, hover on the batch of payouts on the Tally Payouts page and click the **DOWNLOAD MIS** option.

   ![Download MIS](https://razorpay.com/docs/build/browser/assets/images/RZPX-tally-epayments-download-tally-mis.jpg)

2. Now shift to TallyPrime. Go to **TallyPrime** → **Import** → **Intermediate File**.

   ![Import Intermediate file](https://razorpay.com/docs/build/browser/assets/images/RZPX-tally-epayments-rzpx-reconciliation-step1.jpg)

3. Upload the MIS file downloaded from RazorpayX in the **File to import (CSV)** field.

   ![Uploading the File to CSV](https://razorpay.com/docs/build/browser/assets/images/RZPX-tally-epayments-rzpx-reconciliation-step2.jpg)

4. TallyPrime automatically reconciles all transactions and updates the bank date.

   ![Reconciliation](https://razorpay.com/docs/build/browser/assets/images/RZPX-tally-epayments-rzpx-reconciliation-step3.jpg)

### Related Information

* [About Tally e-Payments](https://razorpay.com/docs/x/tally-epayments.md)
* [Create RazorpayX Ledger in TallyPrime](https://razorpay.com/docs/x/tally-epayments/set-up.md)
* [Export and Approve Payouts](https://razorpay.com/docs/x/tally-epayments/export-approve-payouts.md)
