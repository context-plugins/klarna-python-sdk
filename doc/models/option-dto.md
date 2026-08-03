
# Option Dto

The available options and corresponding fees for extending the due date

*This model accepts additional fields of type Any.*

## Structure

`OptionDto`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `amount` | `int` | Optional | The fee for extending the due date this many days. In minor units. |
| `number_of_days` | `int` | Optional | How many days to extend the due date with |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.option_dto import OptionDto

option_dto = OptionDto(
    amount=202,
    number_of_days=58,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

