
# Payment Dispute Body

## Data Type

`PaymentDisputeBodyDisputeInitiated | PaymentDisputeBodyRepresentment | PaymentDisputeBodyPreArbitration | PaymentDisputeBodyArbitration | PaymentDisputeBodyClosed`

## Cases

| Type |
|  --- |
| [`PaymentDisputeBodyDisputeInitiated`](../../../doc/models/payment-dispute-body-dispute-initiated.md) |
| [`PaymentDisputeBodyRepresentment`](../../../doc/models/payment-dispute-body-representment.md) |
| [`PaymentDisputeBodyPreArbitration`](../../../doc/models/payment-dispute-body-pre-arbitration.md) |
| [`PaymentDisputeBodyArbitration`](../../../doc/models/payment-dispute-body-arbitration.md) |
| [`PaymentDisputeBodyClosed`](../../../doc/models/payment-dispute-body-closed.md) |

## PaymentDisputeBodyDisputeInitiated

### Initialization Code

#### Example

```python
value = PaymentDisputeBodyDisputeInitiated(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    dispute_reason=PaymentDisputeReason.PRODUCTS_OR_SERVICES_NOT_RECEIVED,
    state=State.PRE_ARBITRATION,
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    dispute_details=PaymentDisputeDetailsBase(
        dispute_amount=114,
        currency='USD',
        created_by=CreatedBy.CUSTOMER
    ),
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    state_context=StateContext(
        representment=PaymentDisputeRepresentment(
            state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
            expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
        )
    ),
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    product_id='krn:partner:global:account:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918',
    payment_account_reference='payment_account_ref',
    partner_account_id='krn:partner:global:account:live:LWT2XJSE'
)
```

## PaymentDisputeBodyRepresentment

### Initialization Code

#### Example

```python
value = PaymentDisputeBodyRepresentment(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    dispute_reason=PaymentDisputeReason.PRODUCTS_OR_SERVICES_NOT_RECEIVED,
    state=State.ARBITRATION,
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    dispute_details=PaymentDisputeDetailsBase(
        dispute_amount=114,
        currency='USD',
        created_by=CreatedBy.CUSTOMER
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
            ]
        )
    ),
    previous_state=PaymentDisputePreviousState.INITIATED,
    representment=PaymentDisputeRepresentment(
        state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
        expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
    ),
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    product_id='krn:partner:global:account:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918',
    payment_account_reference='payment_account_ref',
    partner_account_id='krn:partner:global:account:live:LWT2XJSE'
)
```

## PaymentDisputeBodyPreArbitration

### Initialization Code

#### Example

```python
value = PaymentDisputeBodyPreArbitration(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    dispute_reason=PaymentDisputeReason.PRODUCTS_OR_SERVICES_NOT_RECEIVED,
    state=State.REPRESENTMENT,
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    dispute_details=PaymentDisputeDetailsBase(
        dispute_amount=114,
        currency='USD',
        created_by=CreatedBy.CUSTOMER
    ),
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    state_context=StateContext2(
        arbitration_expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
    ),
    previous_state=PaymentDisputePreviousState.PRE_ARBITRATION,
    arbitration=PaymentDisputeArbitrationDetailsBase(
        preliminary_outcome=ArbitrationPreliminaryOutcome.WON,
        preliminary_outcome_detailed='PARTNER_DID_NOT_REPLY_TO_DISPUTE_REQUEST'
    ),
    representment=PaymentDisputeRepresentment(
        state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
        expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
    ),
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    product_id='krn:partner:global:account:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918',
    payment_account_reference='payment_account_ref',
    partner_account_id='krn:partner:global:account:live:LWT2XJSE'
)
```

## PaymentDisputeBodyArbitration

### Initialization Code

#### Example

```python
value = PaymentDisputeBodyArbitration(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    dispute_reason=PaymentDisputeReason.PRODUCTS_OR_SERVICES_NOT_RECEIVED,
    state=State.CLOSED,
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    dispute_details=PaymentDisputeDetailsBase(
        dispute_amount=114,
        currency='USD',
        created_by=CreatedBy.CUSTOMER
    ),
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    previous_state=PaymentDisputePreviousState.PRE_ARBITRATION,
    arbitration=PaymentDisputeArbitrationDetailsBase(
        preliminary_outcome=ArbitrationPreliminaryOutcome.WON,
        preliminary_outcome_detailed='PARTNER_DID_NOT_REPLY_TO_DISPUTE_REQUEST'
    ),
    representment=PaymentDisputeRepresentment(
        state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
        expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
    ),
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    product_id='krn:partner:global:account:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918',
    payment_account_reference='payment_account_ref',
    partner_account_id='krn:partner:global:account:live:LWT2XJSE'
)
```

## PaymentDisputeBodyClosed

### Initialization Code

#### Example

```python
value = PaymentDisputeBodyClosed(
    payment_dispute_id='krn:network:us1:live:payment:dispute:5169719611111',
    dispute_reason=PaymentDisputeReason.PRODUCTS_OR_SERVICES_NOT_RECEIVED,
    state=State.INITIATED,
    order_id='5c8ca572-5751-4f0a-ab2f-0a29aa845b37',
    payment_transaction_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0',
    payment_account_id='krn:partner:global:payment-account:test:3440b9b7-7ca2-44a3-8f62-776caacdaa0b',
    dispute_details=PaymentDisputeDetailsBase(
        dispute_amount=114,
        currency='USD',
        created_by=CreatedBy.CUSTOMER
    ),
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    updated_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    state_context=StateContext3(
        dispute_outcome=DisputeOutcome.WON,
        dispute_outcome_detailed='PARTNER_DID_NOT_REPLY_TO_DISPUTE_REQUEST',
        closed_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
    ),
    previous_state=PaymentDisputePreviousState.PRE_ARBITRATION,
    arbitration=PaymentDisputeArbitrationDetailsBase(
        preliminary_outcome=ArbitrationPreliminaryOutcome.WON,
        preliminary_outcome_detailed='PARTNER_DID_NOT_REPLY_TO_DISPUTE_REQUEST'
    ),
    representment=PaymentDisputeRepresentment(
        state=PaymentDisputeRepresentmentState.REPRESENTMENT_AUTOMATICALLY_REJECTED,
        expires_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
    ),
    payment_transaction_reference='partner-transaction-reference-4567',
    purchase_reference='merchant-order-9876',
    merchant_reference_2='501',
    capture_id='partner-capture-reference-1234',
    payment_capture_reference='partner-capture-reference-1234',
    capture_krn='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    payment_capture_id='krn:payment:eu1:transaction:6debe89e-98c0-486e-b7a5-08a4f6df94b0:capture:1',
    product_id='krn:partner:global:account:product:payment:ad71bc48-8a07-4919-a2c1-103dba3fc918',
    payment_account_reference='payment_account_ref',
    partner_account_id='krn:partner:global:account:live:LWT2XJSE'
)
```

