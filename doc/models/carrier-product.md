
# Carrier Product

The chosen timeslot of the selected shipping option

*This model accepts additional fields of type Any.*

## Structure

`CarrierProduct`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `identifier` | `str` | Optional | Id of carrier product |
| `name` | `str` | Optional | Name of carrier product |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.carrier_product import CarrierProduct

carrier_product = CarrierProduct(
    identifier='identifier2',
    name='name0',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

