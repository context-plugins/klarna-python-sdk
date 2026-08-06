
# Access Error Rate Limited

The request was rate limited.

All requests from this client are temporarily rate limited.

*This model accepts additional fields of type Any.*

## Structure

`AccessErrorRateLimited`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | [`ErrorCode6`](../../doc/models/error-code-6.md) | Required | Error code within the error type<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_type` | [`ErrorType3`](../../doc/models/error-type-3.md) | Required | The type of error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.access_error_rate_limited import AccessErrorRateLimited
from klarna.models.error_code_6 import ErrorCode6
from klarna.models.error_type_3 import ErrorType3

access_error_rate_limited = AccessErrorRateLimited(
    error_id='000001aa-0000-0000-0000-000000000000',
    error_code=ErrorCode6.RATE_LIMITED,
    error_type=ErrorType3.ACCESS_ERROR,
    error_message='Too many requests - please try again later',
    doc_url='doc_url8',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

