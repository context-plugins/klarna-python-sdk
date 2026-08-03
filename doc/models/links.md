
# Links

HATEOAS links to any next and/or previous pages in a pagination context.

*This model accepts additional fields of type Any.*

## Structure

`Links`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `next` | [`Link`](../../doc/models/link.md) | Optional | A URI to a resource |
| `prev` | [`Link`](../../doc/models/link.md) | Optional | A URI to a resource |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.link import Link
from klarna.models.links import Links
from klarna.models.method import Method

links = Links(
    next=Link(
        href='href4',
        method=Method.PATCH,
        rel='rel8',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    prev=Link(
        href='href8',
        method=Method.POST,
        rel='rel2',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

