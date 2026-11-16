> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Frequently Asked Questions (FAQs)

> Find answers to frequently asked questions about the Push Tokenisation.

Available in
🇮🇳 India

> [accordion] What is Push Tokenisation?
>
> With Push Tokenisation, you can enable your customers to save their cards directly through their bank's secure portal and enjoy hasslefree checkout experience across multiple merchants.

> [accordion] Can I use email instead of phone number?
>
> No, Push Tokenisation exclusively uses phone numbers as identifiers. This is a requirement from our banking partners to ensure consistent customer identification across systems. Make sure your checkout flow captures customer phone numbers.

> [accordion] What if my integration only uses customer IDs?
>
> You will need to update your integration to collect phone numbers. We recommend:
>
> * Adding phone number as a required field in your checkout.
> * Updating existing customer records to include phone numbers.
> * Using phone number as the primary identifier for token operations.

> [accordion] How do I handle customers with multiple phone numbers?
>
> Tokens are linked to the specific phone number used during bank portal registration. Ensure customers use their registered phone number during checkout for successful token retrieval.

> [accordion] Do all my customers automatically get Push Tokenisation?
>
> No, Push Tokenisation can be enabled only for customers who:
>
> * Have cards from participating banks.
> * Have opted for tokenisation through their bank portal.
> * Have selected your business during the setup process.

> [accordion] Which banks support Push Tokenisation?
>
> Push Tokenisation is supported by the following banks: Axis Bank, HDFC Bank, SBI Bank, RBL Bank, Yes Bank, Federal Bank, and Canara Bank.

> [accordion] Is user consent required for token creation?
>
> Yes, user consent is required for saving a card/creating a token. This is done during push tokenisation on the bank's portal.

> [accordion] Are the Saved Card feature and Tokenisation feature the same?
>
> Yes. As per the RBI guidelines, saved cards will be tokenised with networks and issuers to ensure compliance.
