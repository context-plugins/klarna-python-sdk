
# V4 Payment Disputes Accept Loss Response

*This model accepts additional fields of type Any.*

## Structure

`V4PaymentDisputesAcceptLossResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `state` | `str` | Required | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.v_4_payment_disputes_accept_loss_response import V4PaymentDisputesAcceptLossResponse

v_4_payment_disputes_accept_loss_response = V4PaymentDisputesAcceptLossResponse(
    state='CLOSED',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

