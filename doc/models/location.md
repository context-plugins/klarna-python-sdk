
# Location

The location of the selected shipping option

*This model accepts additional fields of type Any.*

## Structure

`Location`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `address` | [`AddressLocation`](../../doc/models/address-location.md) | Optional | The address of the location |
| `id` | `str` | Optional | The location id |
| `name` | `str` | Optional | The display name of the location |
| `price` | `int` | Optional | The price for this location |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address_location import AddressLocation
from klarna.models.location import Location

location = Location(
    address=AddressLocation(
        country='country0',
        street_address='street_address8',
        city='city6',
        postal_code='postal_code8',
        region='region2',
        street_address_2='street_address__28',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    id='id4',
    name='name4',
    price=102,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

