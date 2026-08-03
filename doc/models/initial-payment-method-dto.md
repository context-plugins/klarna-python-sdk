
# Initial Payment Method Dto

Initial payment method for this order

*This model accepts additional fields of type Any.*

## Structure

`InitialPaymentMethodDto`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `description` | `str` | Optional | The description of the initial payment method. |
| `number_of_installments` | `int` | Optional | The number of installments (if applicable). |
| `mtype` | `str` | Optional | The type of the initial payment method. One of ACCOUNT, ALTERNATIVE_PAYMENT_METHOD, BANK_TRANSFER, CARD, DEFERRED_INTEREST, DIRECT_DEBIT, FIXED_AMOUNT_BY_CARD, FIXED_AMOUNT, FIXED_SUM_CREDIT, INVOICE_BUSINESS, INVOICE, MOBILEPAY, PAY_BY_CARD, PAY_IN_X, PAY_LATER_BY_CARD, PAY_LATER_IN_PARTS, SWISH, OTHER |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.initial_payment_method_dto import InitialPaymentMethodDto

initial_payment_method_dto = InitialPaymentMethodDto(
    description='Slice it (Fixed Payments)',
    number_of_installments=3,
    mtype='FIXED_AMOUNT',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

