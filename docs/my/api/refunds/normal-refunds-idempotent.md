> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Create a Normal Refund (Idempotent Request)

> Retry or send the same normal refund request multiple times safely using the Razorpay Curlec API.

Available in
🇮🇳 India
🇲🇾 Malaysia

Idempotency allows you to safely retry or send the same request multiple times without fear of repeating the normal refund request more than once.

* When you try to create a normal refund, in some cases due to network downtimes, you may not get a response from our servers. As a consequence, you will not be aware of the refund id or its state. In such cases, you can safely retry the transaction using the same idempotency key without risk of double-refund or duplication.
* To make a normal refund request idempotent, add the header `X-Refund-Idempotency` to the request and pass an idempotency key against it. The idempotency key must be at least 10 character long and can contain alphabets, numbers, hyphens and underscores only. For example, `550e8400-e29b-41d4-a716-446655440000`.
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
  "amount": 500100
}'
```

```bash CLI theme={null}
razorpay refunds create pay_ABC123 --amount 500100 --idempotency-key 550e8400-e29b-41d4-a716-446655440000
```

```json Success theme={null}
{
  "id": "rfnd_FP8QHiV938haTz",
  "entity": "refund",
  "amount": 500100,
  "receipt": "Receipt No. 31",
  "currency": "MYR",
  "payment_id": "pay_29QQoUBi66xm2f",
  "notes": {},
  "acquirer_data": {
    "arn": null
  },
  "created_at": 1597078866,
  "batch_id": null,
  "status": "processed",
  "speed_processed": "normal",
  "speed_requested": "normal"
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

The amount to be refunded. Amount should be in the smallest unit of the currency in which the payment was made. In the case of three decimal currencies, such as KWD, BHD and OMR, to refund a payment of 295.991, pass the value as `295990`. And in the case of zero decimal currencies such as JPY, to refund a payment of 295, pass the value as `295`.

* For a **partial refund**, enter a value lesser than the payment amount. For example, if the payment amount is ₹1500 and you want to refund only ₹500, you must pass `50000`.
* For **full refund**, enter the entire payment amount. If the `amount` parameter is not passed, the entire payment amount will be refunded.

> [!WARNING]
>
> **Watch Out!**
>
> As per payment guidelines, you should pass the last decimal number as 0 for three decimal currency payments. For example, if you want to refund a customer 99.991 KD for a transaction, you should pass the value for the amount parameter as `99990` and not `99991`.

**speed** `string`

The speed at which the refund is to be processed. The default value is `normal`. Refund will be processed via the normal speed, and the customer will receive the refund within 5-7 working days.

**notes** `json object`

Key-value pairs used to store additional information. A maximum of 15 key-value pairs can be included.

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

The currency of payment amount for which the refund is initiated. Check the list of [supported currencies](https://razorpay.com/docs/my/payments/international-payments#malaysian-businesses).

**payment\_id** `string`

The unique identifier of the payment for which a refund is initiated. For example, `pay_FgR9UMzgmKDJRi`.

**created\_at** `integer`

Unix timestamp at which the refund was created. For example, `1600856650`.

**batch\_id** `string`

This parameter is populated if the refund was created as part of a batch upload. For example, `batch_00000000000001`.

**notes** `json object`

Key-value store for storing your reference data. A maximum of 15 key-value pairs can be included. For example, `"note_key": "Beam me up Scotty"`.

**receipt** `string`

A unique identifier provided by you for your internal reference.

**acquirer\_data** `array`

A dynamic array consisting of a unique reference number (either RRN, ARN or UTR) that is provided by the banking partner when a refund is processed. This reference number can be used by the customer to track the status of the refund with the bank.

**status** `string`

Indicates the state of the refund. Possible values:

* `pending`: This state indicates that Razorpay Curlec is attempting to process the refund.
* `processed`: This is the final state of the refund.
* `failed`: A refund can attain the failed state in the following scenarios:\\

  * Normal refund is not possible for a payment which is more than 6 months old.\\

  * Instant Refund can sometimes fail because of customer's account or bank-related issues.

**speed\_requested** `string`

The processing mode of the refund seen in the refund response. \
&#x20;This attribute is seen in the refund response only if the `speed` parameter is set in the refund request.\
Possible values:

* `normal`: Indicates that the refund will be processed via the normal speed. The refund will take 5-7 working days.
* `optimum`: Indicates that the refund will be processed at an optimal speed based on Razorpay Curlec's internal fund transfer logic.
  * If the refund can be processed instantly, Razorpay Curlec will do so, irrespective of the payment method used to make the payment.
  * If an instant refund is not possible, Razorpay Curlec will initiate a refund that is processed at the normal speed.

**speed\_processed** `string`

This is a parameter in the response which describes the mode used to process a refund. \
&#x20;This attribute is seen in the refund response only if the `speed` parameter is set in the refund request. Possible values:

* `instant`: Indicates that the refund has been processed instantly via fund transfer.
* `normal`: Indicates that the refund has been processed by the payment processing partner. The refund will take 5-7 working days.

## Errors

> [accordion] The API \{key/secret} provided is invalid.
>
> **Code:** `4xx`
>
> The API credentials passed in the API call differ from the ones generated on the Dashboard.
>
> **Solution:** The API keys must be active and entered correctly with no whitespace before or after.

> [accordion] \{Payment\_id} is not a valid id.
>
> **Code:** `400`
>
> The `payment_id` provided is invalid.
>
> **Solution:** Use a valid `payment_id`.

> [accordion] The requested URL was not found on the server.
>
> **Code:** `400`
>
> Possible reasons:
>
> * The URL is wrong or is missing something.
> * A POST API is executed by GET method.
>
> **Solution:**
>
> * Ensure that the URL is correct and complete.
> * Use the correct method, that is, POST.

> [accordion] \{any Extra field} is/are not required and should not be sent.
>
> **Code:** `400`
>
> An additional or unrequired parameter is passed.
>
> **Solution:** Ensure that you only pass the required parameters in the request body.

> [accordion] The refund amount provided is greater than amount captured.
>
> **Code:** `400`
>
> The refund amount entered is more than the amount captured.
>
> **Solution:** Enter an amount equal to or less than the amount captured.

> [accordion] The amount must be at least
> INR 1.00.
>
> **Code:** `400`
>
> The refund amount entered is less than .
>
> **Solution:** Enter an amount of at least .

> [accordion] The payment has been fully refunded already.
>
> **Code:** `400`
>
> The `payment_id` has already been refunded fully.
>
> **Solution:** Use a `payment_id` that has not been fully refunded.

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
> **Solution:** Retry the request after some time. If the issue persists, contact [Razorpay Curlec Support](https://curlec.com/support/).

> [accordion] Internal server error - Failed to parse request body
>
> **Code:** `500`
>
> The server failed to parse the request body to generate the request hash.
>
> **Solution:** Ensure the request body is properly formatted as valid JSON. If the issue persists, contact [Razorpay Curlec Support](https://curlec.com/support/).

> [accordion] The idempotency key must be at least 10 characters long.
>
> **Code:** `400`
>
> The idempotency key provided is less than 10 characters in length.
>
> **Solution:** Use an idempotency key that is at least 10 characters long.

> [accordion] The idempotency key must only contain alphanumeric characters, underscores, and hyphens
>
> **Code:** `400`
>
> The idempotency key contains invalid special characters.
>
> **Solution:** Ensure the idempotency key only contains alphanumeric characters (A-Z, a-z, 0-9), underscores (\_), and hyphens (-).

> [accordion] Merchant id not found in authentication
>
> **Code:** `500`
>
> The request contains an idempotency key but the merchant authentication is invalid or missing.
>
> **Solution:** Ensure you are using valid API credentials (Key ID and Key Secret) for authentication. If the issue persists, contact [Razorpay Curlec Support](https://curlec.com/support/).
