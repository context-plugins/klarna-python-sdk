
# Input Error Content Type Error

The input does not conform to the expected content type syntax. For example invalid JSON.

*This model accepts additional fields of type Any.*

## Structure

`InputErrorContentTypeError`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | `str` | Required, Constant | Error code within the error type<br><br>**Value**: `"INVALID_CONTENT_TYPE"` |
| `error_type` | `str` | Required, Constant | The type of error.<br><br>**Value**: `"INPUT_ERROR"` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.input_error_content_type_error import InputErrorContentTypeError

input_error_content_type_error = InputErrorContentTypeError(
    error_id='00001b84-0000-0000-0000-000000000000',
    error_message='The received input is not valid JSON',
    doc_url='doc_url6',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

