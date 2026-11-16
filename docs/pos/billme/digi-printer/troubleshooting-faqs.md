> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Troubleshooting & FAQs

> Troubleshoot common errors and find answers to frequently asked questions about Razorpay Digi Printer.

Available in
🇮🇳 India

> [accordion] Why is there a misalignment issue when printing directly?
>
> The misalignment issue may occur due to the paper size not matching the printed content, causing the alignment to be off. This can happen because:
>
> 1. The `directprint` value in the registry is set, preventing the print pop-up from launching.
> 2. The printer configurations on the system are incorrect.
> 3. The printer model, such as a POS 8c printer, may require specific settings to ensure proper alignment.

> [accordion] How can I fix the printer alignment issue?
>
> To resolve this issue, follow these steps:
>
> 1. **Clear the `directprint` value in the registry:** This ensures that the print pop-up appears, allowing proper configuration before printing.
> 2. **Check and correct the system's printer configurations:** Ensure that the paper size and scaling settings are accurate.
> 3. **Use a POS 8c printer if available:** Adjust the datatype to **NT EMF 1.008** to ensure the image scales and fits correctly on the paper.

> [accordion] What is the issue with the secondary screen during checkout?
>
> On checkout, the pop-up window displays the phone number correctly on the primary screen, but the secondary screen shows an incorrect message ("share your number for a digital bill") instead of the phone number.

> [accordion] How can I fix the issue with the secondary screen not displaying the phone number?
>
> The issue can be resolved by adjusting the code to account for screen resolution differences between the primary and secondary screens. For example:
>
> * **Primary screen resolution:** 1024x768
> * **Secondary screen resolution:** 600x800

> [accordion] Why does the "Failed to generate OTP for Razorpay EDC linking" error occur after running Upgrade.exe?
>
> This issue arises when the "Generate OTP" function in BillMeSettings is used after running Upgrade.exe. The error is likely caused by an incorrect configuration of the `DNSResolver` registry value.

> [accordion] How can I fix the OTP generation issue?
>
> To resolve this error, ensure the registry value for **DNSResolver** is correctly configured:
>
> * Set the value to **0** (default setting).
> * Only set it to **1** if using MCD functionality.

> [accordion] Why does the pop-up window show an empty text box instead of the previously used phone number during a transaction?
>
> This issue occurs when the system fails to auto-copy the previously used phone number into the pop-up text box. It may be caused by an incorrect configuration of the `NoExtractorFileType` registry value.

> [accordion] How can I fix the auto-copy issue?
>
> To resolve this problem, ensure the registry value for `NoExtractorFileType` is set correctly. Set it to **"txt"** instead of **"raw"**.

> [accordion] Why does the printed thermal copy show misalignment or cut off text on the right side?
>
> This issue occurs due to incorrect page dimension settings in the thermal printer configuration, causing the printed content to misalign or get truncated.

> [accordion] How can I fix the thermal print alignment issue?
>
> To resolve this problem, follow these steps:
>
> 1. Navigate to the `tpdps.gpd` file located in: `C:\Windows\System32\spool\drivers\x64\3`
> 2. Open the file and adjust the **PageDimensions** for the **ThermalReceipt** setting.
> 3. Experiment with new values for the page dimensions until the alignment is correct.

> [accordion] Why is the printer incorrectly printing multiple copies during transactions?
>
> This issue occurs due to improper configuration of the **BMAuto** and **WhiteList** settings, leading to unintended printing behaviour.

> [accordion] How can I fix the BMAuto setup issue?
>
> To resolve the problem, configure the following settings correctly:
>
> 1. Set **BMAuto** to **2.**
> 2. Set **BMCopies** to **0.**
> 3. Set **WhiteList** to **1.**
> 4. Ensure that the **WhiteListString** is properly defined for tax invoices.

> [accordion] Why does no print file appear in the print queue when using an Epson printer, and why is the printer paused?
>
> This issue occurs because the printer’s print processor is not correctly configured to match the required `PrintDataType` format, causing the printer to pause and fail to process print jobs.

> [accordion] How can I fix the hardware print issue with the Epson printer?
>
> To resolve this problem, follow these steps:
>
> 1. Navigate to **Printer Properties** for the Epson printer.
> 2. Go to the **Advanced Tab** and select **Print Processor.**
> 3. Set the print processor to **NT EMF 1.008** to match the registry settings.
>    This adjustment ensures compatibility between the printer and the configured data type, allowing print jobs to appear in the queue and process correctly.

> [accordion] Why is the total amount displayed incorrectly on the secondary screen (for example, 3000.00 appears as 300000.00)?
>
> This issue arises due to improper parsing of the total amount string, likely caused by incorrect spacing or formatting in the registry values for **MBILLPAY** and **FBILLPAY.**

> [accordion] How can I fix the total amount parsing issue on the secondary screen?
>
> To resolve this issue, verify and adjust the registry values:
>
> 1. Check the **MBILLPAY** and **FBILLPAY** registry settings.
> 2. Ensure that proper spacing and formatting are included in the parsed strings.
>    Setting up the correct registry value with all the spaces from the txt file resolves this issue.

> [accordion] Why are PDF files improperly formatted during printing, leading to incorrect paper usage?
>
> This issue occurs when there is a mismatch between the paper size settings in **BillMe** and the default printer, causing the PDF to print with incorrect formatting.

> [accordion] How can I fix the paper size mismatch issue?
>
> To resolve this problem, align the paper size settings:
>
> 1. Open the **Printer Properties** for the default printer.
> 2. Adjust the paper size settings to match the configuration in **BillMe.**

> [accordion] Why are transactions uploaded as CW instead of BM or BM+Print when files are moved or deleted from the upload/queued folder?
>
> This issue occurs when the number of files in the upload/queued folder exceeds the preconfigured limit, causing the system to incorrectly upload transactions as CW rather than BM or BM+Print.

> [accordion] How can I fix the issue of suspicious transactions due to file count limits?
>
> To resolve this, adjust the **FileLimit** registry value. Increase the **FileLimit** from **10** to **11** or **12** to accommodate more files per transaction.
> This adjustment will prevent transactions from being incorrectly uploaded and allow the system to handle a higher number of files.

> [accordion] Why do multi-page invoices result in paper cuts after each printed page?
>
> This issue occurs when the printer is set to automatically cut the paper after each page, which causes the paper cuts between pages when printing multi-page invoices.

> [accordion] How can I fix the issue of paper cuts when printing multi-page invoices?
>
> To resolve this, follow these steps:
>
> 1. Enable the **IsMultiPageInvoice** registry setting by setting it to **1.**
> 2. Adjust the printer settings to **disable** the automatic paper cutting after each page.
