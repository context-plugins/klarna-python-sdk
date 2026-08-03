
# Payment Dispute Updated

There was a non-state-changing update on the payment dispute.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeUpdated`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `event_type` | [`EventType1`](../../doc/models/event-type-1.md) | Optional | The type of the event. For this webhook, the value will always be `payment.dispute.updated.representment-deadline-extended`. |
| `event_id` | `uuid\|str` | Optional | Unique identifier |
| `occurred_at` | `datetime` | Optional | The timestamp when the webhook event occurred. In ISO 8601 with timezone e.g. 2024-01-01T12:00:00Z |
| `metadata` | [`WebhookMetadata`](../../doc/models/webhook-metadata.md) | Optional | The metadata of the webhook event. |
| `payload` | [`Payload`](../../doc/models/payload.md) | Optional | The dispute fields that has been updated. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.event_type_1 import EventType1
from klarna.models.payload import Payload
from klarna.models.payment_dispute_state import PaymentDisputeState
from klarna.models.payment_dispute_updated import PaymentDisputeUpdated
from klarna.models.updated_fields import UpdatedFields
from klarna.models.webhook_metadata import WebhookMetadata

payment_dispute_updated = PaymentDisputeUpdated(
    event_type=EventType1.ENUM_PAYMENTDISPUTEUPDATEDREPRESENTMENTDEADLINEEXTENDED,
    event_id='00001b1e-0000-0000-0000-000000000000',
    occurred_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    metadata=WebhookMetadata(
        event_id='event_id2',
        event_type='event_type6',
        event_version='event_version2',
        occurred_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
        subject_account_id='subject_account_id2',
        recipient_account_id='recipient_account_id0',
        webhook_id='webhook_id0',
        live=False,
        merchant_id='merchant_id6',
        correlation_id='correlation_id0',
        product_instance_id='product_instance_id0',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    payload=Payload(
        payment_dispute_id='payment_dispute_id6',
        order_id='order_id0',
        payment_transaction_id='payment_transaction_id0',
        state=PaymentDisputeState.ARBITRATION,
        updated_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
        updated_fields=UpdatedFields(
            evidence_response_deadline_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        payment_account_id='payment_account_id2',
        payment_account_reference='payment_account_reference4',
        payment_transaction_reference='payment_transaction_reference4',
        purchase_reference='purchase_reference6',
        merchant_reference_2='merchant_reference20',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

