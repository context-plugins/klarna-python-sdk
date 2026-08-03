
# Cancel Order Request Status Cancelled

*This model accepts additional fields of type Any.*

## Structure

`CancelOrderRequestStatusCancelled`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | `str` | Required, Constant | The status of the order cancellation request.<br><br>**Value**: `"CANCELLED"` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.cancel_order_request_status_cancelled import CancelOrderRequestStatusCancelled

cancel_order_request_status_cancelled = CancelOrderRequestStatusCancelled(
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

