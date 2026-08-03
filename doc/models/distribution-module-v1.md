
# Distribution Module V1

*This model accepts additional fields of type Any.*

## Structure

`DistributionModuleV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `generation_url` | `str` | Optional | - |
| `standalone_url` | `str` | Optional | - |
| `token` | `str` | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.distribution_module_v_1 import DistributionModuleV1

distribution_module_v_1 = DistributionModuleV1(
    generation_url='generation_url6',
    standalone_url='standalone_url4',
    token='token2',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

