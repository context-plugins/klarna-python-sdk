
# Payment Dispute Customer Attachment

Attachment

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeCustomerAttachment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `description` | `str` | Optional | Optional description of the attachment<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `500` |
| `mime_type` | `str` | Optional | The MIME type of the attachment.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `url` | `str` | Optional | The URL to download the attachment.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2000` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.payment_dispute_customer_attachment import PaymentDisputeCustomerAttachment

payment_dispute_customer_attachment = PaymentDisputeCustomerAttachment(
    description='Shipment confirmation',
    mime_type='image/jpeg',
    url='/payment/disputes/krn:network:us1:live:payment:dispute:1234567890/customer-claim/attachments/1/download',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

