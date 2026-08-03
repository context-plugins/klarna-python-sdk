
# Payout

## Structure

`Payout`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `totals` | [`Totals`](../../doc/models/totals.md) | Required | - |
| `payment_reference` | `str` | Required | The reference id of the payout |
| `payout_date` | `datetime` | Required | ISO 8601 formatted date-time string |
| `currency_code` | `str` | Required | ISO 4217 Currency Code. Like USD, EUR, AUD or GBP. |
| `currency_code_of_registration_country` | `str` | Optional | ISO 4217 Currency Code of the country you are registered in. |
| `merchant_settlement_type` | [`MerchantSettlementType`](../../doc/models/merchant-settlement-type.md) | Required | Whether the amounts are net or gross |
| `merchant_id` | `str` | Required | The merchant id |
| `transactions` | `str` | Optional | Link to the transactions that are part of this payout |

## Example

```python
import dateutil.parser

from klarna.models.merchant_settlement_type import MerchantSettlementType
from klarna.models.payout import Payout
from klarna.models.totals import Totals

payout = Payout(
    totals=Totals(
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
    ),
    payment_reference='XISA93DJ',
    payout_date=dateutil.parser.parse('2016-12-14T07:52:26Z'),
    currency_code='USD',
    merchant_settlement_type=MerchantSettlementType.NET,
    merchant_id='merchant_id2',
    currency_code_of_registration_country='EUR',
    transactions='https://{settlements_api}/transactions?payment_reference=XISA93DJ'
)
```

