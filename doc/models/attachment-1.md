
# Attachment 1

*This model accepts additional fields of type Any.*

## Structure

`Attachment1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | `str` | Required | The content of the extra merchant data should be presented as a string inside this property. The body should be an object containing any of the keys and sub-objects described below serialized to JSON. More information on that object can be found [here](https://docs.klarna.com/api/extra-merchant-data). |
| `content_type` | `str` | Required | The content type of the body. It is usually represented as "application/vnd.klarna.internal.emd-v2+json" |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.attachment_1 import Attachment1

attachment_1 = Attachment1(
    body='{"customer_account_info":[{"unique_account_identifier":"test@gmail.com","account_registration_date":"2017-02-13T10:49:20Z","account_last_modified":"2019-03-13T11:45:27Z"}]}',
    content_type='application/vnd.klarna.internal.emd-v2+json',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

