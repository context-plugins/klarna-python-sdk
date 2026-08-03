
# Intent

Intent for the session. The field is designed to let partners inform Klarna of the purpose of the customer’s session.

## Enumeration

`Intent`

## Fields

| Name |
|  --- |
| `BUY` |
| `TOKENIZE` |
| `BUY_AND_TOKENIZE` |

## Example

```python
from klarna.models.intent import Intent

intent = Intent.BUY_AND_TOKENIZE
```

