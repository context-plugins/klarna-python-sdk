
# Product Identifiers

product_identifiers

*This model accepts additional fields of type Any.*

## Structure

`ProductIdentifiers`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `brand` | `str` | Optional | The product's brand name as generally recognized by consumers. If no brand is available for a product, do not supply any value. Maximum 70 characters. Example: Intel<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `70` |
| `category_path` | `str` | Optional | The product's category path as used in the merchant's webshop. Include the full and most detailed category and separate the segments with ' > '. Maximum 750 characters. Example: Electronics Store > Computers & Tablets > Desktops<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `750` |
| `color` | `str` | Optional | Color to be shown to the end customer (max 64 characters). Example: Denim blue<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `global_trade_item_number` | `str` | Optional | The product's Global Trade Item Number (GTIN). Common types of GTIN are EAN, ISBN or UPC. Exclude dashes and spaces, where possible. Maximum 50 characters. Example: 735858293167<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `50` |
| `manufacturer_part_number` | `str` | Optional | The product's Manufacturer Part Number (MPN), which - together with the brand - uniquely identifies a product. Only submit MPNs assigned by a manufacturer and use the most specific MPN possible. Maximum 70 characters. Example: BOXNUC5CPYH<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `70` |
| `size` | `str` | Optional | Size to be shown to the end customer (max 64 characters). Example: 4<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.product_identifiers import ProductIdentifiers

product_identifiers = ProductIdentifiers(
    brand='Intel',
    category_path='Electronics Store > Computers & Tablets > Desktops',
    color='Denim blue',
    global_trade_item_number='735858293167',
    manufacturer_part_number='BOXNUC5CPYH',
    size='4',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

