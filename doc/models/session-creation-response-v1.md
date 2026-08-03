
# Session Creation Response V1

*This model accepts additional fields of type Any.*

## Structure

`SessionCreationResponseV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `distribution_module` | [`DistributionModuleV1`](../../doc/models/distribution-module-v1.md) | Optional | - |
| `distribution_url` | `str` | Optional | Endpoint for link distribution |
| `expires_at` | `datetime` | Optional | Session expiration time |
| `manual_identification_check_url` | `str` | Optional | Endpoint for manual identification check |
| `qr_code_url` | `str` | Optional | HPP url to download qr code image |
| `redirect_url` | `str` | Optional | HPP url to redirect the consumer to. ECOMMERCE only |
| `session_id` | `str` | Optional | HPP session id |
| `session_url` | `str` | Optional | Endpoint to get the session |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.distribution_module_v_1 import DistributionModuleV1
from klarna.models.session_creation_response_v_1 import SessionCreationResponseV1

session_creation_response_v_1 = SessionCreationResponseV1(
    distribution_module=DistributionModuleV1(
        generation_url='generation_url4',
        standalone_url='standalone_url2',
        token='token0',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    distribution_url='https://api.klarna.com/hpp/v1/sessions/9cbc9884-1fdb-45a8-9694-9340340d0436/distribution',
    expires_at=dateutil.parser.parse('2038-01-19T03:14:07.000Z'),
    manual_identification_check_url='https://api.klarna.com/hpp/v1/sessions/9cbc9884-1fdb-45a8-9694-9340340d0436/manual-id-check',
    qr_code_url='https://pay.klarna.com/eu/hpp/payments/a94e7760-d135-2721-a538-d6294ea254ed/qr',
    redirect_url='https://pay.klarna.com/eu/hpp/payments/2OCkffK',
    session_id='9cbc9884-1fdb-45a8-9694-9340340d0436',
    session_url='https://api.klarna.com/hpp/v1/sessions/9cbc9884-1fdb-45a8-9694-9340340d0436',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

