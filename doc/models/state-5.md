
# State 5

The new state of the dispute after submitting the response. The dispute transitions to REPRESENTMENT state for Klarna review.

## Enumeration

`State5`

## Fields

| Name |
|  --- |
| `INITIATED` |
| `REPRESENTMENT` |
| `PRE_ARBITRATION` |
| `ARBITRATION` |
| `CLOSED` |

## Example

```python
from klarna.models.state_5 import State5

state_5 = State5.CLOSED
```

