
# Customer Token Creation Request

*This model accepts additional fields of type Any.*

## Structure

`CustomerTokenCreationRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `billing_address` | [`Address1`](../../doc/models/address-1.md) | Optional | Once the customer has provided any data, updates to this object will be ignored (without generating an error). |
| `customer` | [`Customer1`](../../doc/models/customer-1.md) | Optional | Information about the liable customer of the order. |
| `description` | `str` | Required | Description of the purpose of the token.<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `intended_use` | [`IntendedUse`](../../doc/models/intended-use.md) | Required | Intended use for the token. |
| `locale` | `str` | Required | RFC 1766 customer's locale.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{2,2}(?:-[A-Za-z]{2,2})*$` |
| `purchase_country` | `str` | Required | ISO 3166 alpha-2 purchase country.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{2,2}$` |
| `purchase_currency` | `str` | Required | ISO 4217 purchase currency.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{3,3}$` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address_1 import Address1
from klarna.models.customer_1 import Customer1
from klarna.models.customer_token_creation_request import CustomerTokenCreationRequest
from klarna.models.intended_use import IntendedUse

customer_token_creation_request = CustomerTokenCreationRequest(
    description='description0',
    intended_use=IntendedUse.SUBSCRIPTION,
    locale='en-US',
    purchase_country='US',
    purchase_currency='USD',
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
    customer=Customer1(
        customer_token='customer_token2',
        date_of_birth='date_of_birth8',
        gender='gender6',
        last_four_ssn='last_four_ssn0',
        national_identification_number='national_identification_number2',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

