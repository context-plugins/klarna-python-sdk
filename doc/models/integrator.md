
# Integrator

An integrator is the entity that is responsible for the integration with Klarna.

*This model accepts additional fields of type Any.*

## Structure

`Integrator`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `str` | Required | The name of the integrator using SCREAMING_SNAKE_CASE.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `50`, *Pattern*: `^[A-Z0-9_]+$` |
| `session_reference` | `str` | Required | A reference to the session that is being used.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100` |
| `module_name` | `str` | Optional | The name of the module that is being used to initiate the request<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `50` |
| `module_version` | `str` | Optional | The version of the module that is being used.<br>Can be a semantic version, commit hash, date or any other versioning scheme to identify which code that issued the request.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `50` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.integrator import Integrator

integrator = Integrator(
    name='PSP',
    session_reference='session_reference6',
    module_name='psp-new-payment',
    module_version='module_version8',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

