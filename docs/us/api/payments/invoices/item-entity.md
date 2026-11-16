> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Items Entity

> Entity parameters and sample code for Items API.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇺🇸 United States

The Items entity has the following parameters:

```json Entity theme={null}
{
  "id": "item_JInaSLODeDUQiQ",
  "active": true,
  "name": "Book / English August",
  "description": "An Indian story, Booker prize winner.",
  "amount": 20000,
  "unit_amount": 20000,
  "currency": "USD",
  "type": "invoice",
  "unit": null,
  "tax_inclusive": false,
  "hsn_code": null,
  "sac_code": null,
  "tax_rate": null,
  "tax_id": null,
  "tax_group_id": null,
  "created_at": 1649843796
}
```

**id** `string`

The unique identifier of the item.

**active** `boolean`

Indicates the status of the item. Possible values:

* `true` (default): Item is in the active state.
* `false`: Item is in the inactive state.

**name** `string`

The name of the item.

**description** `string`

A text description about the item.

**unit\_amount** `integer`

The per unit billing amount for each individual unit.

**amount** `integer` *required*

The price of the item.

**currency** `string` *required*

The currency in which the amount should be charged.

**type** `string`

Here, it must be `invoice`.

**unit** `integer`

The number of units of the item billed in the invoice.

**tax\_inclusive** `boolean`

Indicates whether the base amount includes tax.

* `true`: The base amount includes tax.
* `false`: The base amount does not include tax. By default, the value is set to `false`.

**hsn\_code** `integer`

The 8-digit code used to classify the product as per the Harmonised System of Nomenclature.

**sac\_code** `integer`

The 6-digit code used to classify the service as per the Services Accounting Code.

**tax\_rate** `string`

The percentage at which an individual or a corporation is taxed.

**tax\_id** `string`

The identification number that gets displayed on invoices issued to the customer.

**tax\_group\_id** `string`

The identification number for the tax group. A tax group is a collection of taxes that can be applied as a single set of rules.

**created\_at** `integer`

Unix timestamp, at which the item was created. For example, `1649843796`.
