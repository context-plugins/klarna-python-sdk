
# Merchant Manual Identification V1

*This model accepts additional fields of type Any.*

## Structure

`MerchantManualIdentificationV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `challenge` | `str` | Optional | Identification challenge |
| `customer` | [`CustomerV1`](../../doc/models/customer-v1.md) | Optional | - |
| `customer_obfuscated` | [`CustomerV1`](../../doc/models/customer-v1.md) | Optional | - |
| `expires_at` | `datetime` | Optional | Session identification expiry time (YYYY-MM-ddThh:mm:ss.fffZ) |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.customer_v_1 import CustomerV1
from klarna.models.merchant_manual_identification_v_1 import MerchantManualIdentificationV1

merchant_manual_identification_v_1 = MerchantManualIdentificationV1(
    challenge='A78',
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
    expires_at=dateutil.parser.parse('2038-01-19T03:14:07.000Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

