
# Refund

*This model accepts additional fields of type Any.*

## Structure

`Refund`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `credit_invoice` | `bool` | Optional | Only relevant for B2B Orders. If the flag is set to true for an order with B2B_invoice as payment method, the customer will receive the refund as a credit invoice. |
| `description` | `str` | Optional | Description of the refund shown to the customer. Max length is 255 characters. |
| `order_lines` | [`List[OrderLine]`](../../doc/models/order-line.md) | Optional | Order lines for the refund shown to the customer. Optional but increases the customer experience. Maximum 1000 order lines. |
| `reference` | `str` | Optional | Internal reference to the refund that is also included in the settlement files. Max length is 255 characters. |
| `refund_id` | `str` | Optional | The refund id. Generated when the refund is created. |
| `refunded_amount` | `int` | Optional | Refunded amount in minor units. |
| `refunded_at` | `datetime` | Optional | The time of the refund. ISO 8601. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.order_line import OrderLine
from klarna.models.product_identifiers import ProductIdentifiers
from klarna.models.refund import Refund

refund = Refund(
    credit_invoice=False,
    description='The item was returned and the order refunded.',
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
    reference='reference4',
    refund_id='b2cb4f2e-2781-4359-80ad-555735ebb8d8',
    refunded_at=dateutil.parser.parse('2015-12-04T15:17:40Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

