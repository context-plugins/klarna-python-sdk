
# Session Response V1

*This model accepts additional fields of type Any.*

## Structure

`SessionResponseV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `authorization_token` | `str` | Optional | Authorization token (only for KP Sessions) |
| `customer` | [`CustomerV1`](../../doc/models/customer-v1.md) | Optional | - |
| `expires_at` | `datetime` | Optional | Session expiration time |
| `klarna_reference` | `str` | Optional | Klarna reference provided by MoOD |
| `manual_identification` | [`MerchantManualIdentificationV1`](../../doc/models/merchant-manual-identification-v1.md) | Optional | - |
| `order_id` | `str` | Optional | Order id of the payment session |
| `session_id` | `str` | Optional | The id of the HPP Session |
| `status` | [`Status`](../../doc/models/status.md) | Optional | Current HPP Session status |
| `updated_at` | `datetime` | Optional | Latest status update time |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.customer_v_1 import CustomerV1
from klarna.models.merchant_manual_identification_v_1 import MerchantManualIdentificationV1
from klarna.models.session_response_v_1 import SessionResponseV1
from klarna.models.status import Status

session_response_v_1 = SessionResponseV1(
    authorization_token='70850a20-a2a0-5c70-810c-096fa6f850bb',
    customer=CustomerV1(
        date_of_birth='date_of_birth8',
        family_name='family_name6',
        given_name='given_name2',
        national_identification_number='national_identification_number2',
        title='title4',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    expires_at=dateutil.parser.parse('2038-01-19T03:14:07.000Z'),
    klarna_reference='ffc25786',
    manual_identification=MerchantManualIdentificationV1(
        challenge='challenge2',
        customer=CustomerV1(
            date_of_birth='date_of_birth8',
            family_name='family_name6',
            given_name='given_name2',
            national_identification_number='national_identification_number2',
            title='title4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        customer_obfuscated=CustomerV1(
            date_of_birth='date_of_birth4',
            family_name='family_name2',
            given_name='given_name6',
            national_identification_number='national_identification_number6',
            title='title0',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        expires_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    order_id='93d644a2-43f3-11e9-b210-d663bd873d93',
    session_id='a15b228c-02ad-11e9-8eb2-f2801f1b9fd1',
    status=Status.COMPLETED,
    updated_at=dateutil.parser.parse('2038-01-19T03:14:07.000Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

