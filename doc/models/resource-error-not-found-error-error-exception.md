
# Resource Error Not Found Error Error Exception

The requested resource was not found.

*This model accepts additional fields of type Any.*

## Structure

`ResourceErrorNotFoundErrorErrorException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | [`ErrorCode5`](../../doc/models/error-code-5.md) | Required | Error code within the error type<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_type` | [`ErrorType`](../../doc/models/error-type.md) | Required | The type of error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except ResourceErrorNotFoundErrorErrorException as e:
    print(e)
except ApiException as e:
    print(e)
```

