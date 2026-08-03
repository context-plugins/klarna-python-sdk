
# Application Json

*This model accepts additional fields of type Any.*

## Structure

`ApplicationJson`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `integrator` | [`Integrator`](../../doc/models/integrator.md) | Required | An integrator is the entity that is responsible for the integration with Klarna. |
| `originators` | [`List[Originator]`](../../doc/models/originator.md) | Optional | Array of originators that are responsible for the request.<br>If the request is sent through multiple systems before reaching the integrator, each system can be represented as an originator.<br><br>**Constraints**: *Maximum Items*: `10` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.application_json import ApplicationJson
from klarna.models.integrator import Integrator
from klarna.models.originator import Originator

application_json = ApplicationJson(
    integrator=Integrator(
        name='PSP',
        session_reference='session_reference6',
        module_name='psp-new-payment',
        module_version='module_version8',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    originators=[
        Originator(
            name='name6',
            session_reference='session_reference6',
            module_name='module_name4',
            module_version='module_version8',
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

