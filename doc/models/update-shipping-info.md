
# Update Shipping Info

*This model accepts additional fields of type Any.*

## Structure

`UpdateShippingInfo`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `shipping_info` | [`List[ShippingInfo]`](../../doc/models/shipping-info.md) | Required | New shipping info. Maximum: 500 items.<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `500` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.shipping_info import ShippingInfo
from klarna.models.update_shipping_info import UpdateShippingInfo

update_shipping_info = UpdateShippingInfo(
    shipping_info=[
        ShippingInfo(
            return_shipping_company='dhl-express',
            return_tracking_number='93456415674545679888',
            return_tracking_uri='http://shipping.example/findmypackage?93456415674545679888',
            shipping_company='dhl-express',
            shipping_method='Home',
            tracking_number='63456415674545679874',
            tracking_uri='http://shipping.example/findmypackage?63456415674545679874',
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

