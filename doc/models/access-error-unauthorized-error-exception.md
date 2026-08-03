
# Access Error Unauthorized Error Exception

The presented credentials failed authentication.

*This model accepts additional fields of type Any.*

## Structure

`AccessErrorUnauthorizedErrorException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | `str` | Required, Constant | Error code within the error type<br><br>**Value**: `"UNAUTHORIZED"` |
| `error_type` | `str` | Required, Constant | The type of error.<br><br>**Value**: `"ACCESS_ERROR"` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except AccessErrorUnauthorizedErrorException as e:
    print(e)
except ApiException as e:
    print(e)
```

