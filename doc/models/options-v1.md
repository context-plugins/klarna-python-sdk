
# Options V1

*This model accepts additional fields of type Any.*

## Structure

`OptionsV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `background_images` | [`List[BackgroundImageV1]`](../../doc/models/background-image-v1.md) | Optional | List of Images to use for the background. Best matching resolution will be used. |
| `logo_url` | `str` | Optional | URL of the logo to be displayed |
| `page_title` | `str` | Optional | Title for the Payment Page |
| `payment_method_categories` | [`List[PaymentMethodCategory]`](../../doc/models/payment-method-category.md) | Optional | Payment Method Categories to show on the Payment Page. All available categories will be given to the customer if none is specified using payment_method_category or payment_method_categories. Ignored field for KCO Orders. |
| `payment_method_category` | [`PaymentMethodCategory1`](../../doc/models/payment-method-category-1.md) | Optional | Payment Method Category to show on the Payment Page. All available categories will be given to the customer if none is specified using payment_method_category or payment_method_categories. Ignored field for KCO Orders. |
| `place_order_mode` | [`PlaceOrderMode`](../../doc/models/place-order-mode.md) | Optional | - |
| `purchase_type` | [`PurchaseType`](../../doc/models/purchase-type.md) | Optional | The type of this purchase |
| `show_subtotal_detail` | [`ShowSubtotalDetail`](../../doc/models/show-subtotal-detail.md) | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.background_image_v_1 import BackgroundImageV1
from klarna.models.options_v_1 import OptionsV1
from klarna.models.payment_method_category import PaymentMethodCategory
from klarna.models.payment_method_category_1 import PaymentMethodCategory1
from klarna.models.place_order_mode import PlaceOrderMode
from klarna.models.purchase_type import PurchaseType
from klarna.models.show_subtotal_detail import ShowSubtotalDetail

options_v_1 = OptionsV1(
    background_images=[
        BackgroundImageV1(
            url='url4',
            width=58,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        BackgroundImageV1(
            url='url4',
            width=58,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    logo_url='https://example.com/logo.jpg',
    page_title='Complete your purchase',
    payment_method_categories=[
        PaymentMethodCategory.DIRECT_BANK_TRANSFER
    ],
    payment_method_category=PaymentMethodCategory1.PAY_NOW,
    place_order_mode=PlaceOrderMode.PLACE_ORDER,
    purchase_type=PurchaseType.BUY,
    show_subtotal_detail=ShowSubtotalDetail.HIDE,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

