
# Resource Error Operation Forbidden

Insufficient privileges to perform the requested operation on the resource.

*This model accepts additional fields of type Any.*

## Structure

`ResourceErrorOperationForbidden`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | [`ErrorCode4`](../../doc/models/error-code-4.md) | Required | Error code within the error type<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_type` | [`ErrorType`](../../doc/models/error-type.md) | Required | The type of error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.error_code_4 import ErrorCode4
from klarna.models.error_type import ErrorType
from klarna.models.resource_error_operation_forbidden import ResourceErrorOperationForbidden

resource_error_operation_forbidden = ResourceErrorOperationForbidden(
    error_id='000003e4-0000-0000-0000-000000000000',
    error_code=ErrorCode4.OPERATION_FORBIDDEN,
    error_type=ErrorType.RESOURCE_ERROR,
    error_message='Insufficient privileges to <operation> on resource <resource>',
    doc_url='doc_url8',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

