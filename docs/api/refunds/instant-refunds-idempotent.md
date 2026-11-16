> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create an Instant Refund (Idempotent Request)

> Retry or send the same instant refund request multiple times safely using the Razorpay API.

Available in
🇮🇳 India

Idempotency allows you to safely retry or send the same request multiple times without fear of repeating the instant refund request more than once.

* When you try to create an instant refund, in some cases due to network downtimes, you may not get a response from our servers. As a consequence, you will not be aware of the refund id or its state. In such cases, you can safely retry the transaction using the same idempotency key without risk of double-refund or duplication.
* To make an instant refund request idempotent, add the header `X-Refund-Idempotency` to the request and pass an idempotency key against it. The idempotency key must be at least 10 character long and can contain alphabets, numbers, hyphens and underscores only. For example, `550e8400-e29b-41d4-a716-446655440000`.
* Idempotency is supported for both Normal and Instant Refunds APIs.

> [!NOTE]
>
> **Handy Tips**
>
> * When retrying a request, the request body must be the same as the first request for idempotency to work. A different payload will be rejected as a `BAD_REQUEST`.
> * The idempotency key in retries must be the same as the original request.
> * Use unique idempotency keys for each unique request.
> * If a request is received while a prior request is still being processed, the system will return a 409 Conflict status code. You may retry the request upon receiving this response.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET] \
-X POST https://api.razorpay.com/v1/payments/pay_29QQoUBi66xm2f/refund \
-H 'Content-Type: application/json' \
-H 'X-Refund-Idempotency: 550e8400-e29b-41d4-a716-446655440000' \
-d '{
  "amount":500100,
  "speed":"optimum",
  "receipt":"Receipt No. 31",
  "notes":{
    "notes_key_1":"Tea, Earl Grey, Hot",
    "notes_key_2":"Tea, Earl Grey… decaf."
  }
}'
```

```bash CLI theme={null}
razorpay refunds create pay_ABC123 --amount 500100 --speed optimum --idempotency-key 550e8400-e29b-41d4-a716-446655440000
```

```json Success theme={null}
{
  "id": "rfnd_FP8R8EGjGbPkVb",
  "entity": "refund",
  "amount": 500100,
  "currency": "INR",
  "payment_id": "pay_29QQoUBi66xm2f",
  "notes": {
    "notes_key_1": "Tea, Earl Grey, Hot",
    "notes_key_2": "Tea, Earl Grey… decaf."
  },
  "receipt": "Receipt No. 31",
  "acquirer_data": {
    "arn": null
  },
  "created_at": 1597078914,
  "batch_id": null,
  "status": "processed",
  "speed_processed": "normal",
  "speed_requested": "optimum"
}
```

```json Failure theme={null}
{
  "error": {
    "code": "BAD_REQUEST_ERROR",
    "description": "Different request with the same idempotency key has already been processed.",
    "source": "NA",
    "step": "NA",
    "reason": "NA",
    "metadata": {}
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the payment which needs to be refunded.

## Request Parameters

**amount** `integer`

The amount to be refunded. Amount should be in the smallest unit of the currency in which the payment was made. **Required in case of partial refund**.

* For a **partial refund**, enter a value lesser than the payment amount. For example, if the payment amount is ₹1200 and you want to refund only ₹200, you must pass `20000`.
* In case of a **full refund**, enter the full payment amount. If `amount` parameter is not passed, the entire payment amount will be refunded.

**speed** `string` *required*

Here, it must be `optimum`. Indicates that the refund will be processed at an optimal speed based on Razorpay's internal fund transfer logic.

* If the refund can be processed instantly, Razorpay will do so, irrespective of the payment method used to make the payment.
* If an instant refund is not possible, Razorpay will initiate a refund that is processed at the normal speed.

**notes** `json object`

This is a key-value pair that can be used to store additional information about the entity. It can hold a maximum of 15 key-value pairs, 256 characters (maximum) each. For example, `"note_key": "Beam me up Scotty”`.

**receipt** `string`

A unique identifier provided by you for your internal reference.

## Response Parameters

**id** `string`

The unique identifier of the refund. For example, `rfnd_FgRAHdNOM4ZVbO`.

**entity** `string`

Indicates the type of entity. Here, it is `refund`.

**amount** `integer`

The amount to be refunded (in the smallest unit of currency). \
&#x20;For example, if the refund value is ₹30 it will be `3000`.

**currency** `string`

The currency of payment amount for which the refund is initiated. Check the list of [supported currencies](https://razorpay.com/docs/payments/international-payments#supported-currencies).

**payment\_id** `string`

The unique identifier of the payment for which a refund is initiated. For example, `pay_FgR9UMzgmKDJRi`.

**created\_at** `integer`

Unix timestamp at which the refund was created. For example, `1600856650`.

**batch\_id** `string`

This parameter is populated if the refund was created as part of a batch upload. For example, `batch_00000000000001`.

**notes** `json object`

Key-value store for storing your reference data. A maximum of 15 key-value pairs can be included. For example, `"note_key": "Beam me up Scotty”`.

**receipt** `string`

A unique identifier provided by you for your internal reference.

**acquirer\_data** `array`

A dynamic array consisting of a unique reference number (either RRN, ARN or UTR) that is provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

**status** `string`

Indicates the state of the refund. Possible values:

* `pending`: This state indicates that Razorpay is attempting to process the refund.
* `processed`: This is the final state of the refund.
* `failed`: A refund can attain the failed state in the following scenarios:\\

  * Normal refund is not possible for a payment which is more than 6 months old.\\

  * Instant Refund can sometimes fail because of customer's account or bank-related issues.

**speed\_requested** `string`

The processing mode of the refund seen in the refund response. \
&#x20;This attribute is seen in the refund response only if the `speed` parameter is set in the refund request.\
Possible values:

* `normal`: Indicates that the refund will be processed via the normal speed. The refund will take 5-7 working days.
* `optimum`: Indicates that the refund will be processed at an optimal speed based on Razorpay's internal fund transfer logic.
  * If the refund can be processed instantly, Razorpay will do so, irrespective of the payment method used to make the payment.
  * If an instant refund is not possible, Razorpay will initiate a refund that is processed at the normal speed.

**speed\_processed** `string`

This is a parameter in the response which describes the mode used to process a refund. \
&#x20;This attribute is seen in the refund response only if the `speed` parameter is set in the refund request. Possible values:

* `instant`: Indicates that the refund has been processed instantly via fund transfer.
* `normal`: Indicates that the refund has been processed by the payment processing partner. The refund will take 5-7 working days.

## Errors

> [accordion] Different request with the same idempotency key has already been processed.
>
> **Code:** `409`
>
> Another refund request with different parameters has been processed using the same idempotency key.
>
> **Solution:** Use a unique idempotency key for the new request and retry.

> [accordion] Another request with the same idempotency key is still in progress.
>
> **Code:** `409`
>
> A refund request with the same idempotency key is currently being processed and has not yet returned a response.
>
> **Solution:** Wait for the previous request to complete or use a different idempotency key.

> [accordion] Internal server error - Failed to fetch idempotency record
>
> **Code:** `500`
>
> The server encountered an error while retrieving the idempotency record.
>
> **Solution:** Retry the request after some time. If the issue persists, contact [Razorpay Support](https://razorpay.com/support).

> [accordion] Internal server error - Failed to parse request body
>
> **Code:** `500`
>
> The server failed to parse the request body to generate the request hash.
>
> **Solution:** Ensure the request body is properly formatted as valid JSON. If the issue persists, contact [Razorpay Support](https://razorpay.com/support).

> [accordion] The idempotency key must be at least 10 characters long.
>
> **Code:** `400`
>
> The idempotency key provided is less than 10 characters in length.
>
> **Solution:** Use an idempotency key that is at least 10 characters long.

> [accordion] The idempotency key must only contain alphanumeric characters, underscores and hyphens.
>
> **Code:** `400`
>
> The idempotency key contains invalid special characters.
>
> **Solution:** Ensure the idempotency key only contains alphanumeric characters (A-Z, a-z, 0-9), underscores (\_) and hyphens (-).

> [accordion] Merchant id not found in authentication
>
> **Code:** `500`
>
> The request contains an idempotency key but the merchant authentication is invalid or missing.
>
> **Solution:** Ensure you are using valid API credentials (Key ID and Key Secret) for authentication. If the issue persists, [Razorpay Support](https://razorpay.com/support).
