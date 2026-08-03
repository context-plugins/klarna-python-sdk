
# Card Specification

*This model accepts additional fields of type Any.*

## Structure

`CardSpecification`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `amount` | `int` | Required | The total purchase amount on a card<br><br>**Constraints**: `>= 1` |
| `currency` | `str` | Required | The amount currency |
| `fund_amount` | `int` | Optional | The funded amount that will be on a card |
| `reference` | `str` | Required | Your reference on the card<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `255` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.card_specification import CardSpecification

card_specification = CardSpecification(
    amount=10000,
    currency='USD',
    reference='yPGw6i4lR0GTcyxGpS3Q6Q==',
    fund_amount=10000,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

