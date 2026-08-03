
# Promise Request

*This model accepts additional fields of type Any.*

## Structure

`PromiseRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Required | A valid order id |
| `cards` | [`List[CardSpecification]`](../../doc/models/card-specification.md) | Required | The cards you would like to issue (max 1000)<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `1000` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.card_specification import CardSpecification
from klarna.models.promise_request import PromiseRequest

promise_request = PromiseRequest(
    order_id='f3392f8b-6116-4073-ab96-e330819e2c07',
    cards=[
        CardSpecification(
            amount=10000,
            currency='USD',
            reference='yPGw6i4lR0GTcyxGpS3Q6Q==',
            fund_amount=10000,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

