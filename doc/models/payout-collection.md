
# Payout Collection

## Structure

`PayoutCollection`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payouts` | [`List[Payout]`](../../doc/models/payout.md) | Required | - |
| `pagination` | [`Pagination`](../../doc/models/pagination.md) | Required | - |

## Example

```python
import dateutil.parser

from klarna.models.merchant_settlement_type import MerchantSettlementType
from klarna.models.pagination import Pagination
from klarna.models.payout import Payout
from klarna.models.payout_collection import PayoutCollection
from klarna.models.totals import Totals

payout_collection = PayoutCollection(
    payouts=[
        Payout(
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
    ],
    pagination=Pagination(
        count=10,
        total=42,
        next='http://example.com/collection?offset=21&size=10',
        prev='http://example.com/collection?offset=0&size=10',
        offset=10
    )
)
```

