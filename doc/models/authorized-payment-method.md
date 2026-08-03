
# Authorized Payment Method

*This model accepts additional fields of type Any.*

## Structure

`AuthorizedPaymentMethod`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `number_of_days` | `int` | Optional | - |
| `number_of_installments` | `int` | Optional | - |
| `mtype` | [`Type1`](../../doc/models/type-1.md) | Required | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.authorized_payment_method import AuthorizedPaymentMethod
from klarna.models.type_1 import Type1

authorized_payment_method = AuthorizedPaymentMethod(
    mtype=Type1.FIXED_SUM_CREDIT,
    number_of_days=242,
    number_of_installments=122,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

