
# Payment Dispute Appeal Response

Response after submitting an appeal for a preliminary dispute decision.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeAppealResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `state` | [`State6`](../../doc/models/state-6.md) | Required | The new state of the dispute after submitting the appeal. The dispute transitions to ARBITRATION state for Klarna review. |
| `created_at` | `datetime` | Required | Timestamp of when the appeal was submitted |
| `additional_information` | `str` | Optional | The explanation provided for the appeal<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `10000` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.payment_dispute_appeal_response import PaymentDisputeAppealResponse
from klarna.models.state_6 import State6

payment_dispute_appeal_response = PaymentDisputeAppealResponse(
    state=State6.PRE_ARBITRATION,
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    additional_information='additional_information6',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

