
# Resource Error Not Found Error

The requested resource was not found.

*This model accepts additional fields of type Any.*

## Structure

`ResourceErrorNotFoundError`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | [`ErrorCode5`](../../doc/models/error-code-5.md) | Required | Error code within the error type<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_type` | [`ErrorType`](../../doc/models/error-type.md) | Required | The type of error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.error_code_5 import ErrorCode5
from klarna.models.error_type import ErrorType
from klarna.models.resource_error_not_found_error import ResourceErrorNotFoundError

resource_error_not_found_error = ResourceErrorNotFoundError(
    error_id='00001c1a-0000-0000-0000-000000000000',
    error_code=ErrorCode5.RESOURCE_NOT_FOUND,
    error_type=ErrorType.RESOURCE_ERROR,
    error_message='Resource <resource> does not exist',
    doc_url='doc_url4',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

