
# Customer Token Creation Response

*This model accepts additional fields of type Any.*

## Structure

`CustomerTokenCreationResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `billing_address` | [`Address1`](../../doc/models/address-1.md) | Optional | Provide the billing address of the customer, if you have collected already. If not, then Klarna will collect the details inside the iFrame before authorization. |
| `customer` | [`CustomerReadCreateToken`](../../doc/models/customer-read-create-token.md) | Optional | Object to provide the details of the customer making the payment. |
| `payment_method_reference` | `str` | Optional | Used to connect customers with payment method when it is present. |
| `redirect_url` | `str` | Optional | URL to redirect the customer to after placing the order. This is a Klarna URL where Klarna will place a cookie in the customer’s browser (if redirected) and redirect the customer back to the confirmation URL provided by the merchant. This is not a mandatory step but a recommended one to improve the returning customer’s experience. |
| `token_id` | `str` | Required | Generated customer token. This token will be used to create a new order for the subscription using the Create a New order using token API. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address_1 import Address1
from klarna.models.customer_read_create_token import CustomerReadCreateToken
from klarna.models.customer_token_creation_response import CustomerTokenCreationResponse

customer_token_creation_response = CustomerTokenCreationResponse(
    token_id='0b1d9815-165e-42e2-8867-35bc03789e00',
    billing_address=Address1(
        attention='attention8',
        city='city2',
        country='country2',
        email='email8',
        family_name='family_name8',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    customer=CustomerReadCreateToken(
        date_of_birth='date_of_birth8',
        gender='gender6',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    payment_method_reference='0b1d9815-165e-42e2-8867-35bc03789e00',
    redirect_url='https://credit.klarna.com/v1/sessions/0b1d9815-165e-42e2-8867-35bc03789e00/redirect',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

