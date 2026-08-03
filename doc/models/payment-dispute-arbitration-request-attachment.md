
# Payment Dispute Arbitration Request Attachment

Attachment linked to an arbitration request.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeArbitrationRequestAttachment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_attachment_id` | `str` | Required | Unique identifier for the payment dispute attachment<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `description` | `str` | Optional | Optional description of the attachment.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1000` |
| `mime_type` | `str` | Optional | The MIME type of the attachment.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `url` | `str` | Optional | The URL to download the attachment.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2000` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.payment_dispute_arbitration_request_attachment import PaymentDisputeArbitrationRequestAttachment

payment_dispute_arbitration_request_attachment = PaymentDisputeArbitrationRequestAttachment(
    payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
    description='Shipment confirmation',
    mime_type='image/jpeg',
    url='/payment/disputes/krn:network:us1:live:payment:dispute:1234567890/attachments/1/download',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

