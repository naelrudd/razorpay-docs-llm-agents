> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Delete a Bill

> Delete Bills with this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to delete a Bill.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X DELETE https://api.razorpay.com/v1/bills/bill_4a5e9ulyzk1mk2
```

```json Success theme={null}
{"status": "deleted"}
```

```json Failure theme={null}
{
  "error": {
    "code": "UNAUTHORISED",
    "description": "client not authorised to update",
    "field": null,
    "source": "business",
    "step": "authentication",
    "reason": "unauthorised",
    "metadata": {}
  }
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the bill that must be deleted.

## Errors

> [accordion] client not authorised to update
>
> **Code:** `401`
>
> The client credentials are unauthorised to make changes to this bill.
>
> **Solution:** Use authorised credentials to make changes to the bill.

> [accordion] Operation failed
>
> **Code:** `500`
>
> There is an internal server error
>
> **Solution:** There is a server issue. Raise a support ticket with us to get this resolved.
