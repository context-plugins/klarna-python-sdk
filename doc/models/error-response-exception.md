
# Error Response Exception

*This model accepts additional fields of type Any.*

## Structure

`ErrorResponseException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_code` | `str` | Required | ERROR_CODE |
| `error_messages` | `List[str]` | Required | Array of error messages |
| `correlation_id` | `str` | Required | Unique id for this request used for troubleshooting. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except ErrorResponseException as e:
    print(e)
except ApiException as e:
    print(e)
```

