
# Merchant Urls V1

*This model accepts additional fields of type Any.*

## Structure

`MerchantUrlsV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `back` | `str` | Optional | Back URL |
| `cancel` | `str` | Optional | Cancel URL |
| `error` | `str` | Optional | System error URL |
| `failure` | `str` | Optional | Failure URL |
| `status_update` | `str` | Optional | Status update URL |
| `success` | `str` | Optional | Success URL |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.merchant_urls_v_1 import MerchantUrlsV1

merchant_urls_v_1 = MerchantUrlsV1(
    back='https://example.com/back?sid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&hppId={{session_id}}',
    cancel='https://example.com/cancel?sid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&hppId={{session_id}}',
    error='https://example.com/error?sid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&hppId={{session_id}}',
    failure='https://example.com/fail?sid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&hppId={{session_id}}',
    status_update='https://example.com/status_update?sid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&secret=yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy&hppId={{session_id}}',
    success='https://example.com/success?sid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&hppId={{session_id}}&token={{authorization_token}}',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

