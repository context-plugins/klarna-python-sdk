
# V4 Payment Disputes Appeal Request

*This model accepts additional fields of type Any.*

## Structure

`V4PaymentDisputesAppealRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `additional_information` | `str` | Required | Detailed explanation of why the preliminary decision is considered incorrect. Klarna will review this information when reconsidering the preliminary decision during the arbitration phase.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `10000` |
| `attachments` | [`List[PaymentDisputeAttachment]`](../../doc/models/payment-dispute-attachment.md) | Optional | Optional list of evidence files to support the appeal. Upload files first using the attachment upload endpoint, then reference the returned IDs here.<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `10` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.payment_dispute_attachment import PaymentDisputeAttachment
from klarna.models.v_4_payment_disputes_appeal_request import V4PaymentDisputesAppealRequest

v_4_payment_disputes_appeal_request = V4PaymentDisputesAppealRequest(
    additional_information='We believe the preliminary decision is incorrect because we have proof of delivery with customer signature. The tracking shows the package was delivered and signed for by the customer on the expected date.',
    attachments=[
        PaymentDisputeAttachment(
            payment_dispute_attachment_id='payment_dispute_attachment_id2',
            description='description0'
        ),
        PaymentDisputeAttachment(
            payment_dispute_attachment_id='payment_dispute_attachment_id2',
            description='description0'
        )
    ],
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

