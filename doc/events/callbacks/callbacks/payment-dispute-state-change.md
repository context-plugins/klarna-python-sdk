
# Payment Dispute State-Change

Webhook delivered when the dispute state changes

## Headers

This event's request contains the following headers.

| Name |
|  --- |
| Klarna-Signature |
| Klarna-Signing-Key-ID |
| Content-Type |

## Payload Type

This event's request payload is of type [PaymentDisputeStateChange](../../../../doc/models/payment-dispute-state-change.md).

## Payload Example

### Payment dispute initiated webhook

```json
{
  "event_type": "payment.dispute.state-change.initiated",
  "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
  "occurred_at": "2024-01-01T12:00:00Z",
  "metadata": {
    "event_type": "payment.dispute.state-change.initiated",
    "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
    "event_version": "v1",
    "correlation_id": "3223496a-c253-4c4a-8849-68121c0e99c8",
    "occurred_at": "2024-01-01T12:00:00Z",
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
    "state": "INITIATED",
    "dispute_reason": "REFUND_NOT_PROCESSED",
    "representment": {
      "state": "EVIDENCE_REQUESTED",
      "expires_at": "2025-01-22T09:45:00Z",
      "request": {
        "requested_at": "2025-01-01T09:45:00Z",
        "additional_information": "Dear partner Team,\nTo help us resolve this dispute, please provide proof of delivery, including tracking information, delivery confirmation, and any signature or documentation showing the customer received the order."
      }
    },
    "dispute_details": {
      "dispute_amount": 39900,
      "currency": "EUR",
      "created_by": "CUSTOMER",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    "created_at": "2020-04-15T08:31:00Z",
    "updated_at": "2020-04-15T08:31:00Z",
    "purchase_reference": "purchase_reference8",
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

### Payment dispute representment webhook

```json
{
  "event_type": "payment.dispute.state-change.representment",
  "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
  "occurred_at": "2024-01-01T12:00:00Z",
  "metadata": {
    "event_type": "payment.dispute.state-change.representment",
    "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
    "event_version": "v1",
    "correlation_id": "3223496a-c253-4c4a-8849-68121c0e99c8",
    "occurred_at": "2024-01-01T12:00:00Z",
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
    "previous_state": "INITIATED",
    "partner_evidence": {
      "created_at": "2025-09-18T09:45:00Z",
      "additional_information": "Return was declined as per our return policy",
      "attachments": [
        {
          "payment_dispute_attachment_id": "krn:network:us1:live:payment:dispute:234567891:attachment:1",
          "description": "Return policy documentation",
          "url": "https://www.klarna.com/payment/disputes/krn:network:us1:live:payment:dispute:234567891/attachments/krn:network:us1:live:payment:dispute:234567891:attachment:1/download",
          "mime_type": "application/pdf"
        }
      ]
    },
    "updated_at": "2020-05-09T09:32:18Z",
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

### Payment dispute pre-arbitration webhook

```json
{
  "event_type": "payment.dispute.state-change.pre-arbitration",
  "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
  "occurred_at": "2020-04-15T08:31:01Z",
  "metadata": {
    "event_type": "payment.dispute.state-change.pre-arbitration",
    "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
    "event_version": "v1",
    "correlation_id": "3223496a-c253-4c4a-8849-68121c0e99c8",
    "occurred_at": "2020-04-15T08:31:01Z",
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
    "state": "PRE_ARBITRATION",
    "previous_state": "REPRESENTMENT",
    "arbitration_expires_at": "2025-06-28T09:45:00Z",
    "arbitration": {
      "preliminary_outcome": "LOST",
      "preliminary_outcome_detailed": "INSUFFICIENT_PROOF_OF_DELIVERY"
    },
    "updated_at": "2020-04-15T08:31:01Z",
    "purchase_reference": "purchase_reference6"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

### Payment dispute arbitration webhook

```json
{
  "event_type": "payment.dispute.state-change.arbitration",
  "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
  "occurred_at": "2020-04-15T08:31:01Z",
  "metadata": {
    "event_type": "payment.dispute.state-change.arbitration",
    "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
    "event_version": "v1",
    "correlation_id": "3223496a-c253-4c4a-8849-68121c0e99c8",
    "occurred_at": "2020-04-15T08:31:01Z",
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
    "state": "ARBITRATION",
    "previous_state": "PRE_ARBITRATION",
    "arbitration_request": {
      "requested_at": "2025-01-22T09:45:00Z",
      "additional_information": "We believe that you did not take the return information into account correctly, please re-examine the proof we initially provided.",
      "attachments": [
        {
          "payment_dispute_attachment_id": "krn:network:us1:live:payment:dispute:345678912:attachment:2",
          "url": "https://www.klarna.com/payment/disputes/krn:network:us1:live:payment:dispute:345678912/attachments/krn:network:us1:live:payment:dispute:345678912:attachment:2/download",
          "mime_type": "application/pdf"
        }
      ]
    },
    "updated_at": "2020-04-15T08:31:01Z",
    "purchase_reference": "purchase_reference6"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

### Payment dispute closed webhook

```json
{
  "event_type": "payment.dispute.state-change.closed",
  "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
  "occurred_at": "2020-05-22T00:00:00Z",
  "metadata": {
    "event_type": "payment.dispute.state-change.closed",
    "event_id": "d9f9b1a0-5b1a-4b0e-9b0a-9e9b1a0d5b1a",
    "event_version": "v1",
    "correlation_id": "3223496a-c253-4c4a-8849-68121c0e99c8",
    "occurred_at": "2020-05-22T00:00:00Z",
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
    "state": "CLOSED",
    "previous_state": "ARBITRATION",
    "dispute_outcome": "LOST",
    "dispute_outcome_detailed": "PARTNER_DID_NOT_FOLLOW_KLARNAS_SHIPPING_POLICY",
    "closed_at": "2020-05-22T00:00:00Z",
    "updated_at": "2020-05-22T00:00:00Z",
    "purchase_reference": "purchase_reference6"
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
from klarna.models.payment_dispute_state_change import (
    PaymentDisputeStateChange,
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

    # Step 3: Pattern match for payment.dispute.state-change only.
    if isinstance(event, PaymentDisputeStateChange):
        print("payment.dispute.state-change received")
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

