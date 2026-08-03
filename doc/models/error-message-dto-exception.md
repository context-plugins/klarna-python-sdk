
# Error Message Dto Exception

*This model accepts additional fields of type Any.*

## Structure

`ErrorMessageDtoException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `correlation_id` | `str` | Optional | - |
| `error_code` | `str` | Optional | - |
| `error_messages` | `List[str]` | Optional | - |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except ErrorMessageDtoException as e:
    print(e)
except ApiException as e:
    print(e)
```

