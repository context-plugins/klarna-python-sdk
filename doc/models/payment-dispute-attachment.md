
# Payment Dispute Attachment

Attachment linked to the dispute

## Structure

`PaymentDisputeAttachment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_attachment_id` | `str` | Required | Unique identifier for the payment dispute attachment<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `description` | `str` | Optional | Optional description of the attachment<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1000` |

## Example

```python
from klarna.models.payment_dispute_attachment import PaymentDisputeAttachment

payment_dispute_attachment = PaymentDisputeAttachment(
    payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
    description='Shipment confirmation'
)
```

