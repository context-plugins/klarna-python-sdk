
# Originator

An originator is the entity that is responsible for the request.

*This model accepts additional fields of type Any.*

## Structure

`Originator`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `str` | Required | The name of the originator using SCREAMING_SNAKE_CASE.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `50`, *Pattern*: `^[A-Z0-9_]+$` |
| `session_reference` | `str` | Required | A reference to the session that is being used.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100` |
| `module_name` | `str` | Optional | The name of the module that is being used.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `50` |
| `module_version` | `str` | Optional | The version of the module that is being used.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `50` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.originator import Originator

originator = Originator(
    name='ECOMMERCE_COMPANY',
    session_reference='session_reference0',
    module_name='module_name8',
    module_version='module_version2',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

