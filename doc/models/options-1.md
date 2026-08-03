
# Options 1

*This model accepts additional fields of type Any.*

## Structure

`Options1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `color_border` | `str` | Optional | Color for the border of elements within the iFrame. Value should be a CSS hex color, e.g. "#FF9900"<br><br>**Constraints**: *Pattern*: `^#[A-Fa-f0-9]{6}$` |
| `color_border_selected` | `str` | Optional | Color for the border of elements within the iFrame when selected by the customer. Value should be a CSS hex color, e.g. "#FF9900"<br><br>**Constraints**: *Pattern*: `^#[A-Fa-f0-9]{6}$` |
| `color_details` | `str` | Optional | Color for the bullet points within the iFrame. Value should be a CSS hex color, e.g. "#FF9900"<br><br>**Constraints**: *Pattern*: `^#[A-Fa-f0-9]{6}$` |
| `color_text` | `str` | Optional | Color for the texts within the iFrame. Value should be a CSS hex color, e.g. "#FF9900"<br><br>**Constraints**: *Pattern*: `^#[A-Fa-f0-9]{6}$` |
| `radius_border` | `str` | Optional | Radius for the border of elements within the iFrame. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.options_1 import Options1

options_1 = Options1(
    color_border='#FF9900',
    color_border_selected='#FF9900',
    color_details='#FF9900',
    color_text='#FF9900',
    radius_border='5px',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

