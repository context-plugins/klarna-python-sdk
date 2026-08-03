
# Payment Dispute Respond to Evidence Request Payload

Partner response to the dispute with file evidence. Partner can upload one or more files as evidence, and optionally offer a partial loss acceptance amount.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeRespondToEvidenceRequestPayload`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `attachments` | [`List[PaymentDisputeAttachment]`](../../doc/models/payment-dispute-attachment.md) | Required | List of evidence files provided by the partner to support the dispute response. Partner can upload one or more files.<br><br>**Constraints**: *Minimum Items*: `1` |
| `additional_information` | `str` | Optional | Any free text you wish to provide alongside your attachments when responding to a representment request. Klarna will review this information alongside your attachments when evaluating your representment case.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `5000` |
| `partner_proposed_refund_amount` | `int` | Optional | The amount, in minor currency units, that the partner proposes to refund instead of the whole dispute amount. This is in the settlement currency. Must be less than the full disputed amount. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.payment_dispute_attachment import PaymentDisputeAttachment
from klarna.models.payment_dispute_respond_to_evidence_request_payload import PaymentDisputeRespondToEvidenceRequestPayload

payment_dispute_respond_to_evidence_request_payload = PaymentDisputeRespondToEvidenceRequestPayload(
    attachments=[
        PaymentDisputeAttachment(
            payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
            description='Shipment confirmation'
        )
    ],
    additional_information='Please review the highlighted section in the attached proof of delivery document, which shows the customer signature confirming receipt of the goods.',
    partner_proposed_refund_amount=9700,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

