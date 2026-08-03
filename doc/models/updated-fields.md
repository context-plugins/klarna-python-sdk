
# Updated Fields

The new values of the updated fields.

*This model accepts additional fields of type Any.*

## Structure

`UpdatedFields`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `evidence_response_deadline_at` | `datetime` | Optional | The value of the representment response deadline |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.updated_fields import UpdatedFields

updated_fields = UpdatedFields(
    evidence_response_deadline_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

