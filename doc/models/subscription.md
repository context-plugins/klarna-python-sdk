
# Subscription

Subscription information, such as the cadence and product name of the subscription that an order line item belongs to.

*This model accepts additional fields of type Any.*

## Structure

`Subscription`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `interval` | `str` | Required | The cadence unit. Matches: DAY\|WEEK\|MONTH\|YEAR<br><br>**Constraints**: *Pattern*: `DAY\|WEEK\|MONTH\|YEAR` |
| `interval_count` | `int` | Required | The number of intervals.<br><br>**Constraints**: `>= 1` |
| `name` | `str` | Required | The name of the subscription product. Maximum 255 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.subscription import Subscription

subscription = Subscription(
    interval='MONTH',
    interval_count=234,
    name='name4',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

