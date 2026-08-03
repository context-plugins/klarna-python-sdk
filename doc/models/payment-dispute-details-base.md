
# Payment Dispute Details Base

Core dispute information including the disputed amount, transaction currency, and the party who initiated the dispute.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeDetailsBase`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `dispute_amount` | `int` | Required | The amount being disputed, in minor currency units. This is in the settlement currency. |
| `currency` | `str` | Required | The currency of the disputed transaction.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{3}$` |
| `created_by` | [`CreatedBy`](../../doc/models/created-by.md) | Required | The entity that created the dispute.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.created_by import CreatedBy
from klarna.models.payment_dispute_details_base import PaymentDisputeDetailsBase

payment_dispute_details_base = PaymentDisputeDetailsBase(
    dispute_amount=160,
    currency='USD',
    created_by=CreatedBy.CUSTOMER,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

