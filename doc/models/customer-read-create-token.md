
# Customer Read Create Token

*This model accepts additional fields of type Any.*

## Structure

`CustomerReadCreateToken`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `date_of_birth` | `str` | Optional | Customer’s date of birth. The format is ‘yyyy-mm-dd’ |
| `gender` | `str` | Optional | Customer’s gender - ‘male’ or ‘female’ |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.customer_read_create_token import CustomerReadCreateToken

customer_read_create_token = CustomerReadCreateToken(
    date_of_birth='1978-12-31',
    gender='male',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

