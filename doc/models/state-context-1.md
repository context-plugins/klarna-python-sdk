
# State Context 1

Additional context specific to the current dispute state. Required in all states, with different schemas depending on the state.

*This model accepts additional fields of type Any.*

## Structure

`StateContext1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `partner_evidence` | [`PaymentDisputePartnerEvidence`](../../doc/models/payment-dispute-partner-evidence.md) | Required | Partner representment responses |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.attachment import Attachment
from klarna.models.payment_dispute_partner_evidence import PaymentDisputePartnerEvidence
from klarna.models.state_context_1 import StateContext1

state_context_1 = StateContext1(
    partner_evidence=PaymentDisputePartnerEvidence(
        created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
        attachments=[
            Attachment(
                payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
                description='Shipment confirmation',
                mime_type='image/jpeg',
                url='/payment/disputes/krn:network:us1:live:payment:dispute:1234567890/attachments/1/download'
            )
        ],
        additional_information='additional_information8'
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

