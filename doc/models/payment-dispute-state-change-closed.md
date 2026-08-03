
# Payment Dispute State Change Closed

`CLOSED` - The Dispute is closed.

* Closing reason: `WON` - Dispute is closed in favor of Partner
* Closing reason: `LOST` - Dispute is closed in favor of Customer and a chargeback has been triggered towards Partner

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeStateChangeClosed`

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
| `previous_state` | [`PaymentDisputePreviousState`](../../doc/models/payment-dispute-previous-state.md) | Optional | The previous state of the Dispute.<br><br>* `INITIATED` - Dispute initiated.<br>* `REPRESENTMENT` - Evidence review phase.<br>* `PRE_ARBITRATION` - Pre-arbitration phase with preliminary decision.<br>* `ARBITRATION` - Arbitration phase with final review by Klarna. |
| `dispute_outcome` | [`DisputeOutcome`](../../doc/models/dispute-outcome.md) | Required | Outcome of the arbitration. Possible values:<br><br>- WON: Partner won the dispute<br>- LOST: Partner lost the dispute |
| `dispute_outcome_detailed` | `str` | Required | Detailed outcome of the dispute closure. This is an open enum - clients should handle unknown values gracefully as new values may be added in the future.<br><br>**Open Enum - values:**<br><br>\| Value \| Description \|<br>\|-------\|-------------\|<br>\| `partner_did_not_reply_to_dispute_request` \| Partner did not reply to dispute request \|<br>\| `partner_did_not_follow_klarnas_shipping_policy` \| Partner did not follow Klarna's shipping policy \|<br>\| `partner_did_not_adjust_statement_on_klarnas_request` \| Partner did not adjust statement on Klarna's request \|<br>\| `shipped_stop_requested_order` \| Shipped stop requested order \|<br>\| `invoice_incorrectly_activated` \| Invoice incorrectly activated \|<br>\| `order_missing_consumer_details` \| Order missing consumer details \|<br>\| `shipped_to_non_approved_address` \| Shipped to non-approved address \|<br>\| `incorrect_invalid_delivery_in_physical_store` \| Incorrect invalid delivery in physical store \|<br>\| `service_digital_goods_klarna_does_not_take_risk` \| Service digital goods Klarna does not take risk \|<br>\| `partner_provided_valid_shipping_details` \| Partner provided valid shipping details \|<br>\| `partner_informed_about_invalid_return` \| Partner informed about invalid return \|<br>\| `partner_informs_that_invoice_is_correct` \| Partner informs that invoice is correct \|<br>\| `partner_has_not_received_payment_or_payment_to_3rd_party` \| Partner has not received payment or payment to 3rd party \|<br>\| `partner_has_refunded_payment_to_customer` \| Partner has refunded payment to customer \|<br>\| `partner_solved_the_dispute_with_the_customer` \| Partner solved the dispute with the customer \|<br>\| `partner_informed_about_invalid_dispute` \| Partner informed about invalid dispute \|<br>\| `reactivated_invoice_statement` \| Reactivated invoice statement \|<br>\| `customer_cancelled_dispute` \| Customer cancelled dispute \|<br>\| `incorrect_payment_details_used_refunded` \| Incorrect payment details used refunded \|<br>\| `fully_paid_after_escalation` \| Fully paid after escalation \|<br>\| `refund_issued_by_partner_after_escalation` \| Refund issued by partner after escalation \|<br>\| `partner_accepted_the_loss` \| Partner accepted the loss \|<br>\| `non_approved_address_recipient` \| Non-approved address recipient \|<br>\| `insufficient_proof_of_delivery` \| Insufficient proof of delivery \|<br>\| `non_physical_goods` \| Non-physical goods \|<br>\| `insufficient_recipient_check_at_pickup_delivery` \| Insufficient recipient check at pickup delivery \|<br>\| `partner_did_not_respond_to_stop_request` \| Partner did not respond to stop request \|<br>\| `no_proof_of_delivery` \| No proof of delivery \|<br>\| `partner_successfully_canceled_full_order` \| Partner successfully canceled full order \|<br>\| `partner_successfully_canceled_partial_order` \| Partner successfully canceled partial order \|<br>\| `partner_did_not_respond_but_provided_full_shipping_information_when_order_was_captured` \| Partner did not respond but provided full shipping information when order was captured \|<br>\| `partner_did_not_respond_but_provided_partial_shipping_information_when_order_was_captured` \| Partner did not respond but provided partial shipping information when order was captured \|<br>\| `partner_did_not_respond_and_did_not_provide_shipping_information_when_order_was_captured` \| Partner did not respond and did not provide shipping information when order was captured \|<br>\| `partner_captured_full_order_but_provided_full_shipping_information_via_response` \| Partner captured full order but provided full shipping information via response \|<br>\| `partner_captured_full_order_but_provided_partial_shipping_information_via_response` \| Partner captured full order but provided partial shipping information via response \|<br>\| `partner_responded_but_the_order_was_sent_without_shipping_information` \| Partner responded but the order was sent without shipping information \|<br>\| `partner_claimed_they_would_cancel_the_order_but_did_not` \| Partner claimed they would cancel the order but did not \|<br>\| `partner_captured_partial_order_but_provided_shipping_information_via_response` \| Partner captured partial order but provided shipping information via response \|<br>\| `partner_did_not_perform_promised_refund` \| Partner did not perform promised refund \|<br>\| `klarna_resolved_dispute_in_partner_favor` \| Klarna resolved dispute in partner favor \|<br>\| `could_not_send_another_request` \| Could not send another request \|<br>\| `klarna_resolved_due_wrong_dispute_reason_chosen` \| Klarna resolved due wrong dispute reason chosen \|<br>\| `dispute_opened_under_wrong_dispute_reason` \| Dispute opened under wrong dispute reason \|<br>\| `partner_did_not_update_order_as_requested` \| Partner did not update order as requested \|<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `200` |
| `closed_at` | `datetime` | Required | Timestamp in ISO 8601 with timezone<br>Valid examples:<br><br>- 2025-06-24T05:51<br>- 2025-06-24T05:51:48Z<br>- 2025-06-24T05:51:48.1Z<br>- 2025-06-24T05:51:48.12Z<br>- 2025-06-24T05:51:48.123Z |
| `configuration` | [`PaymentDisputeConfiguration`](../../doc/models/payment-dispute-configuration.md) | Optional | Configuration block that helps partners route dispute handling logic. base_framework identifies the dispute framework: FRAMEWORK_2026 for disputes routed through the V4 flow, FRAMEWORK_2020 for disputes created through the old disputes flow. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.dispute_outcome import DisputeOutcome
from klarna.models.payment_dispute_state import PaymentDisputeState
from klarna.models.payment_dispute_state_change_closed import PaymentDisputeStateChangeClosed

payment_dispute_state_change_closed = PaymentDisputeStateChangeClosed(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    state=PaymentDisputeState.INITIATED,
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    dispute_outcome=DisputeOutcome.WON,
    dispute_outcome_detailed='PARTNER_DID_NOT_REPLY_TO_DISPUTE_REQUEST',
    closed_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    payment_account_reference='payment_account_ref',
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

