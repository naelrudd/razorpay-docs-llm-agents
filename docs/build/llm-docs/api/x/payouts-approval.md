# Payouts Approval

In Payouts Approval API, the payout can be reviewed by multiple approvers from your [team](https://razorpay.com/docs/build/llm-docs/x/manage-teams.md) on the same level of approval. However, the payout is not processed until the [owner](https://razorpay.com/docs/build/llm-docs/x/manage-teams/create-user-role.md) approves it. 
      

      Payouts Approval API is not available by default. [Contact support](https://razorpay.com/docs/build/llm-docs/x/support.md) to get this feature activated on your account. To use the Approvals APIs, it is mandatory to be a [Technology Partner](https://razorpay.com/docs/build/llm-docs/partners/existing-merchant.md#become-a-razorpay-partner) and [integrate with OAuth](https://razorpay.com/docs/build/llm-docs/partners/technology-partners/onboard-businesses/integrate-oauth.md). Only then you can make payouts. 

        

      Fork the Razorpay Postman Public Workspace and try the Payouts Approval APIs using your [Test API Keys](https://razorpay.com/docs/build/llm-docs/x/dashboard/api-keys.md). 

        

      [](https://www.postman.com/razorpaydev/workspace/razorpay-public-workspace/folder/12492020-117c93d1-1a79-4958-9067-eb97a3459f08)
    

    
### Related Guides

      [About Approval Workflow](https://razorpay.com/docs/build/llm-docs/x/manage-teams/approval-workflow.md)
      [Set Up Webhooks](https://razorpay.com/docs/build/llm-docs/webhooks/setup-edit-payouts.md)
      [Webhook Payloads](https://razorpay.com/docs/build/llm-docs/webhooks.md)
      [Make Payouts](https://razorpay.com/docs/build/llm-docs/api/x/payouts.md)
    

    
### Endpoints

        - **post** `/v1/payouts/:id/approve` - Approve Payouts: 
          Approves the Payout.
        

        - **post** `/v1/payouts/:id/reject` - Reject Payouts: 
          Rejects the Payout.
