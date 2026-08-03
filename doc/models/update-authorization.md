
# Update Authorization

*This model accepts additional fields of type Any.*

## Structure

`UpdateAuthorization`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `description` | `str` | Optional | Description of the change.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `order_amount` | `int` | Required | The new total order amount. Minor units.<br><br>**Constraints**: `>= 0`, `<= 200000000` |
| `order_lines` | [`List[OrderLine]`](../../doc/models/order-line.md) | Optional | New set of order lines for the order.<br><br>**Constraints**: *Minimum Items*: `0`, *Maximum Items*: `1000` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.order_line import OrderLine
from klarna.models.product_identifiers import ProductIdentifiers
from klarna.models.update_authorization import UpdateAuthorization

update_authorization = UpdateAuthorization(
    order_amount=84,
    description='Added charger',
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
        )
    ],
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

