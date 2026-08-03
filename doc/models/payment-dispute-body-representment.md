
# Payment Dispute Body Representment

The dispute is in the representment state and evidence is being reviewed by Klarna.
It's not possible to reply to the evidence request in this state.

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeBodyRepresentment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Required | Unique identifier for the payment dispute<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `dispute_reason` | [`PaymentDisputeReason`](../../doc/models/payment-dispute-reason.md) | Required | Reason for creating the dispute. Possible values:<br><br>- REFUND_NOT_PROCESSED: Customer claims that they returned goods or canceled services, but the Partner has not issued a refund to the Customer through the Acquiring Partners integration or Klarna's Partner Portal<br>- PRODUCTS_OR_SERVICES_NOT_RECEIVED: Customer claims that they did not receive the goods or services because the Partner was unwilling or unable to provide the goods or services<br>- PRODUCTS_DEFECTIVE_OR_NOT_AS_DESCRIBED: Customer claims that they received the goods or services, but that they deviated from what was advertised in terms of authenticity, condition or in other ways defective<br>- PURCHASE_HIGH_RISK: Klarna identified this transaction as high risk. Cancel the order if possible; if already shipped, provide tracking details and attempt to stop delivery. Response required within 96 hours.<br>- INCORRECT_AMOUNT: Customer claims to have received a charge for purchase that is incorrect, for example, missing discounts, unadvertised shipping fees at the time of purchase, incorrect items listed on the invoice, or an order amount already paid directly to the Partner outside of the Klarna Network<br>- PURCHASE_UNAUTHORIZED: Customer claims they have never made the purchase<br>- NON_COMPLIANCE: For transactions where Klarna has identified that the Partner has entered the Risk Program and is in Major Breach under Section 15.4 Partner Responsibilities and a Customer has not successfully disputed the transaction under another Dispute Type<br>- NON_GUARANTEED_PAYMENT_PROGRAM: Klarna identified that the transaction was not paid by the Customer and reverses the Claim to the Acquiring Partner. Only applicable to the "Debit Risk" Payment Program |
| `state` | [`State`](../../doc/models/state.md) | Required | The current state of the dispute.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `order_id` | `str` | Required | The unique identifier of the payment transaction that is disputed<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_transaction_id` | `str` | Required | The unique identifier of the payment transaction that is disputed<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_account_id` | `str` | Required | Unique payment account identifier assigned by Klarna. This identifies the payment account associated with the disputed transaction.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `dispute_details` | [`PaymentDisputeDetailsBase`](../../doc/models/payment-dispute-details-base.md) | Required | Core dispute information including the disputed amount, transaction currency, and the party who initiated the dispute. |
| `created_at` | `datetime` | Required | Timestamp of when the dispute was created |
| `updated_at` | `datetime` | Required | Timestamp of when the dispute was last updated |
| `state_context` | [`StateContext1`](../../doc/models/state-context-1.md) | Required | Additional context specific to the current dispute state. Required in all states, with different schemas depending on the state. |
| `process_exceptions` | List[[PaymentDisputeFlowDisputeWindowExtensionExceptions](../../doc/models/payment-dispute-flow-dispute-window-extension-exceptions.md) \| [PaymentDisputeFlowImmediateDisputeResolutionExceptions](../../doc/models/payment-dispute-flow-immediate-dispute-resolution-exceptions.md)] \| None | Optional | Exceptions that may have occurred during the dispute flow, causing deviations from the standard dispute process.<br><br>Exception types include:<br><br>- DISPUTE_WINDOW_EXTENSION: The dispute window has been extended beyond the standard timeframe, allowing disputes to be opened outside the regular period.<br>- IMMEDIATE_DISPUTE_RESOLUTION: The dispute is resolved immediately without a standard defense period.<br><br>Each exception includes a specific reason and human-readable description explaining why the exception was applied.<br><br>**Constraints**: *Minimum Items*: `0`, *Maximum Items*: `3` |
| `payment_transaction_reference` | `str` | Optional | Reference to the payment or equivalent resource created on your side.<br>This will be exposed in the Payment Transaction webhooks for the purpose of correlating your resource with the Klarna Payment Transaction.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `purchase_reference` | `str` | Optional | Used for storing the customer-facing order number. It will be displayed to customers on the Klarna app and other communications. It will also be included in settlement reports for the purpose of reconciliation.<br>If you are a direct merchant with Klarna, this can be the same as `payment_transaction_reference`. If you are a PSP, this is the reference your merchant generated for their customer order.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `merchant_reference_2` | `str` | Optional | Can be used to store your internal reference to the order. This is generally an internal reference number that merchants use as alternate identifier that matches their internal ERP or Order Management system.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `capture_id` | `str` | Optional | Reference to the capture or equivalent resource created on your side.<br>This will be exposed in the Payment Transaction webhooks and included in the settlement file.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_capture_reference` | `str` | Optional | Reference to the capture or equivalent resource created on your side.<br>This will be exposed in the Payment Transaction webhooks and included in the settlement file.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `capture_krn` | `str` | Optional | Unique identifier for a created Payment Capture.<br><br>You should not make any assumption about the format of this identifier, you should treat it as an opaque string.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `payment_capture_id` | `str` | Optional | Unique identifier for a created Payment Capture.<br><br>You should not make any assumption about the format of this identifier, you should treat it as an opaque string.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `product_id` | `str` | Optional | Unique payment product identifier assigned by Klarna. This identifies the payment product instance associated with the disputed transaction.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_account_reference` | `str` | Optional | Partner-provided reference for the payment account associated with the disputed transaction.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `partner_account_id` | `str` | Optional | Unique identifier assigned by Klarna to the onboarded partner.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `customer_evidences` | [`List[PaymentDisputeCustomerProvidedEvidence]`](../../doc/models/payment-dispute-customer-provided-evidence.md) | Optional | List of evidence provided by the customer<br><br>**Constraints**: *Minimum Items*: `0`, *Maximum Items*: `2` |
| `previous_state` | [`PaymentDisputePreviousState`](../../doc/models/payment-dispute-previous-state.md) | Required | The previous state of the Dispute.<br><br>* `INITIATED` - Dispute initiated.<br>* `REPRESENTMENT` - Evidence review phase.<br>* `PRE_ARBITRATION` - Pre-arbitration phase with preliminary decision.<br>* `ARBITRATION` - Arbitration phase with final review by Klarna. |
| `representment` | [`PaymentDisputeRepresentment`](../../doc/models/payment-dispute-representment.md) | Required | Representment details for the current dispute |
| `configuration` | [`PaymentDisputeConfiguration`](../../doc/models/payment-dispute-configuration.md) | Optional | Configuration block that helps partners route dispute handling logic. base_framework identifies the dispute framework: FRAMEWORK_2026 for disputes routed through the V4 flow, FRAMEWORK_2020 for disputes created through the old disputes flow. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.attachment import Attachment
from klarna.models.created_by import CreatedBy
from klarna.models.partner_evidence import PartnerEvidence
from klarna.models.payment_dispute_body_representment import PaymentDisputeBodyRepresentment
from klarna.models.payment_dispute_details_base import PaymentDisputeDetailsBase
from klarna.models.payment_dispute_flow_dispute_window_extension_exceptions import PaymentDisputeFlowDisputeWindowExtensionExceptions
from klarna.models.payment_dispute_partner_evidence import PaymentDisputePartnerEvidence
from klarna.models.payment_dispute_previous_state import PaymentDisputePreviousState
from klarna.models.payment_dispute_reason import PaymentDisputeReason
from klarna.models.payment_dispute_representment import PaymentDisputeRepresentment
from klarna.models.payment_dispute_representment_previous_state import PaymentDisputeRepresentmentPreviousState
from klarna.models.payment_dispute_representment_request import PaymentDisputeRepresentmentRequest
from klarna.models.payment_dispute_representment_state import PaymentDisputeRepresentmentState
from klarna.models.state import State
from klarna.models.state_context_1 import StateContext1

payment_dispute_body_representment = PaymentDisputeBodyRepresentment(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    dispute_reason=PaymentDisputeReason.PRODUCTS_OR_SERVICES_NOT_RECEIVED,
    state=State.REPRESENTMENT,
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    dispute_details=PaymentDisputeDetailsBase(
        dispute_amount=114,
        currency='USD',
        created_by=CreatedBy.CUSTOMER,
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    state_context=StateContext1(
        partner_evidence=PaymentDisputePartnerEvidence(
            created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
            attachments=[
                Attachment(
                    payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
                    description='Shipment confirmation',
                    mime_type='image/jpeg',
                    url='/payment/disputes/krn:network:us1:live:payment:dispute:1234567890/attachments/1/download'
                )
            ],
            additional_information='additional_information8'
        ),
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    previous_state=PaymentDisputePreviousState.PRE_ARBITRATION,
    representment=PaymentDisputeRepresentment(
        state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
        previous_state=PaymentDisputeRepresentmentPreviousState.EVIDENCE_REQUESTED,
        expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
        request=PaymentDisputeRepresentmentRequest(
            additional_information='additional_information6',
            requested_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z')
        ),
        partner_evidence=PartnerEvidence(
            created_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            attachments=[
                Attachment(
                    payment_dispute_attachment_id='payment_dispute_attachment_id2',
                    description='description0',
                    mime_type='mime_type4',
                    url='url4'
                )
            ],
            additional_information='additional_information8'
        ),
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    process_exceptions=[
        PaymentDisputeFlowDisputeWindowExtensionExceptions(
            exception_type='DISPUTE_WINDOW_EXTENSION',
            reason='reason8',
            description='description6',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        PaymentDisputeFlowDisputeWindowExtensionExceptions(
            exception_type='DISPUTE_WINDOW_EXTENSION',
            reason='reason8',
            description='description6',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    product_id='krn:partner:global:account:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918',
    payment_account_reference='payment_account_ref',
    partner_account_id='krn:partner:global:account:live:LWT2XJSE',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

