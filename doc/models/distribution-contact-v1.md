
# Distribution Contact V1

*This model accepts additional fields of type Any.*

## Structure

`DistributionContactV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `access_id` | [`AccessId`](../../doc/models/access-id.md) | Optional | Access Id for connection to HPP session. Only required if distribution method is 'token' |
| `email` | `str` | Optional | Email where to send the email with the HPP link. Only required if distribution method is 'email' |
| `phone` | `str` | Optional | Phone number where to send the sms with the HPP link. Only required if distribution method is 'sms' |
| `phone_country` | `str` | Optional | ISO 3166 alpha-2 phone country. Only required if distribution method is 'sms' |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.access_id import AccessId
from klarna.models.distribution_contact_v_1 import DistributionContactV1

distribution_contact_v_1 = DistributionContactV1(
    access_id=AccessId.ENUM_KLARNA09F4A78DD09647D4A0F6ABCF680C70FE,
    email='test@example.com',
    phone='07000212345',
    phone_country='SE',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

