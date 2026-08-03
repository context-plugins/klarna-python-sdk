
# Payment Dispute Flow Exceptions

## Data Type

`PaymentDisputeFlowDisputeWindowExtensionExceptions | PaymentDisputeFlowImmediateDisputeResolutionExceptions`

## Cases

| Type |
|  --- |
| [`PaymentDisputeFlowDisputeWindowExtensionExceptions`](../../../doc/models/payment-dispute-flow-dispute-window-extension-exceptions.md) |
| [`PaymentDisputeFlowImmediateDisputeResolutionExceptions`](../../../doc/models/payment-dispute-flow-immediate-dispute-resolution-exceptions.md) |

## PaymentDisputeFlowDisputeWindowExtensionExceptions

### Initialization Code

#### Example

```python
value = PaymentDisputeFlowDisputeWindowExtensionExceptions(
    exception_type='DISPUTE_WINDOW_EXTENSION',
    reason='DISPUTE_MIS_HANDLED',
    description='Dispute window extended due to errors or mishandling in the previous dispute process.'
)
```

## PaymentDisputeFlowImmediateDisputeResolutionExceptions

### Initialization Code

#### Example

```python
value = PaymentDisputeFlowImmediateDisputeResolutionExceptions(
    exception_type='IMMEDIATE_DISPUTE_RESOLUTION',
    reason='FRAUDULENT_PARTNER',
    description='Defense period skipped as the partner has been identified as engaging in fraudulent activities.'
)
```

