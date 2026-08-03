
# Input Error Validation Error

An input parameter failed input validation. For example exceeding a max value, or failed pattern matching.

*This model accepts additional fields of type Any.*

## Structure

`InputErrorValidationError`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | `str` | Required, Constant | Error code within the error type<br><br>**Value**: `"VALIDATION_ERROR"` |
| `error_type` | `str` | Required, Constant | The type of error.<br><br>**Value**: `"INPUT_ERROR"` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `validation_errors` | [`List[ParameterError]`](../../doc/models/parameter-error.md) | Optional | A list of validation errors that occurred |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.input_error_validation_error import InputErrorValidationError
from klarna.models.parameter_error import ParameterError

input_error_validation_error = InputErrorValidationError(
    error_id='00001aaa-0000-0000-0000-000000000000',
    error_message='error_message0',
    doc_url='doc_url2',
    validation_errors=[
        ParameterError(
            parameter='parameter2',
            reason='reason8',
            doc_url='doc_url4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        ParameterError(
            parameter='parameter2',
            reason='reason8',
            doc_url='doc_url4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        ParameterError(
            parameter='parameter2',
            reason='reason8',
            doc_url='doc_url4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

