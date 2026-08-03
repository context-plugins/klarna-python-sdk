
# Update Consumer

*This model accepts additional fields of type Any.*

## Structure

`UpdateConsumer`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `shipping_address` | [`Address`](../../doc/models/address.md) | Optional | Shipping address for the capture. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address import Address
from klarna.models.update_consumer import UpdateConsumer

update_consumer = UpdateConsumer(
    shipping_address=Address(
        attention='attention0',
        city='city0',
        country='country4',
        email='email6',
        family_name='family_name4',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

