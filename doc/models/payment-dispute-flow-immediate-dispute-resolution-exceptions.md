
# Payment Dispute Flow Immediate Dispute Resolution Exceptions

Exceptions that cause the dispute to be resolved immediately, bypassing the standard defense period.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeFlowImmediateDisputeResolutionExceptions`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `exception_type` | `str` | Required | The type of exception indicating immediate dispute resolution without a defense period. This is an open enum - clients should handle unknown values gracefully as new values may be added in the future.<br><br>**Open Enum - values:**<br><br>\| Value \| Description \|<br>\|-------\|-------------\|<br>\| `immediate_dispute_resolution` \| Dispute will be resolved immediately, bypassing the standard defense period \|<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `200` |
| `reason` | `str` | Required | The specific reason for immediate dispute resolution. This is an open enum - clients should handle unknown values gracefully as new values may be added in the future.<br><br>**Open Enum - values:**<br><br>\| Value \| Description \|<br>\|-------\|-------------\|<br>\| `fraudulent_partner` \| Defense period skipped as the partner has been identified as engaging in fraudulent activities \|<br>\| `dispute_mis_handled` \| Defense period skipped due to errors or mishandling in the earlier dispute resolution \|<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `200` |
| `description` | `str` | Required | Human-readable explanation of why the exception was applied. The description text should match the reason value as documented above.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `500` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.payment_dispute_flow_immediate_dispute_resolution_exceptions import PaymentDisputeFlowImmediateDisputeResolutionExceptions

payment_dispute_flow_immediate_dispute_resolution_exceptions = PaymentDisputeFlowImmediateDisputeResolutionExceptions(
    exception_type='IMMEDIATE_DISPUTE_RESOLUTION',
    reason='FRAUDULENT_PARTNER',
    description='Defense period skipped as the partner has been identified as engaging in fraudulent activities.',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

