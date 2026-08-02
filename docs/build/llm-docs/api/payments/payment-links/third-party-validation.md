# Perform Third-Party Validation Using Payment Links

**POST** `/v1/payment_links`

Use this endpoint to comply with the regulatory guidelines in a manner such that the customers make payments only from their registered bank account. 

- TPV stands for Third Party Validation. This feature is made available only to businesses operating in Mutual fund, Securities or Brokerage sectors. 

- You can perform third party validation using Payment Links by passing the `options` parameter along with the Create Payment Links API request. Check the [use cases to perform TPV using Payment Links](https://razorpay.com/docs/build/llm-docs/payments/payment-links/use-cases.md).

**INFO**

**Feature Request**

This is an on-demand feature. Please raise a request with our [Support team](https://razorpay.com/support/#request) to get this feature activated on your Razorpay account.

### Request

```curl: Curl

Use this API endpoint for Netbanking

curl -X POST https://api.razorpay.com/v1/payment_links
-H 'content-type: application/json'
-d '{
  "amount": 1000,
  "currency": "INR",
  "accept_partial": true,
  "first_min_partial_amount": 100,
  "reference_id": "#425",
  "description": "Payment for policy no #23456",
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com"
  },
  "notify": {
    "sms": true,
    "email": true
  },
  "reminder_enable": true,
  "options": {
    "order": {
      "method": "netbanking",
      "bank_account": {
        "account_number": "04300040049999",
        "name": "Gaurav Kumar",
        "ifsc": "KKBK0000430"
      }
    }
  }
}'

Use this API endpoint for UPI

curl -X POST https://api.razorpay.com/v1/payment_links
-H 'content-type: application/json'
-d '{
  "amount": 1000,
  "currency": "INR",
  "accept_partial": true,
  "first_min_partial_amount": 100,
  "reference_id": "#42ds6",
  "description": "Payment for policy no #23456",
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com"
  },
  "notify": {
    "sms": true,
    "email": true
  },
  "reminder_enable": true,
  "options": {
    "order": {
      "method": "upi",
      "bank_account": {
        "account_number": "04300040049999",
        "name": "Gaurav Kumar",
        "ifsc": "KKBK0000430"
      }
    }
  }
}'

Use this API endpoint for for either Netbanking or UPI

curl -X POST https://api.razorpay.com/v1/payment_links
-H 'content-type: application/json'
-d '{
  "amount": 1000,
  "currency": "INR",
  "accept_partial": true,
  "first_min_partial_amount": 100,
  "reference_id": "#427",
  "description": "Payment for policy no #23456",
  "customer": {
    "name": "Gaurav Kumar",
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com"
  },
  "notify": {
    "sms": true,
    "email": true
  },
  "reminder_enable": true,
  "options": {
    "order": {
      "bank_account": {
        "account_number": "04300050077634",
        "name": "Gaurav Kumar",
        "ifsc": "KKBK0000430"
      }
    }
  }
}'

```java: Java

Use this API endpoint for Netbanking

import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
JSONObject paymentLinkRequest = new JSONObject();
paymentLinkRequest.put("amount", 1000);
paymentLinkRequest.put("currency", "INR");
paymentLinkRequest.put("accept_partial", true);
paymentLinkRequest.put("first_min_partial_amount", 100);
paymentLinkRequest.put("expire_by", 1691097057);
paymentLinkRequest.put("reference_id", "TS1989");
paymentLinkRequest.put("description", "Payment for policy no #23456");

JSONObject customer = new JSONObject();
customer.put("name", "Gaurav Kumar");
customer.put("contact", "+919876543210");
customer.put("email", "gaurav.kumar@example.com");
paymentLinkRequest.put("customer", customer);

JSONObject notify = new JSONObject();
notify.put("sms", true);
notify.put("email", true);
paymentLinkRequest.put("notify", notify);

paymentLinkRequest.put("reminder_enable", true);

JSONObject options = new JSONObject();
JSONObject methodOption = new JSONObject();
methodOption.put("method", "netbanking");

JSONObject bankingDetails = new JSONObject();
bankingDetails.put("account_number", "04300040049999");
bankingDetails.put("name", "Gaurav Kumar");
bankingDetails.put("ifsc", "KKBK0000430");
methodOption.put("bank_account", bankingDetails);

options.put("order", methodOption);
paymentLinkRequest.put("options", options);

PaymentLink payment = instance.paymentLink.create(paymentLinkRequest);

Use this API endpoint for UPI

import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
JSONObject paymentLinkRequest = new JSONObject();
paymentLinkRequest.put("amount", 1000);
paymentLinkRequest.put("currency", "INR");
paymentLinkRequest.put("accept_partial", true);
paymentLinkRequest.put("first_min_partial_amount", 100);
paymentLinkRequest.put("expire_by", 1691097057);
paymentLinkRequest.put("reference_id", "TS1989");
paymentLinkRequest.put("description", "Payment for policy no #23456");

JSONObject customer = new JSONObject();
customer.put("name", "Gaurav Kumar");
customer.put("contact", "+919876543210");
customer.put("email", "gaurav.kumar@example.com");
paymentLinkRequest.put("customer", customer);

JSONObject notify = new JSONObject();
notify.put("sms", true);
notify.put("email", true);
paymentLinkRequest.put("notify", notify);

paymentLinkRequest.put("reminder_enable", true);

JSONObject options = new JSONObject();
JSONObject methodOption = new JSONObject();
methodOption.put("method", "upi");

JSONObject bankingDetails = new JSONObject();
bankingDetails.put("account_number", "04300040049999");
bankingDetails.put("name", "Gaurav Kumar");
bankingDetails.put("ifsc", "KKBK0000430");
methodOption.put("bank_account", bankingDetails);

options.put("order", methodOption);
paymentLinkRequest.put("options", options);

PaymentLink payment = instance.paymentLink.create(paymentLinkRequest);

Use this API endpoint for for either Netbanking or UPI

import org.json.JSONObject;
import com.razorpay.Payment;
import com.razorpay.RazorpayClient;
import com.razorpay.RazorpayException;

RazorpayClient razorpay = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
JSONObject paymentLinkRequest = new JSONObject();
paymentLinkRequest.put("amount", 1000);
paymentLinkRequest.put("currency", "INR");
paymentLinkRequest.put("accept_partial", true);
paymentLinkRequest.put("first_min_partial_amount", 100);
paymentLinkRequest.put("expire_by", 1691097057);
paymentLinkRequest.put("reference_id", "TS1989");
paymentLinkRequest.put("description", "Payment for policy no #23456");

JSONObject customer = new JSONObject();
customer.put("name", "Gaurav Kumar");
customer.put("contact", "+919876543210");
customer.put("email", "gaurav.kumar@example.com");
paymentLinkRequest.put("customer", customer);

JSONObject notify = new JSONObject();
notify.put("sms", true);
notify.put("email", true);
paymentLinkRequest.put("notify", notify);

paymentLinkRequest.put("reminder_enable", true);

JSONObject options = new JSONObject();
JSONObject methodOption = new JSONObject();

JSONObject bankingDetails = new JSONObject();
bankingDetails.put("account_number", "04300040049999");
bankingDetails.put("name", "Gaurav Kumar");
bankingDetails.put("ifsc", "KKBK0000430");
methodOption.put("bank_account", bankingDetails);

options.put("order", methodOption);
paymentLinkRequest.put("options", options);

PaymentLink payment = instance.paymentLink.create(paymentLinkRequest);

```csharp: .NET

Use this API endpoint for Netbanking

RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
Dictionary paymentLinkRequest = new Dictionary();
paymentLinkRequest.Add("amount", 1000);
paymentLinkRequest.Add("currency", "INR");
paymentLinkRequest.Add("accept_partial", true);
paymentLinkRequest.Add("first_min_partial_amount", 100);
paymentLinkRequest.Add("expire_by", 1691097057);
paymentLinkRequest.Add("reference_id", "TS1989");
paymentLinkRequest.Add("description", "Payment for policy no #23456");
Dictionary customer = new Dictionary();
customer.Add("name", "Gaurav Kumar");
customer.Add("contact", "+919876543210");
customer.Add("email", "gaurav.kumar@example.com");
paymentLinkRequest.Add("customer", customer);
Dictionary notify = new Dictionary();
notify.Add("sms", true);
notify.Add("email", true);
paymentLinkRequest.Add("reminder_enable", true);
Dictionary options = new Dictionary();
Dictionary methodOption = new Dictionary();
Dictionary bankingBank = new Dictionary();
bankingBank.Add("account_number", "04300040049999");
bankingBank.Add("name", "Gaurav Kumar");
bankingBank.Add("ifsc", "KKBK0000430");
methodOption.Add("method", "netbanking");
methodOption.Add("bank_account", bankingBank);
options.Add("order", methodOption);
paymentLinkRequest.Add("options", options);

PaymentLink paymentlink = client.PaymentLink.Create(paymentLinkRequest);

Use this API endpoint for UPI

RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
Dictionary paymentLinkRequest = new Dictionary();
paymentLinkRequest.Add("amount", 1000);
paymentLinkRequest.Add("currency", "INR");
paymentLinkRequest.Add("accept_partial", true);
paymentLinkRequest.Add("first_min_partial_amount", 100);
paymentLinkRequest.Add("expire_by", 1691097057);
paymentLinkRequest.Add("reference_id", "TS1989");
paymentLinkRequest.Add("description", "Payment for policy no #23456");
Dictionary customer = new Dictionary();
customer.Add("name", "Gaurav Kumar");
customer.Add("contact", "+919876543210");
customer.Add("email", "gaurav.kumar@example.com");
paymentLinkRequest.Add("customer", customer);
Dictionary notify = new Dictionary();
otify.Add("sms", true);
notify.Add("email", true);
paymentLinkRequest.Add("reminder_enable", true);
Dictionary options = new Dictionary();
Dictionary methodOption = new Dictionary();
Dictionary bankingBank = new Dictionary();
bankingBank.Add("account_number", "04300040049999");
bankingBank.Add("name", "Gaurav Kumar");
bankingBank.Add("ifsc", "KKBK0000430");
methodOption.Add("method", "upi");
methodOption.Add("bank_account", bankingBank);
options.Add("order", methodOption);
paymentLinkRequest.Add("options", options);

PaymentLink paymentlink = client.PaymentLink.Create(paymentLinkRequest);

Use this API endpoint for for either Netbanking or UPI

RazorpayClient client = new RazorpayClient("[YOUR_KEY_ID]", "[YOUR_KEY_SECRET]");
Dictionary paymentLinkRequest = new Dictionary();
paymentLinkRequest.Add("amount", 1000);
paymentLinkRequest.Add("currency", "INR");
paymentLinkRequest.Add("accept_partial", true);
paymentLinkRequest.Add("first_min_partial_amount", 100);
paymentLinkRequest.Add("expire_by", 1691097057);
paymentLinkRequest.Add("reference_id", "TS1989");
paymentLinkRequest.Add("description", "Payment for policy no #23456");
Dictionary customer = new Dictionary();
customer.Add("name", "Gaurav Kumar");
customer.Add("contact", "+919876543210");
customer.Add("email", "gaurav.kumar@example.com");
paymentLinkRequest.Add("customer", customer);
Dictionary notify = new Dictionary();
notify.Add("sms", true);
notify.Add("email", true);
paymentLinkRequest.Add("reminder_enable", true);
Dictionary options = new Dictionary();
Dictionary methodOption = new Dictionary();
Dictionary bankingBank = new Dictionary();
bankingBank.Add("account_number", "04300040049999");
bankingBank.Add("name", "Gaurav Kumar");
bankingBank.Add("ifsc", "KKBK0000430");
methodOption.Add("bank_account", bankingBank);
options.Add("order", methodOption);
paymentLinkRequest.Add("options", options);

PaymentLink paymentlink = client.PaymentLink.Create(paymentLinkRequest);

```bash: CLI
razorpay payment-links create \
  --amount 1000 \
  --currency INR \
  --order-method netbanking \
  --bank-account-number "1234567890" \
  --bank-account-name "Testing" \
  --bank-account-ifsc "HDFC0001234"
```

### Response

``` json: Netbanking
{
  "accept_partial": true,
  "amount": 1000,
  "amount_paid": 0,
  "callback_method": "",
  "callback_url": "",
  "cancelled_at": 0,
  "created_at": 1596525334,
  "currency": "INR",
  "customer": {
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "name": "Gaurav Kumar"
  },
  "deleted_at": 0,
  "description": "Payment for policy no #23456",
  "expire_by": 0,
  "expired_at": 0,
  "first_min_partial_amount": 100,
  "id": "plink_FMbF1mewlEnf3Q",
  "notes": null,
  "notify": {
    "email": true,
    "sms": true
  },
  "payments": null,
  "reference_id": "#42sd5",
  "reminder_enable": true,
  "reminders": [],
  "short_url": "https://rzp.io/i/XxDxHPE",
  "source": "",
  "source_id": "",
  "status": "created",
  "updated_at": 1596525334,
  "user_id": ""
}

```json: UPI
{
  "accept_partial": true,
  "amount": 1000,
  "amount_paid": 0,
  "callback_method": "",
  "callback_url": "",
  "cancelled_at": 0,
  "created_at": 1596525260,
  "currency": "INR",
  "customer": {
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "name": "Gaurav Kumar"
  },
  "deleted_at": 0,
  "description": "Payment for policy no #23456",
  "expire_by": 0,
  "expired_at": 0,
  "first_min_partial_amount": 100,
  "id": "plink_FMbDixdmiIH7HS",
  "notes": null,
  "notify": {
    "email": true,
    "sms": true
  },
  "payments": null,
  "reference_id": "#42ds6",
  "reminder_enable": true,
  "reminders": [],
  "short_url": "https://rzp.io/i/9ZSCLMJ",
  "source": "",
  "source_id": "",
  "status": "created",
  "updated_at": 1596525260,
  "user_id": ""
}

```json: Either
{
  "accept_partial": true,
  "amount": 1000,
  "amount_paid": 0,
  "callback_method": "",
  "callback_url": "",
  "cancelled_at": 0,
  "created_at": 1596525212,
  "currency": "INR",
  "customer": {
    "contact": "+919876543210",
    "email": "gaurav.kumar@example.com",
    "name": "Gaurav Kumar"
  },
  "deleted_at": 0,
  "description": "Payment for policy no #23456",
  "expire_by": 0,
  "expired_at": 0,
  "first_min_partial_amount": 100,
  "id": "plink_FMbCtD8G9nGHnw",
  "notes": null,
  "notify": {
    "email": true,
    "sms": true
  },
  "payments": null,
  "reference_id": "#qw427",
  "reminder_enable": true,
  "reminders": [],
  "short_url": "https://rzp.io/i/hEldEoc",
  "source": "",
  "source_id": "",
  "status": "created",
  "updated_at": 1596525212,
  "user_id": ""
}

```json: Failure
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "The api key provided is invalid",
    "source": "NA",
    "step": "NA",
    "reason": "NA",
    "metadata": {}
  }
}
```

### Parameters

`amount` _mandatory_
: `integer` Amount to be paid using the Payment Link. Must be in the smallest unit of the currency. For example, if you want to receive a payment of , you must enter the value `30000`. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as 295.

  
**WARN**

**Watch Out!**

As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

`currency` _optional_
: `string` A three-letter ISO code for the currency in which you want to accept the payment. For example, INR. Refer to the list of [supported currencies](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies).

  
**INFO**

**Handy Tips**

Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/build/llm-docs/payments/international-payments/currency-conversion.md) (May 2024).

.

`accept_partial` _optional_
: `boolean` Indicates whether customers can make [partial payments](https://razorpay.com/docs/build/llm-docs/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:
  - `true`: Customer can make partial payments.
  - `false` (default): Customer cannot make partial payments.

`first_min_partial_amount` _conditionally mandatory_
: `integer` Minimum amount, in currency subunits, that must be paid by the customer as the first partial payment. Default value is `100`. Default currency is `INR`. For example, if an amount of  is to be received from the customer in two installments of #1 - , #2 - , then you can set this value as `500000`. Must be passed along with `accept_partial` parameter.

`upi_link` _mandatory for creating UPI Payment Link_
: `boolean` Must be set to `true` for creating UPI Payment Link. If the `upi_link` parameter is not passed or passed with value as false, a Standard Payment Link will be created. Possible values:
  - `true`: Creates a UPI Payment Link.
  - `false`: Creates a Standard Payment Link.
  

`description` _optional_
: `string` A brief description of the Payment Link. The maximum character limit supported is 2048.

`reference_id` _optional_
: `string` Reference number tagged to a Payment Link. Must be a unique number for each Payment Link. The maximum character limit supported is 40.

`customer` _optional_
: `json object` Customer details

  `name` _optional_
  : `string` The customer's name.

  `email` _optional_
  : `string` The customer's email address.

  `contact` _optional_
  : `string` The customer's phone number.

`expire_by` _optional_
: `integer` Timestamp, in Unix, at which the Payment Link will expire. By default, a Payment Link will be valid for six months from the date of creation. Please note that the expire by date cannot exceed more than six months from the date of creation.

`notify` _optional_
: `array` Defines who handles Payment Link notification.

  `sms` _optional_
  : `boolean` Defines who handles the SMS notification. Possible values:
    - `true`: Razorpay handles the notification.
    - `false`: You handle the notification.

  `email` _optional_
  : `boolean` Defines who handles the email notification. Possible values:
    - `true`: Razorpay handles the notification.
    - `false`: You handle the notification.

`notes` _optional_
: `json object` Key-value pair that can be used to store additional information about the entity. Maximum 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Payment Link for Groceries.”`.

`callback_url` _optional_
: `string` If specified, adds a redirect URL to the Payment Link. Once customers completes the payment, they are redirected to the specified URL.

   
**INFO**

**Handy Tips** 

If the `callback_url` is passed, it must be passed in the correct format. That is, it should contain a URL.

`callback_method` _conditionally mandatory_
: `string` If `callback_url` parameter is passed, callback_method must be passed with the value `get`.

`reminder_enable` _optional_
: `boolean` Used to send [reminders](https://razorpay.com/docs/build/llm-docs/payments/payment-links/reminders.md) for the Payment Link. Possible values:
    - `true`: To send reminders.
    - `false`: To disable reminders.

`options` _mandatory_
: `array` Options to configure the customer's bank account details in the Payment Link. Parent parameter under which the `order` child parameter must be passed.

    `order` _mandatory_
    : `array` The parameter under which the customer's bank account details must be configured to perform third party validation.

      `bank_account` _mandatory_
      : `array` Parent parameter under which the customer's bank account details must be passed.

          `account_number` _mandatory_
          : `string` The bank account number through which the customer is expected to make the payment.

          `name` _mandatory_
          : `string` The name of the account holder.

          `ifsc` _mandatory_
          : `string` The IFSC associated with the bank account through which the customer is expected to make the payment.

      `method` _mandatory_
      : `string` Use this parameter to control which payment methods must be shown on the Checkout. Possible values:
        - `netbanking`
        - `upi`

        
**WARN**

**Note**

Do not pass this parameter if allowing customers to make payments using either `netbanking` or `upi` as the payment method.

          `netbanking`
          : `boolean` Used to enable or disable `netbanking` as a payment method  the Checkout. Possible values are:
            - `true` (default): Displays netbanking on the Checkout.
            - `false`: Hides netbanking on the Checkout.

          `upi`
          : `boolean` Used to enable or disable `UPI` as a payment method on the Checkout. Possible values are:
            - `true` (default): Displays UPI on the Checkout.
            - `false`: Hides UPI on the Checkout.

### Parameters

`accept_partial` 
: `boolean` Indicates whether customers can make [partial payments](https://razorpay.com/docs/build/llm-docs/payments/payment-links/partial-payments.md) using the Payment Link. Possible values:
  - `true`: Customer can make partial payments.
  - `false` (default): Customer cannot make partial payments.

`amount`
: `integer` Amount to be paid using the Payment Link. Must be in the smallest unit of the currency. For example, if you want to receive a payment of , you must enter the value `30000`. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as 295990. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as 295.

  
**WARN**

**Watch Out!**

As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

`amount_paid`
: `integer` Amount paid by the customer.

`callback_url`
: `string` If specified, adds a redirect URL to the Payment Link. Once the customer completes the payment, they are redirected to the specified URL.

`callback_method`
: `string` If `callback_url` parameter is passed, `callback_method` must be passed with the value `get`.

`cancelled_at`
: `integer` Timestamp, in Unix, at which the Payment Link was cancelled by you.

`created_at`
: `integer` Timestamp, in Unix, indicating when the Payment Link was created.

`currency`
: `string` Defaults to INR. We accept payments in [international currencies.](https://razorpay.com/docs/build/llm-docs/payments/international-payments.md#supported-currencies)

  
**INFO**

**Handy Tips**

Razorpay has added support for zero decimal currencies, such as JPY, and three decimal currencies, such as KWD, BHD, and OMR, allowing businesses to accept international payments in these currencies. Know more about [Currency Conversion](https://razorpay.com/docs/build/llm-docs/payments/international-payments/currency-conversion.md) (May 2024).

.

`customer`
: `json object` Customer details.

  `name`
  : `string` The customer's name.

  `email`
  : `string` The customer's email address.

  `contact`
  : `string` The customer's phone number.

`description`
: `string` A brief description of the Payment Link.

`expire_by`
: `integer` Timestamp, in Unix, when the Payment Link will expire. By default, a Payment Link will be valid for six months from the date of creation. Please note that the expire by date cannot exceed more than six months from the date of creation.

`expired_at`
: `integer` Timestamp, in Unix, at which the Payment Link expired.

`first_min_partial_amount`
: `integer` Minimum amount that must be paid by the customer as the first partial payment. For example, if an amount of  is to be received from the customer in two installments of #1 - , #2 - , then you can set this value as `500000`.

`id`
: `string` Unique identifier of the Payment Link. For example, `plink_ERgihyaAAC0VNW`.

`upi_link`
: `boolean` Indicates whether the Payment Link is a UPI Payment Link.
  - `true`: A UPI Payment Link has been created.
  - `false`: It is a Standard Payment Link.

`notes`
: `object` Set of key-value pairs that you can use to store additional information. You (Businesses) can enter a maximum of 15 key-value pairs, with each value having a maximum limit of 256 characters.

`notify`
: `array` Defines who handles Payment Link notification.

  `sms`
  : `boolean` Defines who handles the SMS notification.
    - `true`: Razorpay handles the notification.
    - `false`: Businesses handle the notification.

  `email`
  : `boolean` Defines who handles the email notification.
    - `true`: Razorpay handles the notification.
    - `false`: Businesses handle the notification.

`payments`
: `array` Payment details such as amount, payment id, Payment Link id and more are stored in this array. It is populated only after a payment is successfully captured by the customer. Only captured payments will be shown here. Until then, the value is `null`.

  `amount`
  : `integer` The amount paid by the customer using the Payment Link.

  `created_at`
  : `integer` Timestamp, in Unix, indicating when the payment was made.

  

  `method`
  : `string` The payment method used to make the payment. Possible values:
    - `netbanking`
    - `card`
    - `wallet`
    - `upi`
    - `emi`
    - `bank_transfer`
  
  

  

  

  

  `payment_id`
  : `string` Unique identifier of the payment made against the Payment Link.

  `plink_id`
  : `string` Unique identifier of the Payment Link. For example, `plink_ERgihyaAAC0VNW`.

  `status`
  : `string` The payment state. Possible value is `captured`.

  `updated_at`
  : `integer` Timestamp, in Unix, indicating when the payment was updated.

`reference_id`
: `string` Reference number tagged to a Payment Link. Must be a unique number for each Payment Link. The maximum character limit supported is 40.

`short_url`
: `string` The unique short URL generated for the Payment Link.

`status`
: `string` Displays the current state of the Payment Link. Possible values:
  - `created`
  - `partially_paid`
  - `expired`
  - `cancelled`
  - `paid`

`updated_at`
: `integer` Timestamp, in Unix, indicating when the Payment Link was updated.

`reminder_enable`
: `boolean` Used to send [reminders](https://razorpay.com/docs/build/llm-docs/payments/payment-links/reminders.md) for the Payment Link. Possible values:
    - `true`: To send reminders.
    - `false`: To disable reminders.

`user_id`
: `string` A unique identifier for the user role through which the Payment Link was created. For example, `HD1JAKCCPGDfRx`.

### Errors

The api \{key/secret\} provided is invalid
* code: 4xx
* description: There is a mismatch between the API credentials passed in the API call and the API credentials generated on the Dashboard.
* solution: Make sure that: - The API Keys are active and entered correctly.
- There are no white-spaces before or after the keys.

The \{input field\} is required
* code: 4xx
* description: A mandatory field is empty.
* solution: Ensure all mandatory fields and values are present.

wrong input fields sent.
* code: 400
* description: When wrong input fields are sent during Payment Link creation.
* solution: Ensure that the input fields are added correctly. Refer to these [request parameters](https://razorpay.com/docs/build/llm-docs/api/payments/payment-links.md#request-parameters) on how to add correct input fields.

payment link creation with reference ID already attempted
* code: 400
* description: An existing reference id has been passed.
* solution: Ensure that a unique reference id is used for all Payment Links.

timestamp must be atleast 15 minutes in future
* code: 400
* description: The epoch time passed is less than 15 minutes from the current time.
* solution: The `close_by` time should be more than 15 minutes from the current time.

Invalid access: Cannot create a payment link in live mode, as live mode is disabled for merchant.
* code: 400
* description: Occurs when you try to create a Payment Link in Live mode, but live mode is disabled for you
* solution: Raise a request to our [support team](https://razorpay.com/support/) to get live mode enabled for you.

Invalid access: Cannot create a payment link, as Merchant is Suspended.
* code: 400
* description: Occurs when you try to create a Payment Link when you have been been suspended.
* solution: Raise a request to our [support team](https://razorpay.com/support/) to be reinstated.

value: the length must not be greater than 255.
* code: 400
* description: When the notes length is greater than 255 characters during Payment Link creation.
* solution: Please create a payment link with notes values less than 255 characters.
