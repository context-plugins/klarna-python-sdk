
# Card

*This model accepts additional fields of type Any.*

## Structure

`Card`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `reference` | `str` | Optional | Identifier to reference order line. |
| `card_id` | `str` | Optional | Unique card identifier. |
| `amount` | `int` | Optional | The total amount available on the card. In minor units. The number of decimals are controlled by the currency. |
| `currency` | `str` | Optional | The ISO 4217 code states which currency it is and how many decimals the amount has. |
| `pci_data` | `str` | Optional | Encrypted, PCI compliant card data. |
| `iv` | `str` | Optional | Initialization vector for symmetric decryption with the AES key. |
| `aes_key` | `str` | Optional | The symmetric key complying the Advanced Encryption Standard. |
| `brand` | `str` | Optional | The brand of the card. |
| `holder` | `str` | Optional | Card holder name on the card. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.card import Card

card = Card(
    reference='yPGw6i4lR0GTcyxGpS3Q6Q==',
    card_id='b846430c-3656-43a1-812e-2ccff4531b7d',
    amount=10000,
    currency='USD',
    pci_data='pci_data2',
    brand='VISA',
    holder='Jane Doe',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

