
# Representment

The representment case details if the dispute has transitioned to representment state.

*This model accepts additional fields of type Any.*

## Structure

`Representment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `state` | [`PaymentDisputeRepresentmentState`](../../doc/models/payment-dispute-representment-state.md) | Required | The current state of the Dispute Evidence Request.<br><br>* `EVIDENCE_REQUESTED` - Partner can reply to the request.<br>* `EVIDENCE_RECEIVED` - Evidence is being reviewed by Klarna, it's not possible to reply to the request.<br>* `EVIDENCE_REQUEST_EXPIRED` - Request time expired, it's not possible to reply to the request. The dispute will result in outcome LOST if partner does not respond before the deadline.<br>* `EVIDENCE_WAIVED` - Partner accepted the dispute loss in INITIATED state using the accept-loss endpoint. No further action possible.<br>* `REPRESENTMENT_AUTOMATICALLY_REJECTED` - Dispute representment automatically rejected because the dispute amount falls below the partner's configured threshold. Disputes below this threshold are automatically accepted as LOST. No further action possible. |
| `expires_at` | `datetime` | Required | Deadline date for a partner to accept or escalate to arbitration |
| `request` | [`PaymentDisputeRepresentmentRequest`](../../doc/models/payment-dispute-representment-request.md) | Required | Request for information towards the associated partner |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.payment_dispute_representment_request import PaymentDisputeRepresentmentRequest
from klarna.models.payment_dispute_representment_state import PaymentDisputeRepresentmentState
from klarna.models.representment import Representment

representment = Representment(
    state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
    expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    request=PaymentDisputeRepresentmentRequest(
        additional_information='additional_information6',
        requested_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

