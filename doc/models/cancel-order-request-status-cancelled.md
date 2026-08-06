
# Cancel Order Request Status Cancelled

*This model accepts additional fields of type Any.*

## Structure

`CancelOrderRequestStatusCancelled`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | [`Status2`](../../doc/models/status-2.md) | Required | The status of the order cancellation request. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.cancel_order_request_status_cancelled import CancelOrderRequestStatusCancelled
from klarna.models.status_2 import Status2

cancel_order_request_status_cancelled = CancelOrderRequestStatusCancelled(
    status=Status2.CANCELLED,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

