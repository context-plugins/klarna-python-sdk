
# Not Allowed Error Message Exception

*This model accepts additional fields of type Any.*

## Structure

`NotAllowedErrorMessageException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `correlation_id` | `str` | Optional | Correlation id. For searching logs. |
| `error_code` | `str` | Optional | Error code |
| `error_messages` | `List[str]` | Optional | Error messages |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except NotAllowedErrorMessageException as e:
    print(e)
except ApiException as e:
    print(e)
```

