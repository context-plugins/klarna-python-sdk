
# Settlement Response

*This model accepts additional fields of type Any.*

## Structure

`SettlementResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `settlement_id` | `str` | Optional | Unique settlement identifier. |
| `promise_id` | `str` | Optional | Unique identifier for the promise associated to the settlement. |
| `order_id` | `str` | Optional | Unique identifier for the order associated to the settlement. |
| `cards` | [`List[Card]`](../../doc/models/card.md) | Optional | An array of Card objects. |
| `created_at` | `str` | Optional | Settlement creation datetime (ISO 8601). |
| `expires_at` | `str` | Optional | Settlement expiration datetime (ISO 8601). |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.card import Card
from klarna.models.settlement_response import SettlementResponse

settlement_response = SettlementResponse(
    settlement_id='b0ec0bbd-534c-4b1c-b28a-628bf33c3324',
    promise_id='ee4a8e3a-9dfd-49e0-9ac8-ea2b6c76408c',
    order_id='f3392f8b-6116-4073-ab96-e330819e2c07',
    cards=[
        Card(
            reference='reference6',
            card_id='card_id6',
            amount=100,
            currency='currency8',
            pci_data='pci_data4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    created_at='2018-12-03T10:26:06.000Z',
    expires_at='2018-12-04T10:26:06.000Z',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

