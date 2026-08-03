
# Payment Dispute Flow Dispute Window Extension Exceptions

Exceptions that extend the dispute window beyond the standard timeframe, allowing disputes to be opened outside the regular dispute opening period.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeFlowDisputeWindowExtensionExceptions`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `exception_type` | `str` | Required | The type of exception indicating the dispute window has been extended. This is an open enum - clients should handle unknown values gracefully as new values may be added in the future.<br><br>**Open Enum - values:**<br><br>\| Value \| Description \|<br>\|-------\|-------------\|<br>\| `dispute_window_extension` \| Dispute window has been extended beyond the standard timeframe \|<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `200` |
| `reason` | `str` | Required | The specific reason for extending the dispute window. This is an open enum - clients should handle unknown values gracefully as new values may be added in the future.<br><br>**Open Enum - values:**<br><br>\| Value \| Description \|<br>\|-------\|-------------\|<br>\| `dispute_mis_handled` \| Dispute window extended due to errors or mishandling in the previous dispute process \|<br>\| `regulatory_requirement` \| Dispute window extended to comply with applicable legal or regulatory obligations \|<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `200` |
| `description` | `str` | Required | Human-readable explanation of why the exception was applied. The description text should match the reason value as documented above.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `500` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.payment_dispute_flow_dispute_window_extension_exceptions import PaymentDisputeFlowDisputeWindowExtensionExceptions

payment_dispute_flow_dispute_window_extension_exceptions = PaymentDisputeFlowDisputeWindowExtensionExceptions(
    exception_type='DISPUTE_WINDOW_EXTENSION',
    reason='DISPUTE_MIS_HANDLED',
    description='Dispute window extended due to errors or mishandling in the previous dispute process.',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

