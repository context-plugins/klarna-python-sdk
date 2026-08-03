
# Address Location

The address of the location

*This model accepts additional fields of type Any.*

## Structure

`AddressLocation`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `city` | `str` | Optional | City |
| `country` | `str` | Required | Country |
| `postal_code` | `str` | Optional | Postal code. Validation according to [Universal Postal Union addressing system](https://www.upu.int/en/activities/addressing/postal-addressing-systems-in-member-countries.html). |
| `region` | `str` | Optional | Region |
| `street_address` | `str` | Required | The street address. Validation according to [Universal Postal Union addressing system](https://www.upu.int/en/activities/addressing/postal-addressing-systems-in-member-countries.html) |
| `street_address_2` | `str` | Optional | Additional street address |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address_location import AddressLocation

address_location = AddressLocation(
    country='country0',
    street_address='street_address8',
    city='city4',
    postal_code='postal_code8',
    region='region2',
    street_address_2='street_address__28',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

