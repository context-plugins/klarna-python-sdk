
# Timeslot

The chosen timeslot of the selected shipping option

*This model accepts additional fields of type Any.*

## Structure

`Timeslot`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `cutoff` | `str` | Optional | Cutoff time for delivery |
| `end` | `str` | Optional | End of the timeslot |
| `id` | `str` | Optional | The timeslot id |
| `price` | `int` | Optional | Price |
| `start` | `str` | Optional | Start of the timeslot |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.timeslot import Timeslot

timeslot = Timeslot(
    cutoff='cutoff2',
    end='end0',
    id='id2',
    price=24,
    start='start6',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

