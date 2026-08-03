
# Payment Dispute Evidence Request Response

Partner response to the dispute with file evidence only. Simplified evidence submission - partner can upload one or more files.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeEvidenceRequestResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `attachments` | [`List[PaymentDisputeAttachment]`](../../doc/models/payment-dispute-attachment.md) | Required | List of evidence files provided by the partner to support the dispute response.<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `10` |
| `created_at` | `datetime` | Required | Timestamp of when the response was submitted |
| `additional_information` | `str` | Optional | The free text provided alongside the attachments when responding to the representment request.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `5000` |
| `state` | [`State5`](../../doc/models/state-5.md) | Required | The new state of the dispute after submitting the response. The dispute transitions to REPRESENTMENT state for Klarna review. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.payment_dispute_attachment import PaymentDisputeAttachment
from klarna.models.payment_dispute_evidence_request_response import PaymentDisputeEvidenceRequestResponse
from klarna.models.state_5 import State5

payment_dispute_evidence_request_response = PaymentDisputeEvidenceRequestResponse(
    attachments=[
        PaymentDisputeAttachment(
            payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
            description='Shipment confirmation'
        )
    ],
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    state=State5.ARBITRATION,
    additional_information='additional_information2',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

