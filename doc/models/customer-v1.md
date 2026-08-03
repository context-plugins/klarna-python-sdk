
# Customer V1

*This model accepts additional fields of type Any.*

## Structure

`CustomerV1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `date_of_birth` | `str` | Optional | Customer's date of birth (YYYY-MM-dd) |
| `family_name` | `str` | Optional | Customer's family name |
| `given_name` | `str` | Optional | Customer's given name |
| `national_identification_number` | `str` | Optional | Customer's national identity number |
| `title` | `str` | Optional | Customer's title |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.customer_v_1 import CustomerV1

customer_v_1 = CustomerV1(
    date_of_birth='1987-08-15',
    family_name='family_name8',
    given_name='given_name6',
    national_identification_number='19870815-84932',
    title='Mr',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

