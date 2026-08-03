
# State Context 2

Additional context specific to the current dispute state. Required in all states, with different schemas depending on the state.

*This model accepts additional fields of type Any.*

## Structure

`StateContext2`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `arbitration_expires_at` | `datetime` | Required | Timestamp of when the pre-arbitration window will expire (partner must decide to accept or escalate to arbitration) |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.state_context_2 import StateContext2

state_context_2 = StateContext2(
    arbitration_expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

