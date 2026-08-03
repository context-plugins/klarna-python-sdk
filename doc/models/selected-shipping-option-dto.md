
# Selected Shipping Option Dto

The shipping option selected by the user.

*This model accepts additional fields of type Any.*

## Structure

`SelectedShippingOptionDto`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `carrier` | `str` | Optional | The carrier for the selected shipping option |
| `carrier_product` | [`CarrierProduct`](../../doc/models/carrier-product.md) | Optional | The chosen timeslot of the selected shipping option |
| `mclass` | `str` | Optional | The class of the selected shipping option |
| `id` | `str` | Optional | The id of the selected shipping option as provided by the TMS |
| `location` | [`Location`](../../doc/models/location.md) | Optional | The location of the selected shipping option |
| `method` | `str` | Optional | The method of the selected shipping option |
| `name` | `str` | Optional | The display name of the selected shipping option |
| `price` | `int` | Optional | The price of the selected shipping option |
| `selected_addons` | [`List[Addon]`](../../doc/models/addon.md) | Optional | Array consisting of add-ons selected by the consumer, may be empty |
| `tax_amount` | `int` | Optional | The tax amount of the selected shipping option |
| `tax_rate` | `int` | Optional | The tax rate of the selected shipping option |
| `timeslot` | [`Timeslot`](../../doc/models/timeslot.md) | Optional | The chosen timeslot of the selected shipping option |
| `tms_reference` | `str` | Optional | The shipment_id provided by the TMS |
| `mtype` | `str` | Optional | The type of the selected shipping option |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address_location import AddressLocation
from klarna.models.carrier_product import CarrierProduct
from klarna.models.location import Location
from klarna.models.selected_shipping_option_dto import SelectedShippingOptionDto

selected_shipping_option_dto = SelectedShippingOptionDto(
    carrier='carrier0',
    carrier_product=CarrierProduct(
        identifier='identifier2',
        name='name0',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    mclass='class6',
    id='id8',
    location=Location(
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
    ),
    price=0,
    tax_amount=0,
    tax_rate=0,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

