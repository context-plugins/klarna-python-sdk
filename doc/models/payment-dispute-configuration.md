
# Payment Dispute Configuration

Configuration block that helps partners route dispute handling logic. base_framework identifies the dispute framework: FRAMEWORK_2026 for disputes routed through the V4 flow, FRAMEWORK_2020 for disputes created through the old disputes flow.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeConfiguration`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `base_framework` | [`BaseFramework`](../../doc/models/base-framework.md) | Required | Dispute framework version. |
| `options` | [`Options`](../../doc/models/options.md) | Optional | Additional configuration options for the dispute. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.base_framework import BaseFramework
from klarna.models.hold_policy import HoldPolicy
from klarna.models.options import Options
from klarna.models.payment_dispute_configuration import PaymentDisputeConfiguration

payment_dispute_configuration = PaymentDisputeConfiguration(
    base_framework=BaseFramework.FRAMEWORK_2020,
    options=Options(
        hold_policy=HoldPolicy.NONE,
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

