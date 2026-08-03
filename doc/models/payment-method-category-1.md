
# Payment Method Category 1

Payment Method Category to show on the Payment Page. All available categories will be given to the customer if none is specified using payment_method_category or payment_method_categories. Ignored field for KCO Orders.

## Enumeration

`PaymentMethodCategory1`

## Fields

| Name |
|  --- |
| `DIRECT_DEBIT` |
| `DIRECT_BANK_TRANSFER` |
| `PAY_NOW` |
| `PAY_LATER` |
| `PAY_OVER_TIME` |
| `KLARNA` |

## Example

```python
from klarna.models.payment_method_category_1 import PaymentMethodCategory1

payment_method_category_1 = PaymentMethodCategory1.DIRECT_DEBIT
```

