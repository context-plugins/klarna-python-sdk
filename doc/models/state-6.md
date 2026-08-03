
# State 6

The new state of the dispute after submitting the appeal. The dispute transitions to ARBITRATION state for Klarna review.

## Enumeration

`State6`

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
from klarna.models.state_6 import State6

state_6 = State6.ARBITRATION
```

