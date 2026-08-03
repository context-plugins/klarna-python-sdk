
# Hold Policy

Defines when Klarna debits the Partner for any chargebacks and fees related to the dispute.

* `NONE` - Klarna debits the Partner when the dispute is closed, where relevant.
* `ON_DISPUTE_INITIATED` - Klarna holds the chargeback and fee amount when the dispute moves into `INITIATED` state, and releases it again if the Partner wins the dispute.

## Enumeration

`HoldPolicy`

## Fields

| Name |
|  --- |
| `NONE` |
| `ON_DISPUTE_INITIATED` |

## Example

```python
from klarna.models.hold_policy import HoldPolicy

hold_policy = HoldPolicy.NONE
```

