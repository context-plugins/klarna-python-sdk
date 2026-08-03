# Payment Dispute API

```python
payment_dispute_api = client.payment_dispute_api
```

## Class Name

`PaymentDisputeApi`

## Methods

* [Enroll Merchant](../../doc/controllers/payment-dispute-api.md#enroll-merchant)
* [Enroll Partner](../../doc/controllers/payment-dispute-api.md#enroll-partner)
* [List Disputes](../../doc/controllers/payment-dispute-api.md#list-disputes)
* [Get Dispute Details](../../doc/controllers/payment-dispute-api.md#get-dispute-details)
* [Accept Loss](../../doc/controllers/payment-dispute-api.md#accept-loss)
* [Respond to Dispute Request](../../doc/controllers/payment-dispute-api.md#respond-to-dispute-request)
* [Appeal Dispute](../../doc/controllers/payment-dispute-api.md#appeal-dispute)
* [Upload Attachment](../../doc/controllers/payment-dispute-api.md#upload-attachment)
* [Get Dispute Attachment](../../doc/controllers/payment-dispute-api.md#get-dispute-attachment)


# Enroll Merchant

Activates dispute handling for a single merchant account. Partners are not allowed and cannot enroll individual merchants.

```python
def enroll_merchant(self,
                   merchant_id)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `merchant_id` | `str` | Template, Required | Merchant ID<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Response Type

**204**: Merchant successfully onboarded or was onboarded already

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
merchant_id = 'merchant_id0'

result = payment_dispute_api.enroll_merchant(merchant_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 403 | Forbidden, insufficient privileges to perform the requested operation on the resource. | [`ResourceErrorOperationForbiddenErrorException`](../../doc/models/resource-error-operation-forbidden-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# Enroll Partner

Activates dispute handling for a partner account. Merchants are not allowed and cannot enroll a partner.

```python
def enroll_partner(self,
                  partner_id,
                  body)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `partner_id` | `str` | Template, Required | Partner ID<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `body` | [`SelfOnboardPartnerRequestPayload`](../../doc/models/self-onboard-partner-request-payload.md) | Body, Required | Request body for self onboarding |

## Response Type

**204**: Partner successfully onboarded or was onboarded already

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
partner_id = 'krn:partner:global:account:live:LWT2XJSE'

body = SelfOnboardPartnerRequestPayload(
    client_id='abcdefghijklmnop1234567890'
)

result = payment_dispute_api.enroll_partner(
    partner_id,
    body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 403 | Forbidden, insufficient privileges to perform the requested operation on the resource. | [`ResourceErrorOperationForbiddenErrorException`](../../doc/models/resource-error-operation-forbidden-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# List Disputes

Retrieve a list of disputes. Filter by payment transaction ids, state, reason, purchase references, dispute creation date (created_at), or dispute closing date (closed_at).

```python
def list_disputes(self,
                 order_ids=None,
                 payment_transaction_ids=None,
                 state=None,
                 reason=None,
                 sort_by=None,
                 purchase_references=None,
                 created_at_start=None,
                 created_at_end=None,
                 closed_at_start=None,
                 closed_at_end=None,
                 updated_at_start=None,
                 updated_at_end=None,
                 size=None,
                 starting_after=None,
                 klarna_integration_metadata=None,
                 partner_correlation_id=None)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_ids` | `List[str]` | Query, Optional | Order IDs to filter by<br><br>**Constraints**: *Maximum Items*: `100`, *Minimum Length*: `1`, *Maximum Length*: `255` |
| `payment_transaction_ids` | `List[str]` | Query, Optional | Payment Transaction IDs to filter by<br><br>**Constraints**: *Maximum Items*: `100`, *Minimum Length*: `1`, *Maximum Length*: `255` |
| `state` | [`List[PaymentDisputeState]`](../../doc/models/payment-dispute-state.md) | Query, Optional | States of disputes to filter by<br><br>**Constraints**: *Maximum Items*: `100` |
| `reason` | [`List[PaymentDisputeReason]`](../../doc/models/payment-dispute-reason.md) | Query, Optional | Dispute reasons to filter by<br><br>**Constraints**: *Maximum Items*: `10` |
| `sort_by` | [`List[SortBy]`](../../doc/models/sort-by.md) | Query, Optional | Specifies in which order to sort the results. Then results are ordered in ascending order if not prefixed by a - which orders by descending order.<br><br>**Constraints**: *Maximum Items*: `10` |
| `purchase_references` | `List[str]` | Query, Optional | Purchase references to filter by<br><br>**Constraints**: *Maximum Items*: `10`, *Minimum Length*: `1`, *Maximum Length*: `255` |
| `created_at_start` | `datetime` | Query, Optional | Used to filter by dispute creation dates. Only disputes created after (including) the supplied value will be returned. |
| `created_at_end` | `datetime` | Query, Optional | Used to filter by dispute creation dates. Only disputes created before (excluding) the supplied value will be returned. |
| `closed_at_start` | `datetime` | Query, Optional | Used to filter by dispute closing dates. Only disputes closed after (including) the supplied value will be returned. |
| `closed_at_end` | `datetime` | Query, Optional | Used to filter by dispute closing dates. Only disputes closed before (excluding) the supplied value will be returned. |
| `updated_at_start` | `datetime` | Query, Optional | Used to filter by dispute last update dates. Only disputes updated after (including) the supplied value will be returned. |
| `updated_at_end` | `datetime` | Query, Optional | Used to filter by dispute last update dates. Only disputes updated before (excluding) the supplied value will be returned. |
| `size` | `int` | Query, Optional | Limits the number of items to be returned. If omitted, the default page size will be used. |
| `starting_after` | `str` | Query, Optional | A cursor used in pagination, referring to a specific item. The `last_item` returned from a previous call can be used here. The next page will list items after this item. Cannot be used together with `ending_before`. If both `starting_after` and `ending_before` are omitted, the first page will be returned.<br><br>**Constraints**: *Minimum Length*: `1` |
| `klarna_integration_metadata` | [`ApplicationJson`](../../doc/models/application-json.md) | Header, Optional | Metadata about the integrator and originators of the request, a valid JSON object string literal, to improve troubleshooting. [Read more here](https://docs.klarna.com/api/kn/integration-resilience/#tagging)<br><br>The header value as appearing on the wire should be a JSON object string literal without newlines as produced by `JSON.stringify()`.<br><br>Example: `Klarna-Integration-Metadata: {"integrator":{"name":"AcquiringPartner","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v1.0"},"originators":[{"name":"ecommerceCompany","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v2.0"}]}` |
| `partner_correlation_id` | `str` | Header, Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Response Type

**200**: A paginated list of authorized disputes

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`DisputesList`](../../doc/models/disputes-list.md).

## Example Usage

```python
created_at_start = dateutil.parser.parse('01/01/2024 12:00:00')

created_at_end = dateutil.parser.parse('01/01/2024 12:00:00')

closed_at_start = dateutil.parser.parse('01/01/2024 12:00:00')

closed_at_end = dateutil.parser.parse('01/01/2024 12:00:00')

updated_at_start = dateutil.parser.parse('01/01/2024 12:00:00')

updated_at_end = dateutil.parser.parse('01/01/2024 12:00:00')

size = 20

starting_after = 'Zpq6F3mDYtwK8'

klarna_integration_metadata = ApplicationJson(
    integrator=Integrator(
        name='PSP',
        session_reference='session_reference6',
        module_name='psp-new-payment'
    )
)

result = payment_dispute_api.list_disputes(
    created_at_start=created_at_start,
    created_at_end=created_at_end,
    closed_at_start=closed_at_start,
    closed_at_end=closed_at_end,
    updated_at_start=updated_at_start,
    updated_at_end=updated_at_end,
    size=size,
    starting_after=starting_after,
    klarna_integration_metadata=klarna_integration_metadata
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request, there was an error in the input of the request.<br>The request can not be retried without modifications. | `ApiException` |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 403 | Forbidden, insufficient privileges to perform the requested operation on the resource. | [`ResourceErrorOperationForbiddenErrorException`](../../doc/models/resource-error-operation-forbidden-error-exception.md) |
| 404 | Not Found, the requested resource was not found. | [`ResourceErrorNotFoundErrorErrorException`](../../doc/models/resource-error-not-found-error-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# Get Dispute Details

Retrieve the dispute in its current state.

```python
def get_dispute_details(self,
                       payment_dispute_id,
                       klarna_integration_metadata=None,
                       partner_correlation_id=None)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Template, Required | ID of dispute to fetch<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100` |
| `klarna_integration_metadata` | [`ApplicationJson`](../../doc/models/application-json.md) | Header, Optional | Metadata about the integrator and originators of the request, a valid JSON object string literal, to improve troubleshooting. [Read more here](https://docs.klarna.com/api/kn/integration-resilience/#tagging)<br><br>The header value as appearing on the wire should be a JSON object string literal without newlines as produced by `JSON.stringify()`.<br><br>Example: `Klarna-Integration-Metadata: {"integrator":{"name":"AcquiringPartner","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v1.0"},"originators":[{"name":"ecommerceCompany","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v2.0"}]}` |
| `partner_correlation_id` | `str` | Header, Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Response Type

**200**: Complete dispute with all requests and responses

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type `PaymentDisputeBodyDisputeInitiated | PaymentDisputeBodyRepresentment | PaymentDisputeBodyPreArbitration | PaymentDisputeBodyArbitration | PaymentDisputeBodyClosed`.

## Related Callbacks

| Name | Description |
|  --- | --- |
| [Payment Dispute State-Change](../../doc/events/callbacks/callbacks/payment-dispute-state-change.md) | Webhook delivered when the dispute state changes |
| [Payment Dispute Updated](../../doc/events/callbacks/callbacks/payment-dispute-updated.md) | Webhook delivered when the dispute is updated without state change |

## Example Usage

```python
payment_dispute_id = 'payment_dispute_id0'

klarna_integration_metadata = ApplicationJson(
    integrator=Integrator(
        name='PSP',
        session_reference='session_reference6',
        module_name='psp-new-payment'
    )
)

result = payment_dispute_api.get_dispute_details(
    payment_dispute_id,
    klarna_integration_metadata=klarna_integration_metadata
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response

```
{
  "payment_dispute_id": "krn:network:us1:live:payment:dispute:5169719611111",
  "dispute_reason": "PRODUCTS_OR_SERVICES_NOT_RECEIVED",
  "state": "CLOSED",
  "previous_state": "ARBITRATION",
  "payment_transaction_id": "krn:payment:eu1:authorization:6debe89e-98c0-486e-b7a5-08a4f6df94b0",
  "order_id": "5c8ca572-5751-4f0a-ab2f-0a29aa845b37",
  "payment_transaction_reference": "f420e0e1-971b-417a-8ece-2626387eff36",
  "payment_capture_reference": "partner-capture-reference-1234",
  "capture_id": "0b812553-d263-4758-9057-a10961a71716",
  "purchase_reference": "f420e0e1-971b-417a-8ece-2626387eff36",
  "merchant_reference2": "501",
  "product_id": "krn:partner:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918",
  "payment_account_id": "krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b",
  "payment_account_reference": "REF995847",
  "state_context": {
    "dispute_outcome": "LOST",
    "dispute_outcome_detailed": "INSUFFICIENT_PROOF_OF_DELIVERY",
    "closed_at": "2025-11-25T11:20:00Z"
  },
  "arbitration": {
    "arbitration_request": {
      "requested_at": "2025-01-22T09:45:00Z",
      "additional_information": "We strongly disagree with the preliminary outcome. Our delivery records conclusively prove the customer received the goods. The tracking data and signature are authentic and verifiable. Please reconsider."
    },
    "preliminary_outcome": "LOST",
    "preliminary_outcome_detailed": "INSUFFICIENT_PROOF_OF_DELIVERY"
  },
  "representment": {
    "state": "EVIDENCE_RECEIVED",
    "previous_state": "EVIDENCE_REQUESTED",
    "expires_at": "2025-01-22T09:45:00Z",
    "request": {
      "requested_at": "2025-01-01T09:45:00Z",
      "additional_information": "Dear Partner Team,\nTo help us resolve this dispute, please provide proof of delivery, including tracking information, delivery confirmation, and any signature or documentation showing the customer received the order."
    },
    "partner_evidence": {
      "created_at": "2025-09-18T09:45:00Z",
      "additional_information": "The shipment was delivered on March 22, 2024, at 2:45 PM to the address on file. Our carrier records show the package was signed for by the customer. Full tracking history and delivery confirmation are attached.",
      "attachments": [
        {
          "payment_dispute_attachment_id": "krn:network:us1:live:payment:dispute:567891234:attachment:1",
          "description": "Shipment tracking and delivery confirmation",
          "url": "https://www.klarna.com/payment/disputes/krn:network:us1:live:payment:dispute:567891234/attachments/krn:network:us1:live:payment:dispute:567891234:attachment:1/download",
          "mime_type": "application/pdf"
        }
      ]
    }
  },
  "dispute_details": {
    "dispute_amount": 39900,
    "currency": "EUR",
    "created_by": "CUSTOMER"
  },
  "customer_evidences": [
    {
      "payment_dispute_customer_evidence_id": "krn:network:us1:live:payment:dispute:567891234:customer-evidence:1",
      "attachment": {
        "url": "https://www.klarna.com/payment/disputes/krn:network:us1:live:payment:dispute:567891234/attachments/krn:network:us1:live:payment:dispute:567891234:customer-evidence:1/download",
        "mime_type": "application/pdf"
      }
    }
  ],
  "created_at": "2025-09-11T08:31:00Z",
  "updated_at": "2025-09-15T08:31:00Z"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request, there was an error in the input of the request.<br>The request can not be retried without modifications. | `ApiException` |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 404 | Not Found, the requested resource was not found. | [`ResourceErrorNotFoundErrorErrorException`](../../doc/models/resource-error-not-found-error-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# Accept Loss

Use this endpoint to accept the loss of the dispute when the dispute is in `INITIATED` or `PRE_ARBITRATION` state. The dispute will transition to state `CLOSED` with outcome `LOST`.

```python
def accept_loss(self,
               payment_dispute_id,
               klarna_integration_metadata=None,
               partner_correlation_id=None)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Template, Required | ID of dispute to accept<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `klarna_integration_metadata` | [`ApplicationJson`](../../doc/models/application-json.md) | Header, Optional | Metadata about the integrator and originators of the request, a valid JSON object string literal, to improve troubleshooting. [Read more here](https://docs.klarna.com/api/kn/integration-resilience/#tagging)<br><br>The header value as appearing on the wire should be a JSON object string literal without newlines as produced by `JSON.stringify()`.<br><br>Example: `Klarna-Integration-Metadata: {"integrator":{"name":"AcquiringPartner","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v1.0"},"originators":[{"name":"ecommerceCompany","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v2.0"}]}` |
| `partner_correlation_id` | `str` | Header, Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Response Type

**202**: Acceptance was submitted successfully

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`V4PaymentDisputesAcceptLossResponse`](../../doc/models/v4-payment-disputes-accept-loss-response.md).

## Example Usage

```python
payment_dispute_id = 'payment_dispute_id0'

klarna_integration_metadata = ApplicationJson(
    integrator=Integrator(
        name='PSP',
        session_reference='session_reference6',
        module_name='psp-new-payment'
    )
)

result = payment_dispute_api.accept_loss(
    payment_dispute_id,
    klarna_integration_metadata=klarna_integration_metadata
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "state": "CLOSED"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request, there was an error in the input of the request.<br>The request can not be retried without modifications. | `ApiException` |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 404 | Not Found, the requested resource was not found. | [`ResourceErrorNotFoundErrorErrorException`](../../doc/models/resource-error-not-found-error-error-exception.md) |
| 409 | The dispute is not in a state where it can be accepted, or the acceptance type is not valid for the current state. Read the error details for further information. | [`ResourceErrorConflictErrorErrorException`](../../doc/models/resource-error-conflict-error-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# Respond to Dispute Request

Use this endpoint to submit partner information by providing a document containing all relevant information when the dispute is in `INITIATED` state.
Optionally, include `partner_proposed_refund_amount` to propose a partial refund while providing evidence for why the remaining amount should not be refunded.
The dispute will transition to state `REPRESENTMENT` for Klarna review after submission.

```python
def respond_to_dispute_request(self,
                              payment_dispute_id,
                              body,
                              klarna_integration_metadata=None,
                              partner_correlation_id=None)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Template, Required | ID of dispute for which the request to add response to belongs<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `body` | [`PaymentDisputeRespondToEvidenceRequestPayload`](../../doc/models/payment-dispute-respond-to-evidence-request-payload.md) | Body, Required | Payload to respond to a dispute request for representment |
| `klarna_integration_metadata` | [`ApplicationJson`](../../doc/models/application-json.md) | Header, Optional | Metadata about the integrator and originators of the request, a valid JSON object string literal, to improve troubleshooting. [Read more here](https://docs.klarna.com/api/kn/integration-resilience/#tagging)<br><br>The header value as appearing on the wire should be a JSON object string literal without newlines as produced by `JSON.stringify()`.<br><br>Example: `Klarna-Integration-Metadata: {"integrator":{"name":"AcquiringPartner","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v1.0"},"originators":[{"name":"ecommerceCompany","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v2.0"}]}` |
| `partner_correlation_id` | `str` | Header, Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Response Type

**201**: Dispute's representment request response was submitted successfully

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PaymentDisputeEvidenceRequestResponse`](../../doc/models/payment-dispute-evidence-request-response.md).

## Example Usage

```python
payment_dispute_id = 'payment_dispute_id0'

body = PaymentDisputeRespondToEvidenceRequestPayload(
    attachments=[
        PaymentDisputeAttachment(
            payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:123456789:attachment:1',
            description='Proof of delivery documentation'
        )
    ],
    additional_information='The order was successfully delivered on March 15, 2024. Please see attached proof of delivery documentation with customer signature.'
)

result = payment_dispute_api.respond_to_dispute_request(
    payment_dispute_id,
    body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "state": "REPRESENTMENT",
  "created_at": "2020-05-09T09:32:18Z",
  "additional_information": "The order was successfully delivered on March 15, 2024. Please see attached proof of delivery documentation with customer signature.",
  "attachments": [
    {
      "payment_dispute_attachment_id": "krn:network:us1:live:payment:dispute:266092:attachment:1",
      "description": "Proof of delivery"
    }
  ]
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request. Invalid parameters provided. Common errors include partner_proposed_refund_amount being equal to or greater than the full disputed amount. | [`InputErrorValidationErrorErrorException`](../../doc/models/input-error-validation-error-error-exception.md) |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 403 | Forbidden, insufficient privileges to perform the requested operation on the resource. | [`ResourceErrorOperationForbiddenErrorException`](../../doc/models/resource-error-operation-forbidden-error-exception.md) |
| 404 | Not Found, the requested resource was not found. | [`ResourceErrorNotFoundErrorErrorException`](../../doc/models/resource-error-not-found-error-error-exception.md) |
| 409 | The dispute is not in a state where representment can be submitted. | [`ResourceErrorConflictErrorErrorException`](../../doc/models/resource-error-conflict-error-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# Appeal Dispute

Use this endpoint to submit an appeal for a preliminary dispute decision by providing a summary of the reasons why the decision is considered incorrect when the dispute is in `PRE_ARBITRATION` state. The dispute will transition to state `ARBITRATION` while Klarna will review the appeal information.

```python
def appeal_dispute(self,
                  payment_dispute_id,
                  body,
                  klarna_integration_metadata=None,
                  partner_correlation_id=None)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Template, Required | ID of dispute to appeal<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `body` | [`V4PaymentDisputesAppealRequest`](../../doc/models/v4-payment-disputes-appeal-request.md) | Body, Required | - |
| `klarna_integration_metadata` | [`ApplicationJson`](../../doc/models/application-json.md) | Header, Optional | Metadata about the integrator and originators of the request, a valid JSON object string literal, to improve troubleshooting. [Read more here](https://docs.klarna.com/api/kn/integration-resilience/#tagging)<br><br>The header value as appearing on the wire should be a JSON object string literal without newlines as produced by `JSON.stringify()`.<br><br>Example: `Klarna-Integration-Metadata: {"integrator":{"name":"AcquiringPartner","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v1.0"},"originators":[{"name":"ecommerceCompany","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v2.0"}]}` |
| `partner_correlation_id` | `str` | Header, Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Response Type

**201**: Appeal was submitted successfully

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PaymentDisputeAppealResponse`](../../doc/models/payment-dispute-appeal-response.md).

## Example Usage

```python
payment_dispute_id = 'payment_dispute_id0'

body = V4PaymentDisputesAppealRequest(
    additional_information='We believe the preliminary decision is incorrect because we have proof of delivery with customer signature.',
    attachments=[
        PaymentDisputeAttachment(
            payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:266092:attachment:1',
            description='Signed proof of delivery'
        ),
        PaymentDisputeAttachment(
            payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:266092:attachment:2',
            description='Shipment tracking confirmation'
        )
    ]
)

result = payment_dispute_api.appeal_dispute(
    payment_dispute_id,
    body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Example Response *(as JSON)*

```json
{
  "state": "ARBITRATION",
  "created_at": "2020-05-09T09:32:18Z",
  "additional_information": "We believe the preliminary decision is incorrect because we have proof of delivery with customer signature. The tracking shows the package was delivered and signed for by the customer on the expected date."
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request, there was an error in the input of the request.<br>The request can not be retried without modifications. | `ApiException` |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 403 | Forbidden, insufficient privileges to perform the requested operation on the resource. | [`ResourceErrorOperationForbiddenErrorException`](../../doc/models/resource-error-operation-forbidden-error-exception.md) |
| 404 | Not Found, the requested resource was not found. | [`ResourceErrorNotFoundErrorErrorException`](../../doc/models/resource-error-not-found-error-error-exception.md) |
| 409 | The dispute is not in a state where an appeal can be submitted. Read the error details for further information. | [`ResourceErrorConflictErrorErrorException`](../../doc/models/resource-error-conflict-error-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# Upload Attachment

Upload a partner evidence attachment using multipart/form-data. The response returns a `payment_dispute_attachment_id` that you can reference when using the respond endpoint. Supported file types: PDF, JPEG, PNG, and DOCX. Maximum file size is 7MB.

```python
def upload_attachment(self,
                     payment_dispute_id,
                     file,
                     klarna_integration_metadata=None,
                     partner_correlation_id=None,
                     filename=None)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Template, Required | ID of dispute for which the request to add response to belongs<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `file` | `typing.BinaryIO` | Form, Required | The file to upload as binary data. This field is required and must contain the actual file content. Supported file types are: PDF (.pdf), JPEG (.jpg, .jpeg), PNG (.png), and Word documents (.docx). Maximum file size is 7MB. |
| `klarna_integration_metadata` | [`ApplicationJson`](../../doc/models/application-json.md) | Header, Optional | Metadata about the integrator and originators of the request, a valid JSON object string literal, to improve troubleshooting. [Read more here](https://docs.klarna.com/api/kn/integration-resilience/#tagging)<br><br>The header value as appearing on the wire should be a JSON object string literal without newlines as produced by `JSON.stringify()`.<br><br>Example: `Klarna-Integration-Metadata: {"integrator":{"name":"AcquiringPartner","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v1.0"},"originators":[{"name":"ecommerceCompany","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v2.0"}]}` |
| `partner_correlation_id` | `str` | Header, Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `filename` | `str` | Form, Optional | Optional filename for the uploaded attachment. If not provided, the original filename from the uploaded file will be used. If provided, the file extension must match the extension of the uploaded file. Maximum length is 1000 characters (excluding the file extension).<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `1000` |

## Response Type

**201**: Attachment uploaded successfully

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PaymentDisputeNewAttachmentResponse`](../../doc/models/payment-dispute-new-attachment-response.md).

## Example Usage

```python
payment_dispute_id = 'payment_dispute_id0'

file = FileWrapper(Path('dummy_file').open('rb'), 'optional-content-type')

klarna_integration_metadata = ApplicationJson(
    integrator=Integrator(
        name='PSP',
        session_reference='session_reference6',
        module_name='psp-new-payment'
    )
)

filename = 'receipt.pdf'

result = payment_dispute_api.upload_attachment(
    payment_dispute_id,
    file,
    klarna_integration_metadata=klarna_integration_metadata,
    filename=filename
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request, there was an error in the input of the request.<br>The request can not be retried without modifications. | `ApiException` |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 403 | Forbidden, insufficient privileges to perform the requested operation on the resource. | [`ResourceErrorOperationForbiddenErrorException`](../../doc/models/resource-error-operation-forbidden-error-exception.md) |
| 404 | Not Found, the requested resource was not found. | [`ResourceErrorNotFoundErrorErrorException`](../../doc/models/resource-error-not-found-error-error-exception.md) |
| 409 | The dispute is not in a state where attachments can be uploaded. This can occur if the partner has already submitted evidence for this dispute. | [`ResourceErrorConflictErrorErrorException`](../../doc/models/resource-error-conflict-error-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |


# Get Dispute Attachment

Download an attachment file associated with the dispute. This can be either a partner-submitted evidence attachment or a customer-provided evidence attachment. If the attachment_id does not belong to the specified dispute_id, a 404 error will be returned.

```python
def get_dispute_attachment(self,
                          payment_dispute_id,
                          payment_dispute_attachment_id,
                          klarna_integration_metadata=None,
                          partner_correlation_id=None)
```

## Authentication

This endpoint requires [klarna_api_key](../../doc/auth/custom-header-signature.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_dispute_id` | `str` | Template, Required | ID of dispute to fetch<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `100` |
| `payment_dispute_attachment_id` | `str` | Template, Required | ID of attachment to fetch<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `klarna_integration_metadata` | [`ApplicationJson`](../../doc/models/application-json.md) | Header, Optional | Metadata about the integrator and originators of the request, a valid JSON object string literal, to improve troubleshooting. [Read more here](https://docs.klarna.com/api/kn/integration-resilience/#tagging)<br><br>The header value as appearing on the wire should be a JSON object string literal without newlines as produced by `JSON.stringify()`.<br><br>Example: `Klarna-Integration-Metadata: {"integrator":{"name":"AcquiringPartner","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v1.0"},"originators":[{"name":"ecommerceCompany","session_reference":"ecomm_5555-474","module_name":"subIntegrationPath","module_version":"v2.0"}]}` |
| `partner_correlation_id` | `str` | Header, Optional | **Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |

## Response Type

**200**: Attachment was downloaded successfully. The response contains the attachment file in its original format as binary data, with appropriate Content-Type and Content-Disposition headers.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type `Any`.

## Example Usage

```python
payment_dispute_id = 'payment_dispute_id0'

payment_dispute_attachment_id = 'payment_dispute_attachment_id2'

klarna_integration_metadata = ApplicationJson(
    integrator=Integrator(
        name='PSP',
        session_reference='session_reference6',
        module_name='psp-new-payment'
    )
)

result = payment_dispute_api.get_dispute_attachment(
    payment_dispute_id,
    payment_dispute_attachment_id,
    klarna_integration_metadata=klarna_integration_metadata
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request, there was an error in the input of the request.<br>The request can not be retried without modifications. | `ApiException` |
| 401 | Unauthorized, the request was not authorized. | [`AccessErrorUnauthorizedErrorException`](../../doc/models/access-error-unauthorized-error-exception.md) |
| 403 | Forbidden, insufficient privileges to perform the requested operation on the resource. | [`ResourceErrorOperationForbiddenErrorException`](../../doc/models/resource-error-operation-forbidden-error-exception.md) |
| 404 | Not Found, the requested resource was not found. | [`ResourceErrorNotFoundErrorErrorException`](../../doc/models/resource-error-not-found-error-error-exception.md) |
| 429 | Too Many Requests, the request was rate limited. | [`AccessErrorRateLimitedErrorException`](../../doc/models/access-error-rate-limited-error-exception.md) |
| 500 | Internal Server Error, there was an unexpected error in the API. | [`TechnicalErrorInternalErrorErrorException`](../../doc/models/technical-error-internal-error-error-exception.md) |

