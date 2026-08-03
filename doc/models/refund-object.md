
# Refund Object

*This model accepts additional fields of type Any.*

## Structure

`RefundObject`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `description` | `str` | Optional | Description of the refund shown to the customer. Max length is 255 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `order_lines` | [`List[OrderLine]`](../../doc/models/order-line.md) | Optional | Order lines for the refund shown to the customer. Optional but increases the customer experience. Maximum 1000 order lines.<br><br>**Constraints**: *Minimum Items*: `0`, *Maximum Items*: `1000` |
| `reference` | `str` | Optional | Internal reference to the refund. This will be included in the settlement files. Max length is 255 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `refunded_amount` | `int` | Required | Refunded amount in minor units.<br><br>**Constraints**: `>= 0`, `<= 200000000` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.order_line import OrderLine
from klarna.models.product_identifiers import ProductIdentifiers
from klarna.models.refund_object import RefundObject

refund_object = RefundObject(
    refunded_amount=122,
    description='description0',
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
    reference='reference6',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

