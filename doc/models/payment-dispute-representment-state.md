
# Payment Dispute Representment State

The current state of the Dispute Evidence Request.

* `EVIDENCE_REQUESTED` - Partner can reply to the request.
* `EVIDENCE_RECEIVED` - Evidence is being reviewed by Klarna, it's not possible to reply to the request.
* `EVIDENCE_REQUEST_EXPIRED` - Request time expired, it's not possible to reply to the request. The dispute will result in outcome LOST if partner does not respond before the deadline.
* `EVIDENCE_WAIVED` - Partner accepted the dispute loss in INITIATED state using the accept-loss endpoint. No further action possible.
* `REPRESENTMENT_AUTOMATICALLY_REJECTED` - Dispute representment automatically rejected because the dispute amount falls below the partner's configured threshold. Disputes below this threshold are automatically accepted as LOST. No further action possible.

## Enumeration

`PaymentDisputeRepresentmentState`

## Fields

| Name |
|  --- |
| `EVIDENCE_REQUESTED` |
| `EVIDENCE_RECEIVED` |
| `EVIDENCE_REQUEST_EXPIRED` |
| `EVIDENCE_WAIVED` |
| `REPRESENTMENT_AUTOMATICALLY_REJECTED` |

## Example

```python
from klarna.models.payment_dispute_representment_state import PaymentDisputeRepresentmentState

payment_dispute_representment_state = PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED
```

