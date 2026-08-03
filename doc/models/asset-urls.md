
# Asset Urls

*This model accepts additional fields of type Any.*

## Structure

`AssetUrls`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `descriptive` | `str` | Optional | URL of the descriptive asset. Using this dynamic asset will make sure that any copy update of Klarna will automatically be propagated. |
| `standard` | `str` | Optional | URL of the standard asset. Using this dynamic asset will make sure that any copy update of Klarna will automatically be propagated. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.asset_urls import AssetUrls

asset_urls = AssetUrls(
    descriptive='https://x.klarnacdn.net/payment-method/assets/badges/generic/klarna.svg',
    standard='https://x.klarnacdn.net/payment-method/assets/badges/generic/klarna.svg',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

