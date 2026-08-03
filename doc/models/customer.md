
# Customer

Information about the customer placing the order.

*This model accepts additional fields of type Any.*

## Structure

`Customer`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `date_of_birth` | `date` | Optional | The customer date of birth. ISO 8601. |
| `national_identification_number` | `str` | Optional | The customer national identification number |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.customer import Customer

customer = Customer(
    date_of_birth=dateutil.parser.parse('1981-09-06').date(),
    national_identification_number='national_identification_number2',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

