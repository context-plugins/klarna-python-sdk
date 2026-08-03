
# Capture Object

Capture request data

*This model accepts additional fields of type Any.*

## Structure

`CaptureObject`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `captured_amount` | `int` | Required | The captured amount in minor units.<br><br>**Constraints**: `>= 0`, `<= 200000000` |
| `description` | `str` | Optional | Description of the capture shown to the customer. Maximum 255 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `order_lines` | [`List[OrderLine]`](../../doc/models/order-line.md) | Optional | Order lines for this capture. Maximum 1000 items.<br><br>**Constraints**: *Minimum Items*: `0`, *Maximum Items*: `1000` |
| `reference` | `str` | Optional | Internal reference to the capture. This will be included in the settlement files. Max length is 255 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `shipping_delay` | `int` | Optional | Delay before the order will be shipped. Use for improving the customer experience regarding payments. This field is currently not returned when reading the order. Minimum: 0. Please note: to be able to submit values larger than 0, this has to be enabled in your merchant account. Please contact Klarna for further information.<br><br>**Constraints**: `>= 0` |
| `shipping_info` | [`List[ShippingInfo]`](../../doc/models/shipping-info.md) | Optional | Shipping information for this capture. Maximum 500 items.<br><br>**Constraints**: *Minimum Items*: `0`, *Maximum Items*: `500` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.capture_object import CaptureObject
from klarna.models.order_line import OrderLine
from klarna.models.product_identifiers import ProductIdentifiers
from klarna.models.shipping_info import ShippingInfo

capture_object = CaptureObject(
    captured_amount=170,
    description='description6',
    order_lines=[
        OrderLine(
            name='name2',
            quantity=104,
            total_amount=199999000,
            unit_price=199999000,
            image_url='image_url8',
            merchant_data='merchant_data0',
            product_identifiers=ProductIdentifiers(
                brand='brand6',
                category_path='category_path0',
                color='color6',
                global_trade_item_number='global_trade_item_number8',
                manufacturer_part_number='manufacturer_part_number2',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            product_url='product_url6',
            quantity_unit='quantity_unit8',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        OrderLine(
            name='name2',
            quantity=104,
            total_amount=199999000,
            unit_price=199999000,
            image_url='image_url8',
            merchant_data='merchant_data0',
            product_identifiers=ProductIdentifiers(
                brand='brand6',
                category_path='category_path0',
                color='color6',
                global_trade_item_number='global_trade_item_number8',
                manufacturer_part_number='manufacturer_part_number2',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            product_url='product_url6',
            quantity_unit='quantity_unit8',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        OrderLine(
            name='name2',
            quantity=104,
            total_amount=199999000,
            unit_price=199999000,
            image_url='image_url8',
            merchant_data='merchant_data0',
            product_identifiers=ProductIdentifiers(
                brand='brand6',
                category_path='category_path0',
                color='color6',
                global_trade_item_number='global_trade_item_number8',
                manufacturer_part_number='manufacturer_part_number2',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            product_url='product_url6',
            quantity_unit='quantity_unit8',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    reference='reference8',
    shipping_delay=220,
    shipping_info=[
        ShippingInfo(
            return_shipping_company='return_shipping_company6',
            return_tracking_number='return_tracking_number6',
            return_tracking_uri='return_tracking_uri2',
            shipping_company='shipping_company0',
            shipping_method='shipping_method0',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        ShippingInfo(
            return_shipping_company='return_shipping_company6',
            return_tracking_number='return_tracking_number6',
            return_tracking_uri='return_tracking_uri2',
            shipping_company='shipping_company0',
            shipping_method='shipping_method0',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        ShippingInfo(
            return_shipping_company='return_shipping_company6',
            return_tracking_number='return_tracking_number6',
            return_tracking_uri='return_tracking_uri2',
            shipping_company='shipping_company0',
            shipping_method='shipping_method0',
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

