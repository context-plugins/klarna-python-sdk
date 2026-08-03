
# Order

*This model accepts additional fields of type Any.*

## Structure

`Order`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `authorized_payment_method` | [`AuthorizedPaymentMethod`](../../doc/models/authorized-payment-method.md) | Optional | The payment method that Klarna has authorized the customer for. |
| `fraud_status` | `str` | Optional | Fraud status for the order. Either ACCEPTED or PENDING. If ACCEPTED, the order could be captured. If PENDING, please wait till you receive the notification from Klarna in the notification URL that the order has been approved. You can find additional information [here](https://docs.klarna.com/payments/after-payments/order-management/more-actions/pending-orders/). |
| `order_id` | `str` | Required | Unique order ID of the transaction. This ID will be used for all order management processes. |
| `redirect_url` | `str` | Optional | URL to redirect the customer to after placing the order. This is a Klarna URL to which the merchant should redirect the customer to. Klarna will place a cookie in the customer’s browser (if redirected) and redirect the customer back to the confirmation URL provided by the merchant. This is not a mandatory step but a recommended one to improve the returning customer’s experience. It is a spontaneous step and does not harm the customer’s experience. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.authorized_payment_method import AuthorizedPaymentMethod
from klarna.models.order import Order
from klarna.models.type_1 import Type1

order = Order(
    order_id='order_id0',
    authorized_payment_method=AuthorizedPaymentMethod(
        mtype=Type1.FIXED_SUM_CREDIT,
        number_of_days=242,
        number_of_installments=122,
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    fraud_status='fraud_status2',
    redirect_url='https://credit.klarna.com/v1/sessions/0b1d9815-165e-42e2-8867-35bc03789e00/redirect',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

