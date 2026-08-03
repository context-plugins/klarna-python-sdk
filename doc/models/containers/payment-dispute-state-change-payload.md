
# Payment Dispute State Change Payload

## Data Type

`PaymentDisputeStateChangeInitiated | PaymentDisputeStateChangeRepresentment | PaymentDisputeStateChangePreArbitration | PaymentDisputeStateChangeArbitration | PaymentDisputeStateChangeClosed`

## Cases

| Type |
|  --- |
| [`PaymentDisputeStateChangeInitiated`](../../../doc/models/payment-dispute-state-change-initiated.md) |
| [`PaymentDisputeStateChangeRepresentment`](../../../doc/models/payment-dispute-state-change-representment.md) |
| [`PaymentDisputeStateChangePreArbitration`](../../../doc/models/payment-dispute-state-change-pre-arbitration.md) |
| [`PaymentDisputeStateChangeArbitration`](../../../doc/models/payment-dispute-state-change-arbitration.md) |
| [`PaymentDisputeStateChangeClosed`](../../../doc/models/payment-dispute-state-change-closed.md) |

## PaymentDisputeStateChangeInitiated

### Initialization Code

#### Example

```python
value = PaymentDisputeStateChangeInitiated(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    state=PaymentDisputeState.CLOSED,
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    dispute_reason=PaymentDisputeReason.PRODUCTS_OR_SERVICES_NOT_RECEIVED,
    dispute_details=PaymentDisputeDetailsBase(
        dispute_amount=114,
        currency='USD',
        created_by=CreatedBy.CUSTOMER
    ),
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    payment_account_reference='payment_account_ref',
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1'
)
```

## PaymentDisputeStateChangeRepresentment

### Initialization Code

#### Example

```python
value = PaymentDisputeStateChangeRepresentment(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    state=PaymentDisputeState.ARBITRATION,
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    payment_account_reference='payment_account_ref',
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1'
)
```

## PaymentDisputeStateChangePreArbitration

### Initialization Code

#### Example

```python
value = PaymentDisputeStateChangePreArbitration(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    state=PaymentDisputeState.ARBITRATION,
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    arbitration_expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    arbitration=PaymentDisputeArbitrationDetailsBase(
        preliminary_outcome=ArbitrationPreliminaryOutcome.WON,
        preliminary_outcome_detailed='PARTNER_DID_NOT_REPLY_TO_DISPUTE_REQUEST'
    ),
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    payment_account_reference='payment_account_ref',
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1'
)
```

## PaymentDisputeStateChangeArbitration

### Initialization Code

#### Example

```python
value = PaymentDisputeStateChangeArbitration(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    state=PaymentDisputeState.PRE_ARBITRATION,
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    arbitration_request=PaymentDisputeArbitrationRequest(
        requested_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
        additional_information='additional_information2'
    ),
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    payment_account_reference='payment_account_ref',
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1'
)
```

## PaymentDisputeStateChangeClosed

### Initialization Code

#### Example

```python
value = PaymentDisputeStateChangeClosed(
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
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1'
)
```

