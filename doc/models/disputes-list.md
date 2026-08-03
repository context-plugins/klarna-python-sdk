
# Disputes List

## Structure

`DisputesList`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `disputes` | List[[PaymentDisputeBodyDisputeInitiated](../../doc/models/payment-dispute-body-dispute-initiated.md) \| [PaymentDisputeBodyRepresentment](../../doc/models/payment-dispute-body-representment.md) \| [PaymentDisputeBodyPreArbitration](../../doc/models/payment-dispute-body-pre-arbitration.md) \| [PaymentDisputeBodyArbitration](../../doc/models/payment-dispute-body-arbitration.md) \| [PaymentDisputeBodyClosed](../../doc/models/payment-dispute-body-closed.md)] | Required | - |
| `pagination` | [`PaginationResponse`](../../doc/models/pagination-response.md) | Required | A paginated response will return this object with information about the size and links to any next and previous pages. |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.attachment import Attachment
from klarna.models.created_by import CreatedBy
from klarna.models.disputes_list import DisputesList
from klarna.models.link import Link
from klarna.models.links import Links
from klarna.models.method import Method
from klarna.models.pagination_response import PaginationResponse
from klarna.models.partner_evidence import PartnerEvidence
from klarna.models.payment_dispute_body_dispute_initiated import PaymentDisputeBodyDisputeInitiated
from klarna.models.payment_dispute_details_base import PaymentDisputeDetailsBase
from klarna.models.payment_dispute_flow_dispute_window_extension_exceptions import PaymentDisputeFlowDisputeWindowExtensionExceptions
from klarna.models.payment_dispute_reason import PaymentDisputeReason
from klarna.models.payment_dispute_representment import PaymentDisputeRepresentment
from klarna.models.payment_dispute_representment_previous_state import PaymentDisputeRepresentmentPreviousState
from klarna.models.payment_dispute_representment_request import PaymentDisputeRepresentmentRequest
from klarna.models.payment_dispute_representment_state import PaymentDisputeRepresentmentState
from klarna.models.state import State
from klarna.models.state_context import StateContext

disputes_list = DisputesList(
    disputes=[
        PaymentDisputeBodyDisputeInitiated(
            payment_dispute_id='payment_dispute_id6',
            dispute_reason=PaymentDisputeReason.PURCHASE_HIGH_RISK,
            state=State.INITIATED,
            order_id='order_id0',
            payment_transaction_id='payment_transaction_id0',
            payment_account_id='payment_account_id2',
            dispute_details=PaymentDisputeDetailsBase(
                dispute_amount=114,
                currency='currency2',
                created_by=CreatedBy.CUSTOMER,
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            created_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            updated_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            state_context=StateContext(
                representment=PaymentDisputeRepresentment(
                    state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
                    previous_state=PaymentDisputeRepresentmentPreviousState.EVIDENCE_REQUESTED,
                    expires_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
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
            payment_transaction_reference='payment_transaction_reference6',
            purchase_reference='purchase_reference6',
            merchant_reference_2='merchant_reference20',
            capture_id='capture_id8',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    pagination=PaginationResponse(
        count=20,
        last_item='Fvt0G2tMGTuGx',
        first_item='Bxp4Z3sWFXmKq',
        total=1025,
        links=Links(
            next=Link(
                href='href4',
                method=Method.PATCH,
                rel='rel8',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            prev=Link(
                href='href8',
                method=Method.POST,
                rel='rel2',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    )
)
```

