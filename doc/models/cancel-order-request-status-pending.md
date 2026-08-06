
# Cancel Order Request Status Pending

*This model accepts additional fields of type Any.*

## Structure

`CancelOrderRequestStatusPending`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | [`Status11`](../../doc/models/status-11.md) | Required | The status of the order cancellation request. |
| `check_after` | `datetime` | Required | Timestamp for when we expect a decision to be made on order cancellation. (ISO 8601) |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.cancel_order_request_status_pending import CancelOrderRequestStatusPending
from klarna.models.status_11 import Status11

cancel_order_request_status_pending = CancelOrderRequestStatusPending(
    status=Status11.PENDING,
    check_after=dateutil.parser.parse('2018-12-04T10:26:06.000Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

