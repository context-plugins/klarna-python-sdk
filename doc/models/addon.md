
# Addon

Array consisting of add-ons selected by the consumer, may be empty

*This model accepts additional fields of type Any.*

## Structure

`Addon`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `external_id` | `str` | Optional | The ID provided by the TMS |
| `price` | `int` | Required | The price of the add-on<br><br>**Constraints**: `>= 0` |
| `mtype` | `str` | Required | The type of the add-on, e.g. sms or entry-code |
| `user_input` | `str` | Optional | The text provided by the user |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.addon import Addon

addon = Addon(
    price=204,
    mtype='type6',
    external_id='external_id0',
    user_input='user_input2',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

