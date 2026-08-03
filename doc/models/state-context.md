
# State Context

Additional context specific to the current dispute state. Required in all states, with different schemas depending on the state.

*This model accepts additional fields of type Any.*

## Structure

`StateContext`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `representment` | [`PaymentDisputeRepresentment`](../../doc/models/payment-dispute-representment.md) | Required | Representment details for the current dispute |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.attachment import Attachment
from klarna.models.partner_evidence import PartnerEvidence
from klarna.models.payment_dispute_representment import PaymentDisputeRepresentment
from klarna.models.payment_dispute_representment_previous_state import PaymentDisputeRepresentmentPreviousState
from klarna.models.payment_dispute_representment_request import PaymentDisputeRepresentmentRequest
from klarna.models.payment_dispute_representment_state import PaymentDisputeRepresentmentState
from klarna.models.state_context import StateContext

state_context = StateContext(
    representment=PaymentDisputeRepresentment(
        state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
        previous_state=PaymentDisputeRepresentmentPreviousState.EVIDENCE_REQUESTED,
        expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
        request=PaymentDisputeRepresentmentRequest(
            additional_information='additional_information6',
            requested_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z')
        ),
        partner_evidence=PartnerEvidence(
            created_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            attachments=[
                Attachment(
                    payment_dispute_attachment_id='payment_dispute_attachment_id2',
                    description='description0',
                    mime_type='mime_type4',
                    url='url4'
                )
            ],
            additional_information='additional_information8'
        ),
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

