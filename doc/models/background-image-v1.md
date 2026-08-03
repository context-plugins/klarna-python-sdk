
# Background Image V1

*This model accepts additional fields of type Any.*

## Structure

`BackgroundImageV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `url` | `str` | Optional | Url for the image |
| `width` | `int` | Optional | Width of the image |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.background_image_v_1 import BackgroundImageV1

background_image_v_1 = BackgroundImageV1(
    url='url8',
    width=68,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

