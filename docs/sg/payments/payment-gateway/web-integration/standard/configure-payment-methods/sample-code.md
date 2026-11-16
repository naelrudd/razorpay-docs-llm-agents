> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Sample Codes

> Sample codes to help you integrate the payment methods of your choice on Razorpay Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

If you want to list all the payment methods offered by `HSBC` bank and hide `paynow` payment method from the Checkout, you can do so as follows: (Change in code accordingly)

```html Checkout Code theme={null}
<html>
<button id="rzp-button1" class="btn btn-outline-dark btn-lg"><i class="fas fa-money-bill"></i> Own Checkout</button>
<script src="https://checkout.razorpay.com/v1/checkout.js"></script>
<script>
  var options = {
    "key": "[YOUR_KEY_ID]", // Enter the Key ID generated from the Dashboard
    "amount": "1000",
    "currency": "SGD",
    "description": "Acme Corp",
    "image": "https://cdn.razorpay.com/logos/F9Yhfb7ZXjXmIQ_medium.jpg",
    "prefill":
    {
      "email": "<email>",
      "contact": <phone>,
    },
    config: {
      display: {
        blocks: {
          hsbc: { //name for HSBC block
            name: "Pay Using HSBC Bank",
            instruments: [
              {
                method: "card",
                issuers: ["HSBC"]
              },
            ]
          },
        hide: [
          {
          method: "paynow"
          }
        ],
        sequence: ["block.hsbc"],
        preferences: {
          show_default_blocks: false // Should Checkout show its default blocks?
        }
      }
    },
    "handler": function (response) {
      alert(response.razorpay_payment_id);
    },
    "modal": {
      "ondismiss": function () {
        if (confirm("Are you sure, you want to close the form?")) {
          txt = "You pressed OK!";
          console.log("Checkout form closed by the user");
        } else {
          txt = "You pressed Cancel!";
          console.log("Complete the Payment")
        }
      }
    }
  };
  var rzp1 = new Razorpay(options);
  document.getElementById('rzp-button1').onclick = function (e) {
    rzp1.open();
    e.preventDefault();
  }
</script>
</html>
```

> [!WARNING]
>
> **Watch Out!**
>
> You can use the payment methods enabled for your account on the Dashboard. Also, you can raise a request with  our [Support Team](https://razorpay.com/sg/support/)   for additional payment methods or providers.

> [!WARNING]
>
> **UPI Collect Flow Deprecated**
>
> According to NPCI guidelines, the UPI Collect flow is being deprecated effective 28 February 2026. Customers can no longer make payments or register UPI mandates by manually entering VPA/UPI id/mobile numbers.
>
> **Exemptions:** UPI Collect will continue to be supported for:
>
> * MCC 6012 & 6211 (IPO and secondary market transactions).
> * iOS mobile app and mobile web transactions.
> * UPI Mandates (execute/modify/revoke operations only)
> * eRupi vouchers.
> * PACB businesses (cross-border/international payments).
>
> **Action Required:**
>
> * If you are a new Razorpay user, use [UPI Intent](https://razorpay.com/docs/payments/payment-methods/upi/upi-intent.md).
> * If you are an existing Razorpay user not covered by exemptions, you must migrate to UPI Intent or UPI QR code to continue accepting UPI payments. For detailed migration steps, refer to the [migration documentation](https://razorpay.com/docs/announcements/upi-collect-migration/standard-integration).

## Show PayNow Separately on Checkout

Use the code given below to show PayNow separately on Checkout:

```javascript Grab Pay theme={null}
config: {
    display: {
      blocks: {
        banks: {
          name: 'Methods With Offers',
          instruments: [
            {
              method: 'paynow',
              wallets: ['paynow']
            }]
        },
      },
      sequence: ['block.banks'],
      preferences: {
        show_default_blocks: true,
      },
    },
  },
};
```

## Show Most Used Methods

Use the code given below to show the most used methods:

```javascript Most Used Methods theme={null}
config: {
    display: {
      blocks: {
        banks: {
          name: 'Most Used Methods',
          instruments: [
            {
              method: 'paynow'
            },
            {
                method: 'card'
            },
            ],
        },
      },
      sequence: ['block.banks'],
      preferences: {
        show_default_blocks: true,
      },
    },
  },
};
```

## Show Instruments of a Certain Bank Only

Use the code given below to show the instruments of a certain bank only on Checkout:

```javascript Instruments of HSBC Bank Only theme={null}
config: {
    display: {
      blocks: {
        banks: {
          name: 'Pay Using HSBC bank',
          instruments: [
            {
              method: 'card',
              banks: ['HSBC'],
            }
          ],
        },
      },
      sequence: ['block.banks'],
      preferences: {
        show_default_blocks: false,
      },
    },
  },
};
```

## Highlight Instruments of a Certain Bank

Use the code given below to highlight the instruments of a certain bank only on Checkout:

```javascript Highlight Instruments of HSBC Bank theme={null}
config: {
    display: {
      blocks: {
        banks: {
          name: 'Pay Using HSBC Bank',
          instruments: [
            {
              method: 'card',
              banks: ['HSBC'],
            }
          ],
        },
      },
      sequence: ['block.banks'],
      preferences: {
        show_default_blocks: true,
      },
    },
  },
};
```

## Reorder Payment Methods

Use the code given below to reorder payment methods on Checkout:

```javascript Reorder Payment Methods theme={null}
config: {
    display: {
      blocks: {
        banks: {
          name: 'All Payment Options',
          instruments: [
            {
              method: 'card'
            },
            {
                method: 'paynow'
            }
          ],
        },
      },
      sequence: ['block.banks'],
      preferences: {
        show_default_blocks: false,
      },
    },
  },
};
```

## Remove a Method from Checkout

Use the code given below to remove a method from Checkout:

```javascript Wallet Removed from Checkout theme={null}
config: {
    display: {
      hide: [
        {
          method: 'wallet'
        }
      ],
      preferences: {
        show_default_blocks: true,
      },
    },
  },
};
```

## Show Only a Certain Payment Method on Checkout

Use the code given below to show only a certain payment method on Checkout:

### Card

```javascript Land on Card theme={null}
config: {
  display: {
    blocks: {
      cards_only: {
        name: "Pay via Card",
        instruments: [
          {
            method: "card",
          },
        ],
      },
    },
    sequence: ["block.cards_only"],
    preferences: {
      show_default_blocks: false,
      },
    },
  },
};
```

### Related Information

* [Supported Methods](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods/supported-methods.md)
* [Configurability of Payment Methods](https://razorpay.com/docs/sg/payments/payment-gateway/web-integration/standard/configure-payment-methods.md)
