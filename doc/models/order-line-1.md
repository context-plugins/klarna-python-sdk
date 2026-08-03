
# Order Line 1

*This model accepts additional fields of type Any.*

## Structure

`OrderLine1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `image_url` | `str` | Optional | URL to an image that can be later embedded in communications between Klarna and the customer. (max 1024 characters).<br>A minimum of 250x250 px resolution is recommended for the image to look good in the Klarna app, and below 50x50 px won't even show. We recommend using a good sized image (650x650 px or more), however the file size must not exceed 12MB.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `merchant_data` | `str` | Optional | Used for storing merchant's internal order number or other reference. Pass through field. (max 1024 characters)<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `name` | `str` | Required | Descriptive name of the order line item.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `product_identifiers` | [`ProductIdentifiers`](../../doc/models/product-identifiers.md) | Optional | Additional information identifying the order line item. |
| `product_url` | `str` | Optional | URL to the product in the merchant’s webshop that can be later used in communications between Klarna and the customer. (max 1024 characters)<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `quantity` | `int` | Required | Quantity of the order line item. Must be a non-negative number.<br><br>**Constraints**: `>= 0` |
| `quantity_unit` | `str` | Optional | Unit used to describe the quantity, e.g. kg, pcs, etc. If defined the value has to be 1-8 characters.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `8` |
| `reference` | `str` | Optional | Client facing article number, SKU or similar. Max length is 256 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `tax_rate` | `int` | Optional | Tax rate of the order line. Non-negative value. The percentage value is represented with two implicit decimals. I.e 2000 = 20%.<br><br>**Constraints**: `>= 0`, `<= 10000` |
| `total_amount` | `int` | Required | Total amount of the order line. Must be defined as minor units. Includes tax and discount. Eg: 2000=20 euros<br>Value = (quantity x unit_price) - total_discount_amount.<br>(max value: 200000000)<br><br>**Constraints**: `<= 200000000` |
| `total_discount_amount` | `int` | Optional | Non-negative minor units. Includes tax. Eg: 500=5 euros<br><br>**Constraints**: `>= 0` |
| `total_tax_amount` | `int` | Optional | Total tax amount of the order line. Must be within ±1 of total_amount - total_amount 10000 / (10000 + tax_rate). Negative when type is discount. |
| `mtype` | [`Type11`](../../doc/models/type-11.md) | Optional | Type of the order line item. |
| `unit_price` | `int` | Required | Price for a single unit of the order line. Must be defined as minor units and exclude any discount. Typically including taxes, however some countries may include specific requirements, see [Tax handling guidelines](https://docs.klarna.com/payments/web-payments/additional-resources/error-handling-and-validations/tax-handling/) for further details. (max value: 200000000)<br><br>**Constraints**: `<= 200000000` |
| `subscription` | [`Subscription1`](../../doc/models/subscription-1.md) | Optional | Subscription details |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.order_line_1 import OrderLine1
from klarna.models.product_identifiers import ProductIdentifiers
from klarna.models.type_11 import Type11

order_line_1 = OrderLine1(
    name='Running shoe',
    quantity=1,
    total_amount=2000,
    unit_price=2500,
    image_url='https://www.exampleobjects.com/logo.png',
    merchant_data='{"customer_account_info":[{"unique_account_identifier":"test@gmail.com","account_registration_date":"2017-02-13T10:49:20Z","account_last_modified":"2019-03-13T11:45:27Z"}]}',
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
    product_url='https://.../AD6654412.html',
    quantity_unit='pcs',
    reference='AD6654412',
    tax_rate=2000,
    total_discount_amount=500,
    total_tax_amount=333,
    mtype=Type11.PHYSICAL,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

