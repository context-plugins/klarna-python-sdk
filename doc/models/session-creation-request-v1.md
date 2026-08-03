
# Session Creation Request V1

*This model accepts additional fields of type Any.*

## Structure

`SessionCreationRequestV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `merchant_urls` | [`MerchantUrlsV1`](../../doc/models/merchant-urls-v1.md) | Optional | - |
| `options` | [`OptionsV1`](../../doc/models/options-v1.md) | Optional | - |
| `payment_session_url` | `str` | Required | URL of the KP Session or KCO Order to be hosted by the HPP Session |
| `profile_id` | `str` | Optional | Profile id for default session options |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.background_image_v_1 import BackgroundImageV1
from klarna.models.merchant_urls_v_1 import MerchantUrlsV1
from klarna.models.options_v_1 import OptionsV1
from klarna.models.payment_method_category import PaymentMethodCategory
from klarna.models.payment_method_category_1 import PaymentMethodCategory1
from klarna.models.session_creation_request_v_1 import SessionCreationRequestV1

session_creation_request_v_1 = SessionCreationRequestV1(
    payment_session_url='One of https://api.klarna.com/payments/v1/sessions/92d97f60-7a78-46a5-8f68-c56fe52dc4af or https://api.klarna.com/checkout/v3/orders/92d97f60-7a78-46a5-8f68-c56fe52dc4af',
    merchant_urls=MerchantUrlsV1(
        back='back6',
        cancel='cancel6',
        error='error0',
        failure='failure0',
        status_update='status_update8',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    options=OptionsV1(
        background_images=[
            BackgroundImageV1(
                url='url4',
                width=58,
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            )
        ],
        logo_url='logo_url8',
        page_title='page_title6',
        payment_method_categories=[
            PaymentMethodCategory.PAY_LATER,
            PaymentMethodCategory.PAY_OVER_TIME
        ],
        payment_method_category=PaymentMethodCategory1.PAY_NOW,
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    profile_id='87ab3565-5e06-4006-9ada-8eedc6926703',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

