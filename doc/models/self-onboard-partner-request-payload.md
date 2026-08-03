
# Self Onboard Partner Request Payload

*This model accepts additional fields of type Any.*

## Structure

`SelfOnboardPartnerRequestPayload`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `client_id` | `str` | Required | The unique OAuth2 client Id of the partner<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `64`, *Pattern*: `^[a-zA-Z0-9]+$` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.self_onboard_partner_request_payload import SelfOnboardPartnerRequestPayload

self_onboard_partner_request_payload = SelfOnboardPartnerRequestPayload(
    client_id='abcdefghijklmnop1234567890',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

