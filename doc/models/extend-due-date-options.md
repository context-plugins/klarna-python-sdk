
# Extend Due Date Options

*This model accepts additional fields of type Any.*

## Structure

`ExtendDueDateOptions`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `currency` | `str` | Optional | The currency for the fees. Specified in ISO 4217 format. |
| `options` | [`List[OptionDto]`](../../doc/models/option-dto.md) | Optional | The available options and corresponding fees for extending the due date |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.extend_due_date_options import ExtendDueDateOptions
from klarna.models.option_dto import OptionDto

extend_due_date_options = ExtendDueDateOptions(
    currency='usd',
    options=[
        OptionDto(
            amount=172,
            number_of_days=28,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

