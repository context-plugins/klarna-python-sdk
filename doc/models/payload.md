
# Payload

The dispute fields that has been updated.

*This model accepts additional fields of type Any.*

## Structure

`Payload`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Required | Unique identifier for the payment dispute<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `order_id` | `str` | Required | Unique identifier for a created Payment Transaction. This identifier can be used to manage the Payment Transaction through the Payment Transaction API.<br><br>You should not make any assumption about the format of this identifier, you should treat it as an opaque string.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_transaction_id` | `str` | Required | Unique identifier for a created Payment Transaction. This identifier can be used to manage the Payment Transaction through the Payment Transaction API.<br><br>You should not make any assumption about the format of this identifier, you should treat it as an opaque string.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_account_id` | `str` | Optional | Unique payment account identifier assigned by Klarna.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_account_reference` | `str` | Optional | Partner-provided reference for the payment account.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_transaction_reference` | `str` | Optional | Reference to the payment or equivalent resource created on your side.<br>This will be exposed in the Payment Transaction webhooks for the purpose of correlating your resource with the Klarna Payment Transaction.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `purchase_reference` | `str` | Optional | Used for storing the customer-facing order number. It will be displayed to customers on the Klarna app and other communications. It will also be included in settlement reports for the purpose of reconciliation.<br>If you are a direct merchant with Klarna, this can be the same as `payment_transaction_reference`. If you are a PSP, this is the reference your merchant generated for their customer order.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `merchant_reference_2` | `str` | Optional | Can be used to store your internal reference to the order. This is generally an internal reference number that merchants use as alternate identifier that matches their internal ERP or Order Management system.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `capture_id` | `str` | Optional | Reference to the capture or equivalent resource created on your side.<br>This will be exposed in the Payment Transaction webhooks and included in the settlement file.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_capture_reference` | `str` | Optional | Reference to the capture or equivalent resource created on your side.<br>This will be exposed in the Payment Transaction webhooks and included in the settlement file.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `capture_krn` | `str` | Optional | Unique identifier for a created Payment Capture.<br><br>You should not make any assumption about the format of this identifier, you should treat it as an opaque string.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `payment_capture_id` | `str` | Optional | Unique identifier for a created Payment Capture.<br><br>You should not make any assumption about the format of this identifier, you should treat it as an opaque string.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `state` | [`PaymentDisputeState`](../../doc/models/payment-dispute-state.md) | Required | The current state of the Dispute.<br><br>* `INITIATED` - Dispute initiated. Klarna reviews case details and may request Partner response within deadline.<br>* `REPRESENTMENT` - Evidence review phase. Partner has submitted evidence and Klarna is reviewing the representment case.<br>* `PRE_ARBITRATION` - Pre-arbitration phase. Preliminary decision made. Partner has opportunity to accept or challenge the preliminary decision.<br>* `ARBITRATION` - Arbitration phase. Final review by Klarna. Binding decision will be made.<br>* `CLOSED` - Dispute is closed. Check `dispute_outcome` and `dispute_outcome_detailed` for further information. |
| `updated_at` | `datetime` | Required | Timestamp in ISO 8601 with timezone<br>Valid examples:<br><br>- 2025-06-24T05:51<br>- 2025-06-24T05:51:48Z<br>- 2025-06-24T05:51:48.1Z<br>- 2025-06-24T05:51:48.12Z<br>- 2025-06-24T05:51:48.123Z |
| `currency` | `str` | Optional | The currency of the dispute amount<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{3}$` |
| `updated_fields` | [`UpdatedFields`](../../doc/models/updated-fields.md) | Required | The new values of the updated fields. |
| `previous_fields` | [`PreviousFields`](../../doc/models/previous-fields.md) | Optional | The previous values of the updated fields. |
| `configuration` | [`PaymentDisputeConfiguration`](../../doc/models/payment-dispute-configuration.md) | Optional | Configuration block that helps partners route dispute handling logic. base_framework identifies the dispute framework: FRAMEWORK_2026 for disputes routed through the V4 flow, FRAMEWORK_2020 for disputes created through the old disputes flow. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.payload import Payload
from klarna.models.payment_dispute_state import PaymentDisputeState
from klarna.models.updated_fields import UpdatedFields

payload = Payload(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    state=PaymentDisputeState.ARBITRATION,
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    updated_fields=UpdatedFields(
        evidence_response_deadline_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    payment_account_reference='payment_account_ref',
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    currency='USD',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

