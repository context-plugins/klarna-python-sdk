
# Distribution Request V1

*This model accepts additional fields of type Any.*

## Structure

`DistributionRequestV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `contact_information` | [`DistributionContactV1`](../../doc/models/distribution-contact-v1.md) | Required | - |
| `method` | [`Method1`](../../doc/models/method-1.md) | Required | Method used for distribution |
| `template` | [`Template`](../../doc/models/template.md) | Optional | Template to use for distribution. In the current version this value is not used and might be removed in the future. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.access_id import AccessId
from klarna.models.distribution_contact_v_1 import DistributionContactV1
from klarna.models.distribution_request_v_1 import DistributionRequestV1
from klarna.models.method_1 import Method1
from klarna.models.template import Template

distribution_request_v_1 = DistributionRequestV1(
    contact_information=DistributionContactV1(
        access_id=AccessId.ENUM_467521087419,
        email='test@example.com',
        phone='07000212345',
        phone_country='SE',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    method=Method1.SMS,
    template=Template.INSTORE_PURCHASE,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

