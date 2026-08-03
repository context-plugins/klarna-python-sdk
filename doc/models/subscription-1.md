
# Subscription 1

*This model accepts additional fields of type Any.*

## Structure

`Subscription1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `str` | Required | The name of the subscription product<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `interval` | [`Interval`](../../doc/models/interval.md) | Required | The cadence unit for this. |
| `interval_count` | `int` | Required | The number of intervals<br><br>**Constraints**: `>= 1` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.interval import Interval
from klarna.models.subscription_1 import Subscription1

subscription_1 = Subscription1(
    name='name4',
    interval=Interval.MONTH,
    interval_count=16,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

