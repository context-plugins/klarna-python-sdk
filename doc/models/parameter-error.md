
# Parameter Error

A validation error that occurred on a specific parameter.

*This model accepts additional fields of type Any.*

## Structure

`ParameterError`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `parameter` | `str` | Required | The name of the parameter that caused the error.<br>Specified in JSON dot-notation syntax.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `256` |
| `reason` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `512` |
| `doc_url` | `str` | Required | A deep link to the relevant documentation page on klarna.docs on how to fix the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.parameter_error import ParameterError

parameter_error = ParameterError(
    parameter='parameter6',
    reason='reason6',
    doc_url='doc_url0',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

