
# Settlement Request

*This model accepts additional fields of type Any.*

## Structure

`SettlementRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `promise_id` | `str` | Optional | Unique identifier for the promise associated to the settlement. |
| `order_id` | `str` | Required | Unique identifier for the order associated to the settlement. |
| `key_id` | `str` | Required | Unique identifier for the public key to be used for encryption of the card data. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.settlement_request import SettlementRequest

settlement_request = SettlementRequest(
    order_id='f3392f8b-6116-4073-ab96-e330819e2c07',
    key_id='16e4b85e-899b-4427-a39f-07a496e9515b',
    promise_id='ee4a8e3a-9dfd-49e0-9ac8-ea2b6c76408c',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

