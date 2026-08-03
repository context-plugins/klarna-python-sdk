
# Cancel Order Request Status

*This model accepts additional fields of type Any.*

## Structure

`CancelOrderRequestStatus`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | [`Status1`](../../doc/models/status-1.md) | Required | The status of the order cancellation request. |
| `check_after` | `datetime` | Optional | Timestamp for when we expect a decision to be made on order cancellation. (ISO 8601)<br><br>This field is only populated if status is `PENDING`. |
| `reason_code` | [`ReasonCode`](../../doc/models/reason-code.md) | Optional | Reason code for why the order cancellation was rejected.<br><br>This field is only populated if status is `REJECTED`. |
| `reason_message` | `str` | Optional | Human-readable message for why the order cancellation was rejected.<br><br>This field is only populated if status is `REJECTED`. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.cancel_order_request_status import CancelOrderRequestStatus
from klarna.models.reason_code import ReasonCode
from klarna.models.status_1 import Status1

cancel_order_request_status = CancelOrderRequestStatus(
    status=Status1.PENDING,
    check_after=dateutil.parser.parse('2018-12-04T10:26:06.000Z'),
    reason_code=ReasonCode.CARD_IN_USE,
    reason_message='Cancellation request was rejected because the virtual credit card linked to this order is in use.',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

