
# Promise Created Response

*This model accepts additional fields of type Any.*

## Structure

`PromiseCreatedResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `expires_at` | `datetime` | Optional | - |
| `promise_id` | `str` | Optional, Read-only | The unique promise id |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.promise_created_response import PromiseCreatedResponse

promise_created_response = PromiseCreatedResponse(
    expires_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
    promise_id='ee4a8e3a-9dfd-49e0-9ac8-ea2b6c76408c',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

