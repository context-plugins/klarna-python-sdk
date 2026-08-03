
# Resource Error Conflict Error

There was a conflict in using the resource.
Idempotency violation or concurrent updates to a resource occurred.

*This model accepts additional fields of type Any.*

## Structure

`ResourceErrorConflictError`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | `str` | Required, Constant | Error code within the error type<br><br>**Value**: `"RESOURCE_CONFLICT"` |
| `error_type` | `str` | Required, Constant | The type of error.<br><br>**Value**: `"RESOURCE_ERROR"` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.resource_error_conflict_error import ResourceErrorConflictError

resource_error_conflict_error = ResourceErrorConflictError(
    error_id='00000cb2-0000-0000-0000-000000000000',
    error_message='Concurrent update on resource <resource> | Idempotent operation on <resource> failed',
    doc_url='doc_url2',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

