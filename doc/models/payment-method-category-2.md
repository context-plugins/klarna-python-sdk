
# Payment Method Category 2

*This model accepts additional fields of type Any.*

## Structure

`PaymentMethodCategory2`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `asset_urls` | [`AssetUrls`](../../doc/models/asset-urls.md) | Optional | Asset URLs for the payment method. Using this dynamic asset will make sure that any design update of Klarna will automatically be propagated. |
| `identifier` | `str` | Optional | ID of the payment method category to be used while loading the widget later.<br>The possible values are:<ul><li>klarna</li><li>pay_later</li><li>pay_now</li><li>pay_over_time</li><li>direct_bank_transfer</li><li>direct_debit</li></ul> |
| `name` | `str` | Optional | Name of the payment method category. These names are dynamic depending on what payment method is in the category. Using this dynamic asset will make sure that any copy update of Klarna will automatically be propagated, or any updates of included payment methods by you. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.asset_urls import AssetUrls
from klarna.models.payment_method_category_2 import PaymentMethodCategory2

payment_method_category_2 = PaymentMethodCategory2(
    asset_urls=AssetUrls(
        descriptive='descriptive6',
        standard='standard0',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    identifier='klarna',
    name='Pay with Klarna',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

