
# Payment Dispute Customer Provided Evidence

## Structure

`PaymentDisputeCustomerProvidedEvidence`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_customer_evidence_id` | `str` | Optional | Unique identifier of the customer evidence<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `attachment` | [`PaymentDisputeCustomerAttachment`](../../doc/models/payment-dispute-customer-attachment.md) | Optional | Attachment |

## Example

```python
import jsonpickle

from klarna.models.payment_dispute_customer_attachment import PaymentDisputeCustomerAttachment
from klarna.models.payment_dispute_customer_provided_evidence import PaymentDisputeCustomerProvidedEvidence

payment_dispute_customer_provided_evidence = PaymentDisputeCustomerProvidedEvidence(
    payment_dispute_customer_evidence_id='krn:network:us1:live:payment:dispute:1234567890:customer-evidence:1',
    attachment=PaymentDisputeCustomerAttachment(
        description='description8',
        mime_type='mime_type2',
        url='url2',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    )
)
```

