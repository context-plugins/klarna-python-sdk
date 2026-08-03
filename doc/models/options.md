
# Options

Additional configuration options for the dispute.

*This model accepts additional fields of type Any.*

## Structure

`Options`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `hold_policy` | [`HoldPolicy`](../../doc/models/hold-policy.md) | Optional | Defines when Klarna debits the Partner for any chargebacks and fees related to the dispute.<br><br>* `NONE` - Klarna debits the Partner when the dispute is closed, where relevant.<br>* `ON_DISPUTE_INITIATED` - Klarna holds the chargeback and fee amount when the dispute moves into `INITIATED` state, and releases it again if the Partner wins the dispute. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.hold_policy import HoldPolicy
from klarna.models.options import Options

options = Options(
    hold_policy=HoldPolicy.NONE,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

