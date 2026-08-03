
# Order Line

List of order lines for the capture shown to the customer.

*This model accepts additional fields of type Any.*

## Structure

`OrderLine`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `image_url` | `str` | Optional | URL to an image that can be embedded in communications between Klarna and the customer.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `merchant_data` | `str` | Optional | Data about the order line.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `name` | `str` | Required | Descriptive item name.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `product_identifiers` | [`ProductIdentifiers`](../../doc/models/product-identifiers.md) | Optional | product_identifiers |
| `product_url` | `str` | Optional | URL to the product that can be used in communications between Klarna and the customer.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `quantity` | `int` | Required | Item quantity.<br><br>**Constraints**: `>= 0` |
| `quantity_unit` | `str` | Optional | Unit used to describe the quantity.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `10` |
| `reference` | `str` | Optional | Article number, SKU, or similar identifier on the product variant level.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `subscription` | [`Subscription`](../../doc/models/subscription.md) | Optional | Subscription information, such as the cadence and product name of the subscription that an order line item belongs to. |
| `tax_rate` | `int` | Optional | The tax rate in percent with two implicit decimals.<br><br>**Constraints**: `>= 0` |
| `total_amount` | `int` | Required | Total amount including tax and discounts (`quantity * unit_price - total_discount_amount`).<br><br>**Constraints**: `<= 200000000` |
| `total_discount_amount` | `int` | Optional | The discount amount in minor units. Includes tax. Example: 1200 = $12. Max value: 200000000<br><br>**Constraints**: `>= 0`, `<= 200000000` |
| `total_tax_amount` | `int` | Optional | The total tax amount in minor units.<br><br>**Constraints**: `<= 200000000` |
| `mtype` | [`Type`](../../doc/models/type.md) | Optional | Order line type.<br><br>**Constraints**: *Pattern*: `physical\|discount\|shipping_fee\|sales_tax\|store_credit\|gift_card\|digital\|surcharge\|return_fee` |
| `unit_price` | `int` | Required | Unit price including tax without applying discounts in minor units.<br><br>**Constraints**: `<= 200000000` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.mtype import Type
from klarna.models.order_line import OrderLine
from klarna.models.product_identifiers import ProductIdentifiers

order_line = OrderLine(
    name='name0',
    quantity=1,
    total_amount=199999000,
    unit_price=199999000,
    image_url='https://yourstore.example/product/headphones.png',
    merchant_data='Some metadata',
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
    product_url='https://yourstore.example/product/headphones',
    quantity_unit='pcs.',
    reference='75001',
    total_discount_amount=0,
    mtype=Type.PHYSICAL,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

