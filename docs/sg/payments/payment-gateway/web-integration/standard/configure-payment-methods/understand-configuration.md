> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Understand the Configuration

> Understand the building blocks that are required to build a configuration of your choice.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

Let us understand the building blocks that are required to build a configuration of your choice:

1. [Payment Methods](#payment-methods)
2. [Payment Instruments](#payment-instruments)
3. [Blocks](#blocks)
4. [Sequence](#sequence)
5. [Preferences](#preferences)

## Payment Methods

Before deciding the payment methods or payment instruments that you want to configure on the Checkout, refer to the [payment methods](https://razorpay.com/docs/sg/payments/payment-methods) supported by Razorpay.

## Payment Instruments

A payment instrument is a combination of the payment method and its associated properties. For example, a payment instrument can be an **HBSC Debit card**, where **card** is the payment method and the issuer (HBSC bank) is the associated **instrument**.

An instrument is a JSON object with a key named `method`. Each method and its associated properties are described in the sections below:

### Card

Payment instruments for the `method: card` are listed below:

| Name | Type | Description | Values | Examples |
| - | - | - | - | - |
| issuers | array | List of issuers that are allowed | Any bank code | `issuers: ["HBSC", "DBS"]` |
| networks | array | List networks that are allowed | Any card network | `networks: ["Visa", "MasterCard"]` |
| types | array | List of card types that are allowed | Any card type | `types: ["credit", "debit"]` |

```javascript JavaScript theme={null}
// beginning of the code
....
card: { \\name for cards
    name: "Pay Via Cards"
    instruments: [
      {
        method: "card",
        issuers: ["HSBC"],
        networks: ["MasterCard"],
        types: ["debit","credit"]
      }
    ]
},
...
//rest of the code
```

### PayNow

Payment instruments for the `method: paynow` are listed below:

| Name | Type | Description | Values | Examples |
| - | - | - | - | - |
| banks | array`<string>` | List of all banks that are allowed | Any bank code | `banks: ["HSBC", "DBC"]` |

## Blocks

A block is a collection of one or more payment instruments. Each block has a `name` and `code` associated as shown below:

```javascript JavaScript theme={null}
// Block creation
let myPayments = {
  name: "My Custom Block",
  instruments: ["grabpay", "paypal"]
};
// Usage in config
let config = {
  display: {
    blocks: {
      highlighted: myPayments
    }
  }
};
```

Here, `highlighted` is the code associated with `myPayments`. Multiple blocks can be added to the config at the same time.

## Sequence

You can specify the `sequence`, that is the order, in which the payment methods should be displayed on the Checkout.

A sequence is an `array` of strings, where each string is the name of the payment method or a `block`.

In a sequence, you can include any block using the `block.${code}` format. The block with code **highlighted** should be represented as `block.highlighted` as shown below:

```javascript JavaScript theme={null}
let sequence = ["block.highlighted", "paynow"];
```

The above sequence will place the code `highlighted` first followed by the payment method `paynow` in that particular order.

> [!NOTE]
>
> **Handy Tips**
>
> Every block defined has to be present in the sequence. If you do not wish to reorder the methods and want to place your block, the sequence should contain `block.highlighted` with just one item in it.

## Preferences

Using the `preferences` object, you can enhance the configuration of the Checkout. By setting this value, you can decide whether the default list of payment methods should be displayed or not.

Possible values are:

`true`
: Checkout will display the sequence of the payment methods configured by you alongside with the default order of payment methods available in the Checkout.

`false`
: Checkout will only show the sequence of the payment methods configured by you.

## Hide Payment Instruments

You can also hide or remove certain instruments from the Checkout.

This is an `array` containing the `method` key used to hide either the payment method and/or the payment instrument associated with that payment method. For example, you can hide the methods, `card` and `paynow` on the Checkout.

```javascript JavaScript theme={null}
let cardInstrument = {
  method: "card"
};

let instrumentOfSomeBank = {
  method: "paynow",
  banks: ["HSBC"]
};

let hiddenInstruments = [cardInstrument, instrumentOfSomeBank];
```

> [!NOTE]
>
> **Handy Tips**
>
> Hiding any instrument using `hide` does not affect the similar instrument defined in `blocks`. So, if you want to hide `HSBC` bank from `paynow` and have defined the same instrument in one of your blocks, HSBC bank will still be displayed in that block.

## Next Steps

[Display the Configuration](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods/display-configuration.md)

### Related Information

* [Supported Methods](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods/supported-methods.md)
* [Sample Codes](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods/sample-code.md)
