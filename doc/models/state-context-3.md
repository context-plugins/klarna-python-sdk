
# State Context 3

Additional context specific to the current dispute state. Required in all states, with different schemas depending on the state.

*This model accepts additional fields of type Any.*

## Structure

`StateContext3`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `dispute_outcome` | [`DisputeOutcome`](../../doc/models/dispute-outcome.md) | Required | Outcome of the arbitration. Possible values:<br><br>- WON: Partner won the dispute<br>- LOST: Partner lost the dispute |
| `dispute_outcome_detailed` | `str` | Required | Detailed outcome of the dispute closure. This is an open enum - clients should handle unknown values gracefully as new values may be added in the future.<br><br>**Open Enum - values:**<br><br>\| Value \| Description \|<br>\|-------\|-------------\|<br>\| `partner_did_not_reply_to_dispute_request` \| Partner did not reply to dispute request \|<br>\| `partner_did_not_follow_klarnas_shipping_policy` \| Partner did not follow Klarna's shipping policy \|<br>\| `partner_did_not_adjust_statement_on_klarnas_request` \| Partner did not adjust statement on Klarna's request \|<br>\| `shipped_stop_requested_order` \| Shipped stop requested order \|<br>\| `invoice_incorrectly_activated` \| Invoice incorrectly activated \|<br>\| `order_missing_consumer_details` \| Order missing consumer details \|<br>\| `shipped_to_non_approved_address` \| Shipped to non-approved address \|<br>\| `incorrect_invalid_delivery_in_physical_store` \| Incorrect invalid delivery in physical store \|<br>\| `service_digital_goods_klarna_does_not_take_risk` \| Service digital goods Klarna does not take risk \|<br>\| `partner_provided_valid_shipping_details` \| Partner provided valid shipping details \|<br>\| `partner_informed_about_invalid_return` \| Partner informed about invalid return \|<br>\| `partner_informs_that_invoice_is_correct` \| Partner informs that invoice is correct \|<br>\| `partner_has_not_received_payment_or_payment_to_3rd_party` \| Partner has not received payment or payment to 3rd party \|<br>\| `partner_has_refunded_payment_to_customer` \| Partner has refunded payment to customer \|<br>\| `partner_solved_the_dispute_with_the_customer` \| Partner solved the dispute with the customer \|<br>\| `partner_informed_about_invalid_dispute` \| Partner informed about invalid dispute \|<br>\| `reactivated_invoice_statement` \| Reactivated invoice statement \|<br>\| `customer_cancelled_dispute` \| Customer cancelled dispute \|<br>\| `incorrect_payment_details_used_refunded` \| Incorrect payment details used refunded \|<br>\| `fully_paid_after_escalation` \| Fully paid after escalation \|<br>\| `refund_issued_by_partner_after_escalation` \| Refund issued by partner after escalation \|<br>\| `partner_accepted_the_loss` \| Partner accepted the loss \|<br>\| `non_approved_address_recipient` \| Non-approved address recipient \|<br>\| `insufficient_proof_of_delivery` \| Insufficient proof of delivery \|<br>\| `non_physical_goods` \| Non-physical goods \|<br>\| `insufficient_recipient_check_at_pickup_delivery` \| Insufficient recipient check at pickup delivery \|<br>\| `partner_did_not_respond_to_stop_request` \| Partner did not respond to stop request \|<br>\| `no_proof_of_delivery` \| No proof of delivery \|<br>\| `partner_successfully_canceled_full_order` \| Partner successfully canceled full order \|<br>\| `partner_successfully_canceled_partial_order` \| Partner successfully canceled partial order \|<br>\| `partner_did_not_respond_but_provided_full_shipping_information_when_order_was_captured` \| Partner did not respond but provided full shipping information when order was captured \|<br>\| `partner_did_not_respond_but_provided_partial_shipping_information_when_order_was_captured` \| Partner did not respond but provided partial shipping information when order was captured \|<br>\| `partner_did_not_respond_and_did_not_provide_shipping_information_when_order_was_captured` \| Partner did not respond and did not provide shipping information when order was captured \|<br>\| `partner_captured_full_order_but_provided_full_shipping_information_via_response` \| Partner captured full order but provided full shipping information via response \|<br>\| `partner_captured_full_order_but_provided_partial_shipping_information_via_response` \| Partner captured full order but provided partial shipping information via response \|<br>\| `partner_responded_but_the_order_was_sent_without_shipping_information` \| Partner responded but the order was sent without shipping information \|<br>\| `partner_claimed_they_would_cancel_the_order_but_did_not` \| Partner claimed they would cancel the order but did not \|<br>\| `partner_captured_partial_order_but_provided_shipping_information_via_response` \| Partner captured partial order but provided shipping information via response \|<br>\| `partner_did_not_perform_promised_refund` \| Partner did not perform promised refund \|<br>\| `klarna_resolved_dispute_in_partner_favor` \| Klarna resolved dispute in partner favor \|<br>\| `could_not_send_another_request` \| Could not send another request \|<br>\| `klarna_resolved_due_wrong_dispute_reason_chosen` \| Klarna resolved due wrong dispute reason chosen \|<br>\| `dispute_opened_under_wrong_dispute_reason` \| Dispute opened under wrong dispute reason \|<br>\| `partner_did_not_update_order_as_requested` \| Partner did not update order as requested \|<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `200` |
| `closed_at` | `datetime` | Required | Timestamp of when the dispute was closed |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.dispute_outcome import DisputeOutcome
from klarna.models.state_context_3 import StateContext3

state_context_3 = StateContext3(
    dispute_outcome=DisputeOutcome.WON,
    dispute_outcome_detailed='PARTNER_DID_NOT_REPLY_TO_DISPUTE_REQUEST',
    closed_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

