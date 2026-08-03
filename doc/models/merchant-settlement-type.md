
# Merchant Settlement Type

Whether the amounts are net or gross

## Enumeration

`MerchantSettlementType`

## Fields

| Name |
|  --- |
| `GROSS` |
| `NET` |
| `GROSS_FEE` |

## Example

```python
from klarna.models.merchant_settlement_type import MerchantSettlementType

merchant_settlement_type = MerchantSettlementType.GROSS_FEE
```

