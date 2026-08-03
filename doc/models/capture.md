
# Capture

*This model accepts additional fields of type Any.*

## Structure

`Capture`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `billing_address` | [`Address`](../../doc/models/address.md) | Optional | Shipping address for the capture. |
| `capture_id` | `str` | Optional | The capture id. Generated when the capture is created. |
| `captured_amount` | `int` | Optional | The captured amount in minor units.<br><br>**Constraints**: `>= 1` |
| `captured_at` | `datetime` | Optional | The time of the capture. Specified in ISO 8601. |
| `description` | `str` | Optional | Description of the capture shown to the customer. |
| `klarna_reference` | `str` | Optional | Customer friendly reference id, used as a reference when communicating with the customer. |
| `order_lines` | [`List[OrderLine]`](../../doc/models/order-line.md) | Optional | List of order lines for the capture shown to the customer. |
| `reference` | `str` | Optional | Internal reference to the capture which will be included in the settlement files. Max length is 255 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `refunded_amount` | `int` | Optional | Refunded amount for this capture in minor units. |
| `shipping_address` | [`Address`](../../doc/models/address.md) | Optional | Shipping address for the capture. |
| `shipping_info` | [`List[ShippingInfo]`](../../doc/models/shipping-info.md) | Optional | Shipping information for this capture. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.address import Address
from klarna.models.capture import Capture

capture = Capture(
    billing_address=Address(
        attention='attention8',
        city='city2',
        country='country2',
        email='email8',
        family_name='family_name8',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    capture_id='4ba29b50-be7b-44f5-a492-113e6a865e22',
    captured_amount=44,
    captured_at=dateutil.parser.parse('2015-11-19T01:51:17Z'),
    description='Order has been shipped',
    klarna_reference='K4MADNY-1',
    refunded_amount=0,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

