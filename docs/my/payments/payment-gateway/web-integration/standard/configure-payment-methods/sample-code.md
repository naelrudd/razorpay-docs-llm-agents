> ## Documentation Index
> Fetch the complete documentation index at: https://razorpay.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Sample Codes

> Sample codes to help you integrate the payment methods of your choice on Razorpay Curlec Checkout.

Available in
🇮🇳 India
🇲🇾 Malaysia
🇸🇬 Singapore

If you want to list all the payment methods offered by `RHB` bank, allow card payments for `Am` bank only and hide `wallet` payment method from the Checkout, you can do so as follows: (Change in code accordingly)

```html Checkout Code theme={null}
<html>
<button id="rzp-button1" class="btn btn-outline-dark btn-lg"><i class="fas fa-money-bill"></i> Own Checkout</button>
<script src="https://checkout.razorpay.com/v1/checkout.js"></script>
<script>
  var options = {
    "key": "[YOUR_KEY_ID]", // Enter the Key ID generated from the Dashboard
    "amount": "1000",
    "currency": "MYR",
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
          rhb: { //name for RHB block
            name: "Pay Using RHB Bank",
            instruments: [
              {
                method: "card",
                issuers: ["RHB"]
              },
            ]
          },
          other: { //  name for other block
            name: "Other Payment Methods",
            instruments: [
              {
                method: "card",
                issuers: ["Am"]
              }
            ]
          }
        },
        hide: [
          {
          method: "wallet"
          }
        ],
        sequence: ["block.rhb", "block.other"],
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
> You can use the payment methods enabled for your account on the Dashboard. Also, you can raise a request with   our [Support Team](https://curlec.com/support/)  for additional payment methods or providers.

## Show Grab Pay Separately on Checkout

Use the code given below to show Grab Pay separately on Checkout:

```javascript Grab Pay theme={null}
config: {
    display: {
      blocks: {
        banks: {
          name: 'Methods With Offers',
          instruments: [
            {
              method: 'wallet',
              wallets: ['grabpay']
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
              method: 'wallet',
              wallets: ['grabpay']
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
              method: 'fpx',
              banks: ['HSBC'],
            },
            {
              method: 'card',
              issuers: ['HSBC'],
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
              method: 'fpx',
              banks: ['HSBC'],
            },
            {
              method: 'card',
              issuers: ['HSBC'],
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
                method: 'wallet'
            },
            {
                method: 'fpx'
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
        banks: {
          name: 'Pay via Card',
          instruments: [
            {
              method: 'card'
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

### Related Information

* [Supported Methods](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods/supported-methods.md)
* [Configurability of Payment Methods](https://razorpay.com/docs/my/payments/payment-gateway/web-integration/standard/configure-payment-methods.md)
