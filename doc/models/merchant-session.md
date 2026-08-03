
# Merchant Session

*This model accepts additional fields of type Any.*

## Structure

`MerchantSession`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `client_token` | `str` | Required | Client token to be passed to the JS client while initializing the JS SDK in the next step.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `4096` |
| `payment_method_categories` | [`List[PaymentMethodCategory2]`](../../doc/models/payment-method-category-2.md) | Optional | Available payment method categories for this particular session<br><br>**Constraints**: *Unique Items Required* |
| `session_id` | `str` | Required | ID of the created session. Please use this ID to share with Klarna for identifying any issues during integration.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.asset_urls import AssetUrls
from klarna.models.merchant_session import MerchantSession
from klarna.models.payment_method_category_2 import PaymentMethodCategory2

merchant_session = MerchantSession(
    client_token='eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ewogICJzZXNzaW9uX2lkIiA6ICIw',
    session_id='0b1d9815-165e-42e2-8867-35bc03789e00',
    payment_method_categories=[
        PaymentMethodCategory2(
            asset_urls=AssetUrls(
                descriptive='descriptive6',
                standard='standard0',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            identifier='identifier4',
            name='name8',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        PaymentMethodCategory2(
            asset_urls=AssetUrls(
                descriptive='descriptive6',
                standard='standard0',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            identifier='identifier4',
            name='name8',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        PaymentMethodCategory2(
            asset_urls=AssetUrls(
                descriptive='descriptive6',
                standard='standard0',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            identifier='identifier4',
            name='name8',
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

