
# Payment Dispute Previous State

The previous state of the Dispute.

* `INITIATED` - Dispute initiated.
* `REPRESENTMENT` - Evidence review phase.
* `PRE_ARBITRATION` - Pre-arbitration phase with preliminary decision.
* `ARBITRATION` - Arbitration phase with final review by Klarna.

## Enumeration

`PaymentDisputePreviousState`

## Fields

| Name |
|  --- |
| `INITIATED` |
| `REPRESENTMENT` |
| `PRE_ARBITRATION` |
| `ARBITRATION` |

## Example

```python
from klarna.models.payment_dispute_previous_state import PaymentDisputePreviousState

payment_dispute_previous_state = PaymentDisputePreviousState.PRE_ARBITRATION
```

