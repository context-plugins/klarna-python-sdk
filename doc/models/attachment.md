
# Attachment

Attachment

## Structure

`Attachment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_attachment_id` | `str` | Required | Unique identifier for the payment dispute attachment<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `description` | `str` | Optional | Optional description of the attachment<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `500` |
| `mime_type` | `str` | Optional | The MIME type of the attachment.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `url` | `str` | Optional | The URL to download the attachment.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2000` |

## Example

```python
from klarna.models.attachment import Attachment

attachment = Attachment(
    payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
    description='Shipment confirmation',
    mime_type='image/jpeg',
    url='/payment/disputes/krn:network:us1:live:payment:dispute:1234567890/attachments/1/download'
)
```

