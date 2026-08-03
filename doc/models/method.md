
# Method

The HTTP method to use when accessing the resource. Omitting this field implies GET.

## Enumeration

`Method`

## Fields

| Name |
|  --- |
| `GET` |
| `POST` |
| `PUT` |
| `DELETE` |
| `PATCH` |
| `OPTIONS` |
| `HEAD` |
| `TRACE` |
| `CONNECT` |

## Example

```python
from klarna.models.method import Method

method = Method.PUT
```

