> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Update a Bill

> Update Bills with this endpoint.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore
🇺🇸 United States

Use this endpoint to update a Bill.

```bash Curl theme={null}
curl -u [YOUR_KEY_ID]:[YOUR_KEY_SECRET]
-X PATCH https://api.razorpay.com/v1/bills/bill_4a5e9ulyzk1mk2
-d '{
  "store_code": "",
  "customer": {
    "contact": "9000090001",
    "email": "saurav.kumar@example.com"
  },
  "receipt_type": "tax_invoice",
  "receipt_timestamp": 1907416999,
  "receipt_delivery": "digital",
  "line_items": [
    {
      "name": "T-Shirt",
      "quantity": 1,
      "employee_id": "1234",
      "total_amount": 100000
    }
  ],
  "receipt_summary": {
    "total_quantity": 1,
    "sub_total_amount": 100000,
    "currency": "INR",
    "net_payable_amount": 124000,
    "additional_charges": [
      {
        "description": "alteration charge",
        "amount": 2000
      },
      {
        "description": "cash on delivery",
        "amount": 2000
      },
    ],
    "payment_status": "paid"
  },
  "taxes": [
    {
      "name": "cgst",
      "percentage": 1200,
      "amount": 12000
    },
    {
      "name": "sgst",
      "percentage": 1200,
      "amount": 12000
    }
  ],
  "payments": [
    {
      "method": "Bank Transfer",
      "amount": 124000,
      "currency": "INR"
    }
  ]
}'
```

```json Success theme={null}
{
  "id": "bill_PYy4RWJWiNcPyE",
  "business_type": "retail",
  "business_category": "events",
  "customer": {
    "contact": "9000090001",
    "name": "d",
    "email": "saurav.kumar@example.com",
    "customer_id": "",
    "age": 2,
    "date_of_birth": "",
    "profession": "",
    "company_name": "",
    "marital_status": "",
    "spouse_name": "",
    "anniversary_date": "",
    "gender": "",
    "gstin": "",
    "billing_address": {
      "address_line_1": "",
      "address_line_2": "",
      "landmark": "",
      "city": "",
      "province": "",
      "pin_code": "",
      "country": ""
    },
    "shipping_address": {
      "address_line_1": "",
      "address_line_2": "",
      "landmark": "",
      "city": "",
      "province": "",
      "pin_code": "",
      "country": ""
    }
  },
  "loyalty": {
    "type": "",
    "card_num": "",
    "card_holder_name": "",
    "points_redeemed": 1
  },
  "store_code": "JK-001",
  "receipt_timestamp": 1907416999,
  "receipt_number": "INV00124992",
  "receipt_type": "tax_invoice",
  "receipt_delivery": "digital",
  "bar_code_number": "",
  "qr_code_number": "T2322 00000009291",
  "billing_pos_number": "bn",
  "pos_category": "traditional_pos",
  "order_number": "",
  "order_service_type": "",
  "delivery_status_url": "",
  "line_items": [
    {
      "name": "T-Shirt",
      "quantity": 1,
      "unit": "",
      "employee_id": "1234",
      "description": "",
      "hsn_code": "",
      "product_code": "",
      "product_uid": "",
      "image_url": "",
      "total_amount": 100000,
      "brand": "",
      "style": "",
      "colour": "",
      "size": "",
      "financier_data": null,
      "taxes": [],
      "tags": [],
      "sub_items": []
    }
  ],
  "receipt_summary": {
    "total_quantity": 1,
    "sub_total_amount": 100000,
    "currency": "INR",
    "net_payable_amount": 124000,
    "additional_charges": [
      {
        "description": "alteration charge",
        "amount": 2000
      },
      {
        "description": "cash on delivery",
        "amount": 2000
      },
    ],
    "payment_status": "paid",
    "discounts": []
  },
  "taxes": [
    {
      "name": "cgst",
      "percentage": 1200,
      "amount": 120
    },
    {
      "name": "sgst",
      "percentage": 1200,
      "amount": 120
    }
  ],
  "payments": [
    {
      "method": "Bank Transfer",
      "currency": "INR",
      "amount": 124000,
      "payment_reference_id": "",
      "financier_data": null
    }
  ],
  "event": {
    "name": "My Party",
    "start_timestamp": 1722911400,
    "end_timestamp": 1722924000,
    "location": "B-wing",
    "room": "Auditorium 1",
    "seats": [
      "gold b1",
      "gold b2",
      "gold b3"
    ]
  },
  "receipt_url": "yourbill.me/PYy4RWJWiNcPyE",
  "created_at": 1907416999,
  "tags": [
    "party1",
    "graduation"
  ]
}
```

## Path Parameters

**id** `string` *required*

The unique identifier of the Bill.

## Request Parameters

**store\_code** `string` *required*

Associated store code for the receipt. Required if you have a multi-store setup where you have a single integration and have multiple stores under you.

**customer** `object` *required*

Details of the customer. Required if receipt mode is `digital` or `digital_and_print`.

**contact** `string` *required*

The customer's phone number. Required if receipt mode is `digital` or `digital_and_print` and `email` is not present.

**name** `string`

The customer's name.

**email** `string` *required*

The customer's email address. Required if receipt mode is `digital` or `digital_and_print` and `contact` is not present.

**customer\_id** `string`

The customer's customer\_id. Required if receipt mode is `digital` or `digital_and_print` and neither `contact` nor `email` is present.

**age** `integer`

Age of the customer.

**date\_of\_birth** `string`

Customer's date of birth.

**pan** `string`

PAN number of the billed customer.

**profession** `string`

Customer's current job profile name.

**company\_name** `string`

Customer current employer.

**marital\_status** `string`

Customer's marital status. Possible values:

* `married`
* `unmarried`

**spouse\_name** `string`

Name of customer's spouse.

**anniversary\_date** `string`

Customer's date of anniversary.

**gender** `string`

Customer gender. Possible values:

* `male`
* `female`
* `other`

**gstin** `string`

Customer's GST number.

**billing\_address** `object` *required*

Customer's billing address. Required if your `business_type` is `ecommerce`.

**address\_line\_1** `string`

Customer billing address line 1.

**address\_line\_2** `string`

Customer billing address line 2.

**landmark** `string`

Customer billing address landmark.

**city** `string`

Customer billing address city.

**province** `string`

Customer billing address province.

**pin\_code** `string`

Customer billing address PIN code.

**country** `string`

Customer billing address country.

**shipping\_address** `object` *required*

Customer's billing address. Required if your `business_type` is `ecommerce`.

**customer\_name** `string`

Name of the recipient.

**contact** `string`

The mobile number of the recipient.

**gstin** `string`

GST number of the recipient.

**pan** `string`

PAN number of the recipient.

**address\_line\_1** `string`

Customer shipping address line 1.

**address\_line\_2** `string`

Customer shipping address line 2.

**landmark** `string`

Customer shipping address landmark.

**city** `string`

Customer shipping address city.

**province** `string`

Customer shipping address province.

**pin\_code** `string`

Customer shipping address PIN code.

**country** `string`

Customer shipping address country.

**employee** `object`

This is an array of objects containing details of the employees associated with the receipt.

**id** `string`

Employee ID/code. Unique identifier of the employee.

**name** `string`

Name of the employee.

**role** `string`

Employee designation/role.

**loyalty** `object` *required*

Customer loyalty details.

**type** `string`

Customer loyalty type.

**card\_num** `string`

Hashed debit/credit card number provided by the customer.

**card\_holder\_name** `string`

Name of the card holder.

**wallet\_amount** `integer`

Wallet amount after used rewards of the customer.

**amount\_saved** `integer`

Amount saved by the customer.

**points\_earned** `integer`

Points earned by the customer after a transaction.

**points\_redeemed** `integer`

Points redeemed by the customer on a transaction.

**points\_available** `integer`

Points available to the customer at the beginning of the transaction.

**points\_balance** `integer`

Points available to the customer at the end of the transaction.

**receipt\_type** `string` *required*

The type of receipt. Possible values:

* `tax_invoice`
* `sales_invoice`
* `sales_return_invoice`
* `proforma_invoice`
* `credit_invoice`
* `purchase_invoice`
* `debit_invoice`

**receipt\_timestamp** `integer` *required*

UNIX timestamp of the date and time when the receipt was generated.

**receipt\_delivery** `string` *required*

Indicates the delivery type of the receipt. Possible values:

* `digital`
* `print`
* `digital_and_print`

**tags** `string`

An array of strings representing relevant tags associated with the invoice.

**pos\_category** `string`

The type of POS machine. This is applicable if `business_type` is `retail`. Possible values:

* `traditional_pos`
* `kiosk_pos`

**line\_items** `object` *required*

This is an array of objects containing the product data of the bill. Required if `receipt_type` is not `credit_invoice` or `debit_invoice`.

**name** `string` *required*

Name of the product.

**quantity** `float` *required*

Quantity of the product.

**unit\_amount** `integer`

Price of the product.

**unit** `string`

Type of unit. Possible values:

* `kg`
* `g`
* `mg`
* `lt`
* `ml`
* `pc`
* `cm`
* `m`
* `in`
* `ft`
* `set`

**gross\_weight** `float`

The total weight of the item, including all materials such as metal, stones, diamonds, and other embellishments.

**net\_weight** `float`

The weight of only the metal used in the item, excluding the weight of any diamonds, stones, or other materials.

**description** `string`

Product/Item description.

**hsn\_code** `string`

HSN code of the product.

**product\_code** `string`

Product/Item code.

**product\_uid** `string`

Product/Item UID/SKU Code.

**image\_url** `string`

Image URL of the product.

**total\_amount** `integer` *required*

Total amount of the product.

**brand** `string`

Brand name of the product.

**style** `string`

Product style.

**colour** `string`

Colour of the product.

**size** `string`

Size of the product in `cm`.

**tags** `string`

An array of strings representing relevant tags associated with the item.

**employee\_id** `string`

Unique ID of the employee who sold the product.

**additional\_charges** `object`

This is an array of objects containing details of the additional charges of the item.

**description** `string`

Description of the additional charge.

**amount** `integer`

Amount of additional charge.

**percent** `float`

Percent calculated on total amount.

**sub\_items** `object` *required*

An array of objects containing the sub-item details of the item.

**name** `string` *required*

Name of the sub-item.

**quantity** `integer` *required*

Sub-item quantity.

**unit\_amount** `integer`

Price of the sub-item.

**unit** `string`

Type of unit. Possible values:

* `kg`
* `g`
* `mg`
* `lt`
* `ml`
* `pc`
* `cm`
* `m`
* `in`
* `ft`
* `set`

**gross\_weight** `float`

The total weight of the item, including all materials such as metal, stones, diamonds, and other embellishments.

**net\_weight** `float`

The weight of only the metal used in the item, excluding the weight of any diamonds, stones, or other materials.

**description** `string`

Sub-item description.

**hsn\_code** `string`

HSN code of the product.

**product\_code** `string`

Sub-item code.

**product\_uid** `string`

Sub-item UID/SKU Code.

**image\_url** `string`

Image URL of the sub-item.

**total\_amount** `integer` *required*

Total amount of the sub-item.

**brand** `string`

Brand name of the sub-item.

**style** `string`

Sub-item style.

**colour** `string`

Colour of the sub-item.

**size** `string`

Size of the sub-item in `cm`.

**tags** `string`

An array of strings representing relevant tags associated with the sub-item.

**employee\_id** `string`

Unique ID of the employee who sold the product.

**additional\_charges** `object`

This is an array of objects containing details of the additional charges of the item.

**description** `string`

Description of the additional charge.

**amount** `integer`

Amount of additional charge.

**percent** `float`

Percent calculated on total amount.

**taxes** `object`

This is an array of objects containing the details of the taxes incurred.

**name** `string` *required*

Name of the tax. For example, CGST, SGST and so on.

**percentage** `float`

Percentage of tax.

**amount** `integer` *required*

Applicable tax calculated on total amount.

**financier\_data** `object`

Data of the financier. This is applicable if the product is financed. For example, if the product is purchased on EMI.

**reference** `string`

Unique id of the financier.

**name** `string`

Name of the financier.

**taxes** `object`

This is an array of objects containing the details of the taxes incurred.

**name** `string` *required*

Name of the tax. For example, CGST, SGST and so on.

**percentage** `float`

Percentage of tax.

**amount** `integer` *required*

Applicable tax calculated on total amount.

**receipt\_summary** `object` *required*

Details of the receipt.

**total\_quantity** `integer` *required*

Total product quantity sold in the invoice.

**sub\_total\_amount** `integer`

The total amount before taxes, discounts and additional fees are added to the invoice.

**currency** `string` *required*

The currency of the invoice. Refer to this [sheet](https://razorpay.com/docs/build/browser/assets/images/bills-supported-currency-list.xlsx) for the list of supported currencies.

**total\_tax\_amount** `integer`

Total tax amount in paise.

**total\_tax\_percent** `float`

Total tax percentage applied on the receipt.

**net\_payable\_amount** `integer` *required*

The total amount payable after adding taxes, discounts and additional fees to the invoice.

**additional\_charges** `object`

This is an array of objects containing the details of any additional charges applied on the invoice. If `additional_charges` is present, then `description` and `amount` are required.

**description** `string`

Description of the additional charge.

**amount** `integer`

Amount of the additional charge.

**percent** `float`

Percent calculated on total amount.

**payment\_status** `string`

Status of the payment. Possible values:

* `pending`
* `authorized`
* `failed`
* `declined`
* `refunded`
* `cancelled`
* `processed`
* `settled`
* `voided`
* `success`
* `paid`
* `unpaid`

**change\_amount** `integer`

Change amount to be returned to the customer if the payment was made in cash.

**roundup\_amount** `integer`

Change amount to be returned to the customer if the payment was made in cash.

**total\_discount\_percent** `float`

Total percentage of the discount on the sub-total amount without the taxes.

**total\_discount\_amount** `integer`

Total value of the discount on the invoice.

**discounts** `object`

This is an array of objects containing the details of the discount. If product reference (`product_code`, `product_uid`, or `hsn_code`) is present in the object, then the discount will be on the item. If not, the discount will be on the invoice.

**name** `string`

Name of the discount.

**amount** `string`

Amount of the applied discount.

**percent** `integer`

Percentile value of the discounted amount.

**product\_code** `string`

Product/Item code.

**product\_uid** `string`

Product/Item UID/SKU Code.

**hsn\_code** `string`

HSN code of the product.

**reference\_id** `string`

Reference ID of the discount.

**used\_wallet\_amount** `string`

Amount used from the customer's wallet for this transaction.

**taxes** `object`

This is an array of objects containing the details of the taxes incurred.

**name** `string` *required*

Name of the tax. For example, CGST, SGST and so on.

**percentage** `float`

Percentage of tax.

**amount** `integer` *required*

Applicable tax calculated on total amount.

**payments** `object` *required*

This is an array of objects containing the details of the payment.

**method** `string` *required*

The mode of payment.

**currency** `string` *required*

The currency in which the payment was made.

**amount** `integer` *required*

The amount of the payment in paise. For example, if the amount is `1200`. The unit will be `120000`.

**irn** `object`

This object contains IRN ( Invoice Reference Number ) related details. If `irn` is present,
qr\_code and irn\_number are required.

**acknowledgement\_number** `string`

Acknowledgement number of the generated IRN.

**acknowledgement\_date** `integer`

Acknowledgement date of the generated IRN.

**qr\_code** `string` *required*

QR code associated with the IRN. Required if `irn` is present.

**irn\_number** `string` *required*

E-invoice IRN. Required if IRN is present.

## Response Parameters

**id** `string` *required*

Unique id of the bill generated.

**business\_type** `string` *required*

The type of business. Possible values:

* `ecommerce`
* `retail`

**business\_category** `string` *required*

The category the business falls under. Possible values:

* `events`
* `food_and_beverages`
* `retail_and_consumer_goods`
* `other_services`

**customer** `object` *required*

Details of the customer. Required if receipt mode is `digital` or `digital_and_print`.

**contact** `string` *required*

The customer's phone number. Required if receipt mode is `digital` or `digital_and_print` and `email` is not present.

**name** `string`

The customer's name.

**email** `string` *required*

The customer's email address. Required if receipt mode is `digital` or `digital_and_print` & `contact` not present.

**customer\_id** `string`

The customer's customer\_id. Required if receipt mode is `digital` or `digital_and_print` and neither `contact` nor `email` is present.

**age** `integer`

Age of the customer.

**date\_of\_birth** `string`

Customer's date of birth.

**profession** `string`

Customer's current job profile name.

**company\_name** `string`

Customer current employer.

**date\_of\_birth** `string`

Customer's date of birth.

**marital\_status** `string`

Customer's marital status. Possible values:

* `married`
* `unmarried`

**spouse\_name** `string`

Name of customer's spouse.

**anniversary\_date** `string`

Customer's date of anniversary.

**gender** `string`

Customer gender. Possible values:

* `male`
* `female`
* `other`

**gstin** `string`

Customer's GST number.

**billing\_address** `object` *required*

Customer's billing address. Required if your `business_type` is `ecommerce`.

**address\_line\_1** `string`

Customer billing address line 1.

**address\_line\_2** `string`

Customer billing address line 2.

**landmark** `string`

Customer billing address landmark.

**city** `string`

Customer billing address city.

**province** `string`

Customer billing address province.

**pin\_code** `string`

Customer billing address PIN code.

**country** `string`

Customer billing address country.

**shipping\_address** `object` *required*

Customer's billing address. Required if your `business_type` is `ecommerce`.

**address\_line\_1** `string`

Customer shipping address line 1.

**address\_line\_2** `string`

Customer shipping address line 2.

**landmark** `string`

Customer shipping address landmark.

**city** `string`

Customer shipping address city.

**province** `string`

Customer shipping address province.

**pin\_code** `string`

Customer shipping address PIN code.

**country** `string`

Customer shipping address country.

**loyalty** `object` *required*

Customer loyalty details.

**type** `string`

Customer loyalty type.

**card\_num** `string`

Hashed debit/credit card number provided by the customer.

**card\_holder\_name** `string`

Name of the card holder.

**wallet\_amount** `integer`

Wallet amount after used rewards of the customer.

**amount\_saved** `integer`

Amount saved by the customer.

**points\_earned** `integer`

Points earned by the customer after a transaction.

**points\_redeemed** `integer`

Points redeemed by the customer on a transaction.

**points\_available** `integer`

Points available to the customer at the beginning of the transaction.

**points\_balance** `integer`

Points available to the customer at the end of the transaction.

**store\_code** `string` *required*

Associated store code for the receipt. Required if you have a multi-store setup where you have a single integration and have multiple stores under you.

**receipt\_timestamp** `integer` *required*

UNIX timestamp of the date and time when the receipt was generated.

**receipt\_number** `string` *required*

Unique receipt number generated for the bill.

**receipt\_type** `string` *required*

The type of receipt. Possible values:

* `tax_invoice`
* `sales_invoice`
* `sales_return_invoice`
* `proforma_invoice`
* `credit_invoice`
* `purchase_invoice`
* `debit_invoice`

**receipt\_delivery** `string` *required*

Indicates the delivery type of the receipt. Possible values:

* `digital`
* `print`
* `digital_and_print`

**tags** `string`

An array of strings representing relevant tags associated with the invoice.

**bar\_code\_number** `integer`

Bar code generated after the transaction. This will be displayed on the digital bill only.

**qr\_code\_number** `integer`

QR code generated after the transaction. This will be displayed on the digital bill only.

**billing\_pos\_number** `string`

POS number of the machine that generated the bill. This is applicable if `business_type` is `retail`.

**pos\_category** `string`

The type of POS machine. This is applicable if `business_type` is `retail`. Possible values:

* `traditional_pos`
* `kiosk_pos`

**order\_number** `string`

Incremental order number of the generated bill.

**order\_service\_type** `string`

Order service type of the generated bill. This is applicable if `business_category` is `food_and_beverages`. Possible values:

* `dine_in`
* `take_away`

**delivery\_status\_url** `string`

Order delivery status. This is applicable if `business_type` is `ecommerce`.

**line\_items** `object` *required*

This is an array of objects containing the product data of the bill. Required if `receipt_type` is not `credit_invoice` or `debit_invoice`.

**name** `string` *required*

Name of the product.

**quantity** `float` *required*

Quantity of the product.

**unit\_amount** `integer`

Price of the product.

**employee\_id** `string`

Unique ID of the employee who sold the product.

**unit** `string`

Type of unit. Possible values:

* `kg`
* `g`
* `mg`
* `lt`
* `ml`
* `pc`
* `cm`
* `m`
* `in`
* `ft`
* `set`

**description** `string`

Product/Item description.

**hsn\_code** `string`

HSN code of the product.

**product\_code** `string`

Product/Item code.

**product\_uid** `string`

Product/Item UID/SKU Code.

**image\_url** `string`

Image URL of the product.

**total\_amount** `integer` *required*

Total amount of the product.

**brand** `string`

Brand name of the product.

**style** `string`

Product style.

**colour** `string`

Colour of the product.

**size** `string`

Size of the product in `cm`.

**tags** `string`

An array of strings representing relevant tags associated with the item.

**sub\_items** `object` *required*

An array of objects containing the sub-item details of the item.

**name** `string` *required*

Name of the sub-item.

**quantity** `integer` *required*

Sub-item quantity.

**unit\_amount** `integer`

Price of the sub-item.

**employee\_id** `string`

Unique ID of the employee who sold the product.

**unit** `string`

Type of unit. Possible values:

* `kg`
* `g`
* `mg`
* `lt`
* `ml`
* `pc`
* `cm`
* `m`
* `in`
* `ft`
* `set`

**description** `string`

Sub-item description.

**hsn\_code** `string`

HSN code of the product.

**product\_code** `string`

Sub-item code.

**product\_uid** `string`

Sub-item UID/SKU Code.

**image\_url** `string`

Image URL of the sub-item.

**total\_amount** `integer` *required*

Total amount of the sub-item.

**brand** `string`

Brand name of the sub-item.

**style** `string`

Sub-item style.

**colour** `string`

Colour of the sub-item.

**size** `string`

Size of the sub-item in `cm`.

**tags** `string`

An array of strings representing relevant tags associated with the sub-item.

**taxes** `object`

This is an array of objects containing the details of the taxes incurred.

**name** `string` *required*

Name of the tax. For example, CGST, SGST and so on.

**percentage** `float`

Percentage of tax.

**amount** `integer` *required*

Applicable tax calculated on total amount.

**taxes** `object`

This is an array of objects containing the details of the taxes incurred.

**name** `string` *required*

Name of the tax. For example, CGST, SGST and so on.

**percentage** `float`

Percentage of tax.

**amount** `integer` *required*

Applicable tax calculated on total amount.

**receipt\_summary** `object` *required*

Details of the receipt.

**total\_quantity** `integer` *required*

Total product quantity sold in the invoice.

**sub\_total\_amount** `integer`

The total amount before taxes, discounts and additional fees are added to the invoice.

**currency** `string` *required*

The currency of the invoice. Refer to this [sheet](https://razorpay.com/docs/pos/billme/appendix.md) for the list of supported currencies.

**total\_tax\_amount** `integer`

Total tax amount in paise.

**total\_tax\_percent** `float`

Total tax percentage applied on the receipt.

**net\_payable\_amount** `integer` *required*

The total amount payable after adding taxes, discounts and additional fees to the invoice.

**additional\_charges** `object`

This is an array of objects containing the details of any additional charges applied on the invoice. If `additional_charges` is present, then `description` and `amount` are required.

**description** `string`

Description of the additional charge.

**amount** `integer`

Amount of the additional charge.

**percent** `float`

Percent calculated on total amount.

**payment\_status** `string`

Status of the payment. Possible values:

* `pending`
* `authorized`
* `failed`
* `declined`
* `refunded`
* `cancelled`
* `processed`
* `settled`
* `voided`
* `success`
* `paid`
* `unpaid`

**change\_amount** `integer`

Change amount to be returned to the customer if the payment was made in cash.

**roundup\_amount** `integer`

Change amount to be returned to the customer if the payment was made in cash.

**total\_discount\_percent** `float`

Total percentage of the discount on the sub-total amount without the taxes.

**total\_discount\_amount** `integer`

Total value of the discount on the invoice.

**discounts** `object`

This is an array of objects containing the details of the discount.

**name** `string`

Name of the discount.

**amount** `string`

Amount of the applied discount.

**percent** `integer`

Percentile value of the discounted amount.

**used\_wallet\_amount** `string`

Amount used from the customer's wallet for this transaction.

**taxes** `object` *required*

This is an array of objects containing the details of the taxes applied. Required if `receipt_type` is `tax_inovice`, `purchase_invoice` or `sales_invoice`.

**name** `string` *required*

Name of the tax. For example, CGST, SGST and so on.

**percentage** `float`

Percentage of tax.

**amount** `integer` *required*

Applicable tax calculated on total amount.

**payments** `object` *required*

Details of the payment.

**method** `string` *required*

The mode of payment.

**currency** `string` *required*

The currency in which the payment was made.

**amount** `integer` *required*

The amount of the payment in paise. For example, if the amount is `1200`. The unit will be `120000`.

**payment\_reference\_id** `string`

The Unique id of the payment method.

**financier\_data** `object`

Details of the financier.

**reference** `string`

Unique id of the financier.

**name** `string`

Name of the financier.

**event** `object` *required*

Details of the event booking. Required if `business_category` is `events`.

**name** `string` *required*

Name of the event.

**start\_timestamp** `integer`

The exact time in seconds when the event starts.

**end\_timestamp** `integer`

The exact time in seconds when the event ends.

**location** `string`

The location/venue of the event.

**room** `string`

The specific room where the event was held.

**seats** `string`

The number of seats booked for the event.

**receipt\_url** `string`

The link to the receipt.

**created\_at** `integer`

UNIX timestamp of the date when the bill was generated.

## Errors

> [accordion] client not authorised to update
>
> **Code:** `401`
>
> The client credentials are unauthorised to make changes to this bill.
>
> **Solution:** Use authorised credentials to make changes to the bill.

> [accordion] The quantity must be an integer
>
> **Code:** `400`
>
> The quantity of the product was not written in integer format.
>
> **Solution:** Write the quantity in integer format.

> [accordion] Operation failed
>
> **Code:** `400`
>
> There is an internal server error.
>
> **Solution:** There is a server issue. Raise a support ticket with us to get this resolved.

> [accordion] Bill not found for given receipt\_number
>
> **Code:** `400`
>
> The bill id is incorrect or deleted.
>
> **Solution:** Add the correct bill id.
