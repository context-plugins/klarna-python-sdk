
# Promise Response

*This model accepts additional fields of type Any.*

## Structure

`PromiseResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `promise_id` | `str` | Optional, Read-only | The unique promise ID |
| `order_id` | `str` | Optional, Read-only | The order id of the promise |
| `cards` | [`List[CardSpecification]`](../../doc/models/card-specification.md) | Optional, Read-only | The list of card specifications |
| `created_at` | `datetime` | Optional, Read-only | The time when the promise was created |
| `expire_at` | `datetime` | Optional, Read-only | The time when the promise expires |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.card_specification import CardSpecification
from klarna.models.promise_response import PromiseResponse

promise_response = PromiseResponse(
    promise_id='ee4a8e3a-9dfd-49e0-9ac8-ea2b6c76408c',
    order_id='f3392f8b-6116-4073-ab96-e330819e2c07',
    cards=[
        CardSpecification(
            amount=100,
            currency='currency8',
            reference='reference6',
            fund_amount=108,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        CardSpecification(
            amount=100,
            currency='currency8',
            reference='reference6',
            fund_amount=108,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        CardSpecification(
            amount=100,
            currency='currency8',
            reference='reference6',
            fund_amount=108,
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    created_at=dateutil.parser.parse('2018-12-03T10:26:06.000Z'),
    expire_at=dateutil.parser.parse('2018-12-04T10:26:06.000Z'),
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

