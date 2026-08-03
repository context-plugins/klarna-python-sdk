
# Link

A URI to a resource

*This model accepts additional fields of type Any.*

## Structure

`Link`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `href` | `str` | Required | The URI to the resource<br><br>**Constraints**: *Minimum Length*: `0` |
| `method` | [`Method`](../../doc/models/method.md) | Optional | The HTTP method to use when accessing the resource. Omitting this field implies GET. |
| `rel` | `str` | Optional | A descriptive relation indicating the link's purpose or relationship to the current resource<br><br>**Constraints**: *Minimum Length*: `0` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.link import Link
from klarna.models.method import Method

link = Link(
    href='https://api-global.klarna.com/v1/settlement/payouts?size=20&starting_after=Fvt0G2tMGTuGx',
    method=Method.GET,
    rel='Get the next page of results',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

