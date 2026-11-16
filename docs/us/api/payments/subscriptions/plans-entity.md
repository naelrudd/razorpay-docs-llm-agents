> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Plans Entity

> Know about the Plan entity and the associated parameter descriptions.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

The Plans entity has the following parameters.

```json Entity theme={null}
{
  "entity":"collection",
  "count":2,
  "items":[
    {
      "id":"plan_00000000000008",
      "entity":"plan",
      "interval":1,
      "period":"weekly",
      "item":{
        "id":"item_00000000000005",
        "active":true,
        "name":"Test plan - Monthly",
        "description":"Description for the test plan - Monthly",
        "amount":89900,
        "unit_amount":89900,
        "currency":"USD",
        "type":"plan",
        "unit":null,
        "tax_inclusive":false,
        "hsn_code":null,
        "sac_code":null,
        "tax_rate":null,
        "tax_id":null,
        "tax_group_id":null,
        "created_at":1580220461,
        "updated_at":1580220481
      },
      "notes":{
        "notes_key_1":"Tea, Earl Grey, Hot",
        "notes_key_2":"Tea, Earl Grey… decaf."
      },
      "created_at":1580220481
    },
    {
      "id":"plan_00000000000009",
      "entity":"plan",
      "interval":1,
      "period":"monthly",
      "item":{
        "id":"item_00000000000002",
        "active":true,
        "name":"Test plan - Annual",
        "description":null,
        "amount":79900,
        "unit_amount":79900,
        "currency":"USD",
        "type":"plan",
        "unit":null,
        "tax_inclusive":false,
        "hsn_code":null,
        "sac_code":null,
        "tax_rate":null,
        "tax_id":null,
        "tax_group_id":null,
        "created_at":1580220493,
        "updated_at":1580220493
      },
      "notes":[
        
      ],
      "created_at":1580220493
    }
  ]
}
```

**id** `string`

The unique identifier linked to a plan. This is used when creating a Subscription for customers.

**entity** `string`

The entity being created. Here, it is `plan`.

**interval** `integer`

This, combined with `period`, defines the frequency. If the billing cycle is 2 months, the value should be `2`.

> [!NOTE]
>
> **Handy Tips**
>
> For daily plans, the minimum value should be `7`.

**period** `string`

This, combined with `interval`, defines the frequency. Possible values:

* `daily`
* `weekly`
* `monthly`
* `quarterly`
* `yearly`

If the billing cycle is 2 months, the value should be `monthly`.

**item** `object`

Details of the plan.

**id** `string`

The unique identifier linked to an item. For example, `item_00000000000001`.

**name** `string`

Name of the plan. For example, `Test Plan`.

**amount** `integer`

Amount for the plan. When you use this plan to create a Subscription, the customer will be charged this amount periodically.

**currency** `string`

Currency for the payment. Defaults to `USD`.

**description** `string`

Description of the plan. For example, `Description of the test plan`.

**notes** `object`

Notes you can enter for the contact for future reference. This is a key-value pair. You can enter a maximum of 15 key-value pairs. For example, `"note_key": "Monthly Gym"`.

**created\_at** `integer`

The Unix timestamp at which the plan was created.
