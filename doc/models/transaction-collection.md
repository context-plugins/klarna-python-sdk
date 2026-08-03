
# Transaction Collection

## Structure

`TransactionCollection`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `transactions` | [`List[Transaction]`](../../doc/models/transaction.md) | Required | - |
| `pagination` | [`Pagination`](../../doc/models/pagination.md) | Required | - |

## Example

```python
import dateutil.parser

from klarna.models.detailed_type import DetailedType
from klarna.models.pagination import Pagination
from klarna.models.transaction import Transaction
from klarna.models.transaction_collection import TransactionCollection
from klarna.models.type_2 import Type2

transaction_collection = TransactionCollection(
    transactions=[
        Transaction(
            amount=2000,
            sale_date=dateutil.parser.parse('2016-12-14T07:52:26Z'),
            mtype=Type2.SALE,
            capture_date=dateutil.parser.parse('2016-12-14T07:52:26Z'),
            order_id='ce17b4cb-147f-48b7-b8e6-dde2fa397f04',
            currency_code='USD',
            purchase_country='PL',
            capture_id='33db6f16-9f43-43fa-a587-cc51411c98e4',
            merchant_reference_1='merchant_reference14',
            payment_reference='XISA93DJ',
            payout='https://{settlements_api}/payouts/XISA93DJ',
            refund_id='ef1baa1f-b42e-44be-b9e4-4b94510b53e5',
            short_order_id='shortrid',
            vat_rate=2000,
            vat_amount=1000,
            shipping_country='PL',
            initial_payment_method_type='direct_debit',
            initial_number_of_installments=3,
            initial_payment_method_monthly_downpayments=12,
            detailed_type=DetailedType.PURCHASE,
            tax_in_currency_of_registration_country=1000,
            currency_code_of_registration_country='EUR',
            klarna_comment='Loan Amortisation 2022-12-01',
            reversal_reference='krn:klarna:eu1:dispute:goods_not_received:263099944398666'
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

