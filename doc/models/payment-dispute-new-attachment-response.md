
# Payment Dispute New Attachment Response

New file attachment upload response

## Structure

`PaymentDisputeNewAttachmentResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_attachment_id` | `str` | Required | Unique attachment identifier obtained after uploading of an attachment<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Example

```python
from klarna.models.payment_dispute_new_attachment_response import PaymentDisputeNewAttachmentResponse

payment_dispute_new_attachment_response = PaymentDisputeNewAttachmentResponse(
    payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:3'
)
```

