
# Reason Code

Reason code for why the order cancellation was rejected.

This field is only populated if status is `REJECTED`.

## Enumeration

`ReasonCode`

## Fields

| Name |
|  --- |
| `CARD_IN_USE` |
| `OTHER` |

## Example

```python
from klarna.models.reason_code import ReasonCode

reason_code = ReasonCode.CARD_IN_USE
```

