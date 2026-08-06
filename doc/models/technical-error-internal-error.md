
# Technical Error Internal Error

An unexpected error occurred in the API.

The request may be retried without modification after a delay.

If this error persists, please reach out to your Klarna support contact.

*This model accepts additional fields of type Any.*

## Structure

`TechnicalErrorInternalError`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | [`ErrorCode7`](../../doc/models/error-code-7.md) | Required | Error code within the error type<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_type` | [`ErrorType7`](../../doc/models/error-type-7.md) | Required | The type of error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.error_code_7 import ErrorCode7
from klarna.models.error_type_7 import ErrorType7
from klarna.models.technical_error_internal_error import TechnicalErrorInternalError

technical_error_internal_error = TechnicalErrorInternalError(
    error_id='00000e7c-0000-0000-0000-000000000000',
    error_code=ErrorCode7.INTERNAL_ERROR,
    error_type=ErrorType7.TECHNICAL_ERROR,
    error_message='Something went wrong at Klarna, if the error persists please reach out to your support contact and include this message',
    doc_url='doc_url0',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

