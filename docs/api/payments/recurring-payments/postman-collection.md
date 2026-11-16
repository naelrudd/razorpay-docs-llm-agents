> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Postman Collection

> Download the Postman collection for Razorpay Recurring Payments.

Available in
🇮🇳 India

We have a Postman collection to make the integration quicker and easier. Click the **Download Postman Collection** button below to get started.

[Download Postman Collection](https://razorpay.com/docs/build/browser/assets/images/recurring_postman.zip)

## Instructions to Use Postman Collection

* All Razorpay APIs are authenticated using Basic Authentication.
  * [Generate API Keys](https://razorpay.com/docs/api/authentication.md#generate-api-keys) from the Dashboard.
  * Add your API Keys in Postman. Select the required API → Auth → Type = Basic Auth → Username = \[Your\_Key\_ID]; Password = \[Your\_Key\_secret]
  ![](https://razorpay.com/docs/build/browser/assets/images/api-postman_basic_auth.gif)
* Some APIs in the collection require data specific to your account such as `order_id`, `cust_id` and `token_id` either in the request body or as a path parameter.
  * For example, the create order API requires you to add the `cust_id` (Customer ID) in the request body.
  * These parameters are enclosed in \{} in the collection. For example, \{cust\_id}.
  * The API throws an error if these are incorrect or do not exist in your system.
