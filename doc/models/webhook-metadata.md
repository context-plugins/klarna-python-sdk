
# Webhook Metadata

The metadata of the webhook event.

*This model accepts additional fields of type Any.*

## Structure

`WebhookMetadata`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `event_id` | `str` | Required | The unique identifier of the delivered event.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `event_type` | `str` | Required | The event type of the webhook.<br><br>**Constraints**: *Minimum Length*: `0` |
| `correlation_id` | `str` | Optional | The correlation id of the webhook.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `event_version` | `str` | Required | The version of the payload event schema.<br><br>**Constraints**: *Minimum Length*: `0` |
| `occurred_at` | `datetime` | Required | The timestamp when the event occurred. In ISO 8601 with timezone e.g. 2024-01-01T12:00:00Z |
| `subject_account_id` | `str` | Required | The unique identifier of the account for which the event has occurred.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `recipient_account_id` | `str` | Required | The unique identifier of the account that has configured the webhook and receives the notification.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `product_instance_id` | `str` | Optional | The unique identifier of the product instance.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `webhook_id` | `str` | Required | The unique identifier of the webhook that triggered the notification.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `live` | `bool` | Required | A boolean flag indicating whether the event is generated in a production environment. |
| `merchant_id` | `str` | Required | The unique identifier of the merchant for which the event has occurred. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.webhook_metadata import WebhookMetadata

webhook_metadata = WebhookMetadata(
    event_id='28ac927f-5ba7-4589-8bf7-1c8ada082343',
    event_type='event_type0',
    event_version='v2',
    occurred_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    subject_account_id='krn:partner:global:account:live:LWT2XJSE',
    recipient_account_id='krn:partner:global:account:live:LWT2XJSE',
    webhook_id='krn:partner:global:notification:webhook:120e5b7e-abcd-4def-8a90-dca726e639b5',
    live=True,
    merchant_id='K000000',
    correlation_id='28ac927f-5ba7-4589-8bf7-1c8ada082343',
    product_instance_id='krn:partner:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

