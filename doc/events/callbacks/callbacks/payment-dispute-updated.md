
# Payment Dispute Updated

Webhook delivered when the dispute is updated without state change

## Headers

This event's request contains the following headers.

| Name |
|  --- |
| Klarna-Signature |
| Klarna-Signing-Key-ID |
| Content-Type |

## Payload Type

This event's request payload is of type [PaymentDisputeUpdated](../../../../doc/models/payment-dispute-updated.md).

## Payload Example

```json
{
  "event_type": "payment.dispute.updated.representment-deadline-extended",
  "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
  "occurred_at": "2020-05-08T12:00:00Z",
  "metadata": {
    "event_type": "payment.dispute.updated.representment-deadline-extended",
    "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
    "event_version": "v1",
    "correlation_id": "3223496a-c253-4c4a-8849-68121c0e99c8",
    "occurred_at": "2020-05-08T12:00:00Z",
    "webhook_id": "krn:notification:webhook:120e5b7e-abcd-4def-8a90-dca726e639b5",
    "merchant_id": "K000000",
    "live": true,
    "subject_account_id": "subject_account_id2",
    "recipient_account_id": "recipient_account_id0",
    "product_instance_id": "product_instance_id0",
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "payload": {
    "payment_dispute_id": "krn:network:us1:live:payment:dispute:5169719611111",
    "payment_transaction_id": "krn:payment:eu1:authorization:6debe89e-98c0-486e-b7a5-08a4f6df94b0",
    "order_id": "5c8ca572-5751-4f0a-ab2f-0a29aa845b37",
    "payment_transaction_reference": "f420e0e1-971b-417a-8ece-2626387eff36",
    "merchant_reference2": "501",
    "payment_capture_reference": "partner-capture-reference-1234",
    "capture_id": "0b812553-d263-4758-9057-a10961a71716",
    "payment_capture_id": "krn:payment:eu1:transaction:5c8ca572-5751-4f0a-ab2f-0a29aa845b37:capture:1",
    "capture_krn": "krn:mood-eu:capture:a2dcde7c-8b0a-4d56-9eec-7060057eed26",
    "payment_account_id": "krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b",
    "payment_account_reference": "REF995847",
    "state": "REPRESENTMENT",
    "updated_fields": {
      "evidence_response_deadline_at": "2020-05-22T00:00:00Z",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    "previous_fields": {
      "evidence_response_deadline_at": "2020-05-15T00:00:00Z"
    },
    "updated_at": "2020-05-01T12:00:00Z",
    "purchase_reference": "purchase_reference6",
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

## SDK Usage Example

```python
from flask import (
    Flask,
    Response,
    request,
)

from klarna.events.callbacks.callbacks_handler import (
    CallbacksHandler,
)
from klarna.events.unknown_event import UnknownEvent
from klarna.models.payment_dispute_updated import (
    PaymentDisputeUpdated,
)
from klarna.utilities.request_adapter import (
    to_core_request,
)

app = Flask(__name__)

@app.route("/callbacks", methods=[
    "POST",
])
def Callbacks() -> Response:
    # Step 1: Convert the incoming request using to_core_request (Django/Flask)
    #         or await to_core_request_async (FastAPI).
    core_req = to_core_request(request)

    # Step 2: Parse the request into a typed event.
    event = CallbacksHandler.parse_event(core_req)

    # Step 3: Pattern match for payment.dispute.updated only.
    if isinstance(event, PaymentDisputeUpdated):
        print("payment.dispute.updated received")
        # TODO: add handling logic
    elif isinstance(event, UnknownEvent):
        print("Unknown event")
        # TODO: add unknown event handling

    # Step 4: Return 200 OK to acknowledge receipt (adjust with other codes if needed).
    return Response(status=200)
```

## Accepted Server Responses

The server should responds with one of the following status codes:

| Status Code | Description |
|  --- | --- |
| 200 | Webhook accepted |

