
# Payout Summary

## Structure

`PayoutSummary`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `summary_total_fee_correction_amount` | `int` | Required | The total amount of fee correction, in minor units |
| `summary_payout_date_start` | `datetime` | Required | ISO 8601 formatted date-time string |
| `summary_total_release_amount` | `int` | Required | The total amount of money released from holdback by Klarna, in minor units |
| `summary_settlement_currency` | `str` | Required | ISO 4217 Currency Code. Like USD, EUR, AUD or GBP. |
| `summary_payout_date_end` | `datetime` | Required | ISO 8601 formatted date-time string |
| `summary_total_tax_amount` | `int` | Required | The total amount of tax, in minor units |
| `summary_total_settlement_amount` | `int` | Required | The total amount of the settlement in question, in minor units |
| `summary_total_holdback_amount` | `int` | Required | The total amount of money withheld by Klarna, in minor units |
| `summary_total_reversal_amount` | `int` | Required | The total amount of reversals, in minor units |
| `summary_total_return_amount` | `int` | Required | The total amount of returns, in minor units |
| `summary_total_fee_amount` | `int` | Required | The total amount of fees, in minor units |
| `summary_total_commission_amount` | `int` | Required | The total amount of commissions, in minor units |
| `summary_total_commission_reversal_amount` | `int` | Optional | The total amount of commission reversals, in minor units |
| `summary_total_sale_amount` | `int` | Required | The total amount of sales, in minor units |
| `summary_total_repay_amount` | `int` | Required | The total amount of money that has been repaid by the merchant from the debt to Klarna, in minor units |

## Example

```python
import dateutil.parser

from klarna.models.payout_summary import PayoutSummary

payout_summary = PayoutSummary(
    summary_total_fee_correction_amount=550,
    summary_payout_date_start=dateutil.parser.parse('2016-12-14T07:52:26Z'),
    summary_total_release_amount=550,
    summary_settlement_currency='USD',
    summary_payout_date_end=dateutil.parser.parse('2016-12-14T07:52:26Z'),
    summary_total_tax_amount=550,
    summary_total_settlement_amount=550,
    summary_total_holdback_amount=550,
    summary_total_reversal_amount=550,
    summary_total_return_amount=550,
    summary_total_fee_amount=500,
    summary_total_commission_amount=550,
    summary_total_sale_amount=500,
    summary_total_repay_amount=550,
    summary_total_commission_reversal_amount=550
)
```

