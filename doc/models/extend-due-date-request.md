
# Extend Due Date Request

*This model accepts additional fields of type Any.*

## Structure

`ExtendDueDateRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `number_of_days` | `int` | Required | Number of days to extend the due date. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.extend_due_date_request import ExtendDueDateRequest

extend_due_date_request = ExtendDueDateRequest(
    number_of_days=244,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

