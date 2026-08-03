
# Type 2

The type of transaction.

## Enumeration

`Type2`

## Fields

| Name |
|  --- |
| `COMMISSION` |
| `SALE` |
| `REVERSAL` |
| `RETURN` |
| `TAX` |
| `FEE` |
| `FEE_REFUND` |
| `CORRECTION` |
| `REVERSAL_MERCHANT_PROTECTION` |
| `CHARGE` |
| `CREDIT` |
| `HOLDBACK` |
| `RELEASE` |

## Example

```python
from klarna.models.type_2 import Type2

type_2 = Type2.CREDIT
```

