
# Payment Dispute State

The current state of the Dispute.

* `INITIATED` - Dispute initiated. Klarna reviews case details and may request Partner response within deadline.
* `REPRESENTMENT` - Evidence review phase. Partner has submitted evidence and Klarna is reviewing the representment case.
* `PRE_ARBITRATION` - Pre-arbitration phase. Preliminary decision made. Partner has opportunity to accept or challenge the preliminary decision.
* `ARBITRATION` - Arbitration phase. Final review by Klarna. Binding decision will be made.
* `CLOSED` - Dispute is closed. Check `dispute_outcome` and `dispute_outcome_detailed` for further information.

## Enumeration

`PaymentDisputeState`

## Fields

| Name |
|  --- |
| `INITIATED` |
| `REPRESENTMENT` |
| `PRE_ARBITRATION` |
| `ARBITRATION` |
| `CLOSED` |

## Example

```python
from klarna.models.payment_dispute_state import PaymentDisputeState

payment_dispute_state = PaymentDisputeState.CLOSED
```

