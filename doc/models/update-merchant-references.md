
# Update Merchant References

*This model accepts additional fields of type Any.*

## Structure

`UpdateMerchantReferences`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `merchant_reference_1` | `str` | Optional | New merchant reference 1. Old reference will be overwritten if this field is present.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `merchant_reference_2` | `str` | Optional | New merchant reference 2. Old reference will be overwritten if this field is present.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.update_merchant_references import UpdateMerchantReferences

update_merchant_references = UpdateMerchantReferences(
    merchant_reference_1='merchant_reference14',
    merchant_reference_2='merchant_reference24',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

