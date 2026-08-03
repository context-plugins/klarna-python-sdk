
# Cancel Order Request Status No Request Found Exception

*This model accepts additional fields of type Any.*

## Structure

`CancelOrderRequestStatusNoRequestFoundException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | `str` | Required, Constant | The status of the order cancellation request.<br><br>**Value**: `"NO_REQUEST_FOUND"` |
| `reason_code` | `str` | Required, Constant | Reason code for the bad request.<br><br>**Value**: `"NO_REQUEST_FOUND"` |
| `reason_message` | `str` | Required | Human-readable message for the bad request. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
try:
    # make the API call
except CancelOrderRequestStatusNoRequestFoundException as e:
    print(e)
except ApiException as e:
    print(e)
```

