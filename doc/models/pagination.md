
# Pagination

## Structure

`Pagination`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `count` | `int` | Required | The amount of elements in the current result |
| `total` | `int` | Optional | The total amount of elements that are available |
| `next` | `str` | Optional | The URI to the next "page" of results. |
| `prev` | `str` | Optional | The URI to the previous "page" of results. |
| `offset` | `int` | Optional | The current offset. Describes "where" in a collection the current starts. |

## Example

```python
from klarna.models.pagination import Pagination

pagination = Pagination(
    count=10,
    total=42,
    next='http://example.com/collection?offset=21&size=10',
    prev='http://example.com/collection?offset=0&size=10',
    offset=10
)
```

