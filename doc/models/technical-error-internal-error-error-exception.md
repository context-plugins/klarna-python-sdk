
# Technical Error Internal Error Error Exception

An unexpected error occurred in the API.

The request may be retried without modification after a delay.

If this error persists, please reach out to your Klarna support contact.

*This model accepts additional fields of type Any.*

## Structure

`TechnicalErrorInternalErrorErrorException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `error_id` | `uuid\|str` | Required | Unique error identifier |
| `error_code` | [`ErrorCode`](../../doc/models/error-code.md) | Required | Error code within the error type<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `64` |
| `error_type` | `str` | Required, Constant | The type of error.<br><br>**Value**: `"TECHNICAL_ERROR"` |
| `error_message` | `str` | Required | A human readable error message describing the error.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `doc_url` | `str` | Optional | Link to Klarna docs describing how to use the API to avoid the error, or a more detailed explanation of why the error occurred. For a parameter validation error the url should refer directly to the API specification of the parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2048` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except TechnicalErrorInternalErrorErrorException as e:
    print(e)
except ApiException as e:
    print(e)
```

