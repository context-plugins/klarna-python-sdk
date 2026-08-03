
# Payment Dispute Representment

Representment details for the current dispute

*This model accepts additional fields of type Any.*

## Structure

`PaymentDisputeRepresentment`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `state` | [`PaymentDisputeRepresentmentState`](../../doc/models/payment-dispute-representment-state.md) | Required | The current state of the Dispute Evidence Request.<br><br>* `EVIDENCE_REQUESTED` - Partner can reply to the request.<br>* `EVIDENCE_RECEIVED` - Evidence is being reviewed by Klarna, it's not possible to reply to the request.<br>* `EVIDENCE_REQUEST_EXPIRED` - Request time expired, it's not possible to reply to the request. The dispute will result in outcome LOST if partner does not respond before the deadline.<br>* `EVIDENCE_WAIVED` - Partner accepted the dispute loss in INITIATED state using the accept-loss endpoint. No further action possible.<br>* `REPRESENTMENT_AUTOMATICALLY_REJECTED` - Dispute representment automatically rejected because the dispute amount falls below the partner's configured threshold. Disputes below this threshold are automatically accepted as LOST. No further action possible. |
| `previous_state` | [`PaymentDisputeRepresentmentPreviousState`](../../doc/models/payment-dispute-representment-previous-state.md) | Optional | The previous state of the Dispute Evidence Request.<br><br>* `EVIDENCE_REQUESTED` - Partner can reply to the request. |
| `expires_at` | `datetime` | Optional | Deadline date for a partner to accept or escalate to arbitration |
| `request` | [`PaymentDisputeRepresentmentRequest`](../../doc/models/payment-dispute-representment-request.md) | Optional | Request for information towards the associated partner |
| `partner_evidence` | [`PartnerEvidence`](../../doc/models/partner-evidence.md) | Optional | Evidence submitted by the partner in response to the representment request. Only present in PRE_ARBITRATION, ARBITRATION, or CLOSED states when showing historical representment data, and only if the partner has responded. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.attachment import Attachment
from klarna.models.partner_evidence import PartnerEvidence
from klarna.models.payment_dispute_representment import PaymentDisputeRepresentment
from klarna.models.payment_dispute_representment_previous_state import PaymentDisputeRepresentmentPreviousState
from klarna.models.payment_dispute_representment_request import PaymentDisputeRepresentmentRequest
from klarna.models.payment_dispute_representment_state import PaymentDisputeRepresentmentState

payment_dispute_representment = PaymentDisputeRepresentment(
    state=PaymentDisputeRepresentmentState.EVIDENCE_REQUESTED,
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
)
```

