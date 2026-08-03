
# Payment Dispute State Change

The payment dispute state change webhook is triggered when the state of a payment dispute changes (aligned with Visa Claims Resolution lifecycle).

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeStateChange`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `event_type` | [`EventType`](../../doc/models/event-type.md) | Optional | - |
| `event_id` | `uuid\|str` | Optional | Unique identifier |
| `occurred_at` | `datetime` | Optional | The timestamp when the webhook event occurred. In ISO 8601 with timezone e.g. 2024-01-01T12:00:00Z |
| `metadata` | [`WebhookMetadata`](../../doc/models/webhook-metadata.md) | Optional | The metadata of the webhook event. |
| `payload` | [payment.dispute.state-change.initiated](../../doc/models/payment-dispute-state-change-initiated.md) \| [payment.dispute.state-change.representment](../../doc/models/payment-dispute-state-change-representment.md) \| [payment.dispute.state-change.pre-arbitration](../../doc/models/payment-dispute-state-change-pre-arbitration.md) \| [payment.dispute.state-change.arbitration](../../doc/models/payment-dispute-state-change-arbitration.md) \| [payment.dispute.state-change.closed](../../doc/models/payment-dispute-state-change-closed.md) \| None | Optional | This is a container for any-of cases. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.created_by import CreatedBy
from klarna.models.event_type import EventType
from klarna.models.payment_dispute_details_base import PaymentDisputeDetailsBase
from klarna.models.payment_dispute_reason import PaymentDisputeReason
from klarna.models.payment_dispute_state import PaymentDisputeState
from klarna.models.payment_dispute_state_change import PaymentDisputeStateChange
from klarna.models.payment_dispute_state_change_initiated import PaymentDisputeStateChangeInitiated
from klarna.models.webhook_metadata import WebhookMetadata

payment_dispute_state_change = PaymentDisputeStateChange(
    event_type=EventType.ENUM_PAYMENTDISPUTESTATECHANGEINITIATED,
    event_id='00000f5c-0000-0000-0000-000000000000',
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
    payload=PaymentDisputeStateChangeInitiated(
        payment_dispute_id='payment_dispute_id8',
        order_id='order_id2',
        payment_transaction_id='payment_transaction_id2',
        state=PaymentDisputeState.CLOSED,
        updated_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
        dispute_reason=PaymentDisputeReason.PRODUCTS_DEFECTIVE_OR_NOT_AS_DESCRIBED,
        dispute_details=PaymentDisputeDetailsBase(
            dispute_amount=114,
            currency='currency2',
            created_by=CreatedBy.CUSTOMER,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        created_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
        payment_account_id='payment_account_id4',
        payment_account_reference='payment_account_reference6',
        payment_transaction_reference='payment_transaction_reference2',
        purchase_reference='purchase_reference8',
        merchant_reference_2='merchant_reference22',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

