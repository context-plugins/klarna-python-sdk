
# Transaction

## Structure

`Transaction`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `amount` | `int` | Required | Total amount of the specific transaction, in minor units |
| `capture_id` | `str` | Optional | Each capture on an order is assigned a unique identifier, referred to as the capture_id, which is provided exclusively for sale and fee transactions. In instances of partial shipments, an order may undergo multiple captures, each of which is reflected as a separate transaction with its own unique capture_id. It's important to note that for certain transaction types such as RETURNS and REVERSALS, where captures do not exist, the API will return empty strings for the capture_ID field. |
| `merchant_reference_1` | `str` | Optional | Merchant assigned reference, typically a reference to an order management system id |
| `sale_date` | `datetime` | Required | ISO 8601 formatted date-time string |
| `mtype` | [`Type2`](../../doc/models/type-2.md) | Required | The type of transaction. |
| `capture_date` | `datetime` | Required | ISO 8601 formatted date-time string |
| `payment_reference` | `str` | Optional | Reference to the specific payout the transaction is part of, if available. |
| `order_id` | `uuid\|str` | Required | The Klarna assigned order id reference |
| `payout` | `str` | Optional | Link to the payout that this transaction is part of |
| `refund_id` | `str` | Optional | The Klarna assigned id reference of a specific refund |
| `short_order_id` | `str` | Optional | The Klarna assigned short order id reference |
| `merchant_reference_2` | `str` | Optional | Merchant assigned reference, typically a reference to an order management system id |
| `currency_code` | `str` | Required | ISO 4217 Currency Code. Like USD, EUR, AUD or GBP. |
| `purchase_country` | `str` | Required | ISO Alpha-2 Country Code |
| `vat_rate` | `int` | Optional | VAT (Value added tax) rate on Klarna fees |
| `vat_amount` | `int` | Optional | VAT (Value added tax) amount on Klarna fees, in minor units |
| `shipping_country` | `str` | Optional | ISO Alpha-2 Country Code |
| `initial_payment_method_type` | `str` | Optional | Payment method the consumer chose during checkout |
| `initial_number_of_installments` | `int` | Optional | Number of installments the consumer chose during checkout in case of installment payments |
| `initial_payment_method_monthly_downpayments` | `int` | Optional | Number of monthly downpayments that were chosen during the checkout in case of installment payments. |
| `merchant_capture_reference` | `str` | Optional | Your internal reference to the capture, that has been submitted during capturing an order via API |
| `merchant_refund_reference` | `str` | Optional | Your internal reference to the refund, that has been submitted during refunding an order via API |
| `detailed_type` | [`DetailedType`](../../doc/models/detailed-type.md) | Optional | Detailed description of the transaction type |
| `tax_in_currency_of_registration_country` | `int` | Optional | The tax amount on the respective fee, converted into the currency of your registration country. In case you are a German merchant selling in another currency then EUR or a Swedish merchant selling in another currency then SEK, we convert the VAT amount on the Klarna fees into the currency of the country you are registered in, based on the exchange rate of the capture date. |
| `currency_code_of_registration_country` | `str` | Optional | ISO 4217 Currency Code of the country you are registered in. |
| `klarna_comment` | `str` | Optional | Any additional information necessary to provide more context about the transaction. |
| `reversal_reference` | `str` | Optional | Unique internal identifier, known as DisputeKRN, assigned to each dispute by Klarna. This identifier includes a dispute category and a numeric code, enabling efficient tracking and management of the dispute's status. |

## Example

```python
import dateutil.parser

from klarna.models.detailed_type import DetailedType
from klarna.models.transaction import Transaction
from klarna.models.type_2 import Type2

transaction = Transaction(
    amount=2000,
    sale_date=dateutil.parser.parse('2016-12-14T07:52:26Z'),
    mtype=Type2.SALE,
    capture_date=dateutil.parser.parse('2016-12-14T07:52:26Z'),
    order_id='ce17b4cb-147f-48b7-b8e6-dde2fa397f04',
    currency_code='USD',
    purchase_country='PL',
    capture_id='33db6f16-9f43-43fa-a587-cc51411c98e4',
    merchant_reference_1='merchant_reference16',
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
```

