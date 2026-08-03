
# Payment Dispute Arbitration Request

Captures the Partner's appeal against a preliminary arbitration decision, including the written explanation and any supporting evidence files.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeArbitrationRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `requested_at` | `datetime` | Required | Timestamp of when the arbitration request was created |
| `additional_information` | `str` | Required | Free-text explanation of why the preliminary decision is considered incorrect. Klarna will review this when reconsidering the dispute during the arbitration phase.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `10000` |
| `attachments` | [`List[PaymentDisputeArbitrationRequestAttachment]`](../../doc/models/payment-dispute-arbitration-request-attachment.md) | Optional | Evidence files provided by the Partner to support the appeal.<br><br>**Constraints**: *Minimum Items*: `1` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.payment_dispute_arbitration_request import PaymentDisputeArbitrationRequest
from klarna.models.payment_dispute_arbitration_request_attachment import PaymentDisputeArbitrationRequestAttachment

payment_dispute_arbitration_request = PaymentDisputeArbitrationRequest(
    requested_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    additional_information='additional_information0',
    attachments=[
        PaymentDisputeArbitrationRequestAttachment(
            payment_dispute_attachment_id='payment_dispute_attachment_id2',
            description='description0',
            mime_type='mime_type4',
            url='url4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        PaymentDisputeArbitrationRequestAttachment(
            payment_dispute_attachment_id='payment_dispute_attachment_id2',
            description='description0',
            mime_type='mime_type4',
            url='url4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

