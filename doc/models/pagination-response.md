
# Pagination Response

A paginated response will return this object with information about the size and links to any next and previous pages.

*This model accepts additional fields of type Any.*

## Structure

`PaginationResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `last_item` | `str` | Optional | Cursor referring to last item in the returned results. Can be used for getting the next page together with "starting_after". Will be null if there are no more items.<br><br>**Constraints**: *Minimum Length*: `0` |
| `first_item` | `str` | Optional | Cursor referring to first item in the returned results. Can be used for getting the previous page together with "ending_before". May be null if there is no previous page or stepping back is not supported.<br><br>**Constraints**: *Minimum Length*: `0` |
| `count` | `int` | Required | The number of returned items. |
| `total` | `int` | Optional | The total number of items available. |
| `links` | [`Links`](../../doc/models/links.md) | Optional | HATEOAS links to any next and/or previous pages in a pagination context. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.link import Link
from klarna.models.links import Links
from klarna.models.method import Method
from klarna.models.pagination_response import PaginationResponse

pagination_response = PaginationResponse(
    count=20,
    last_item='Fvt0G2tMGTuGx',
    first_item='Bxp4Z3sWFXmKq',
    total=1025,
    links=Links(
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
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

