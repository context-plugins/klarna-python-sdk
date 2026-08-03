
# Dispute Outcome

Outcome of the arbitration. Possible values:

- WON: Partner won the dispute
- LOST: Partner lost the dispute

## Enumeration

`DisputeOutcome`

## Fields

| Name |
|  --- |
| `WON` |
| `LOST` |

## Example

```python
from klarna.models.dispute_outcome import DisputeOutcome

dispute_outcome = DisputeOutcome.WON
```

