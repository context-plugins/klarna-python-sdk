
# Totals

## Structure

`Totals`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `commission_amount` | `int` | Required | The total amount of commissions, in minor units |
| `commission_reversal_amount` | `int` | Optional | The total amount of commission reversals, in minor units |
| `repay_amount` | `int` | Required | The total amount of money that has been repaid by the merchant from the debt to Klarna, in minor units |
| `sale_amount` | `int` | Required | The total amount of sales, in minor units |
| `holdback_amount` | `int` | Required | The total amount of money withheld by Klarna, in minor units |
| `tax_amount` | `int` | Optional | The total amount of tax, in minor units |
| `settlement_amount` | `int` | Required | The total amount of the settlement in question, in minor units |
| `fee_correction_amount` | `int` | Optional | The total amount of fee correction, in minor units |
| `reversal_amount` | `int` | Required | The total amount of reversals, in minor units |
| `release_amount` | `int` | Required | The total amount of money released from holdback by Klarna, in minor units |
| `return_amount` | `int` | Required | The total amount of returns, in minor units |
| `fee_amount` | `int` | Required | The total amount of fees, in minor units |
| `charge_amount` | `int` | Required | The total amount of charges, in minor units. The additional field detailed_type contains the purpose of the charge |
| `credit_amount` | `int` | Required | The total amount of credits, in minor units. The additional field detailed_type contains the purpose of the credit |
| `fee_refund_amount` | `int` | Required | The total amount of refunded fees in a given settlement, in minor units. |
| `tax_refund_amount` | `int` | Required | The total amount of refunded tax in a given settlement, in minor units. |
| `deposit_amount` | `int` | Required | The increase of your debt balance with Klarna if your returns, fees, and other charges exceed your sales within this settlement period. This debt will be deducted from your next settlements and describes the amount that is increasing your debt balance, to be seen in the closing_debt_balance. In minor units. |
| `opening_debt_balance_amount` | `int` | Required | Your negative balance with Klarna from previous settlements, if your returns, fees, and other charges exceeded your sales. This amount equals the closing_debt_balance of your last settlement unless Klarna has invoiced you separately for the amount. In minor units. |
| `closing_debt_balance_amount` | `int` | Required | Your debt balance after the settlement. This amount will be the opening debt balance of your next settlement and helps you understand which amounts will be deducted from your next settlements. In minor units. |

## Example

```python
from klarna.models.totals import Totals

totals = Totals(
    commission_amount=550,
    repay_amount=550,
    sale_amount=500,
    holdback_amount=550,
    settlement_amount=550,
    reversal_amount=550,
    release_amount=550,
    return_amount=550,
    fee_amount=500,
    charge_amount=500,
    credit_amount=500,
    fee_refund_amount=500,
    tax_refund_amount=500,
    deposit_amount=500,
    opening_debt_balance_amount=500,
    closing_debt_balance_amount=500,
    commission_reversal_amount=550,
    tax_amount=550,
    fee_correction_amount=550
)
```

