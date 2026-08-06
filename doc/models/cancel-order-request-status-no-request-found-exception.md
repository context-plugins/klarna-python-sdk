
# Cancel Order Request Status No Request Found Exception

*This model accepts additional fields of type Any.*

## Structure

`CancelOrderRequestStatusNoRequestFoundException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | [`Status3`](../../doc/models/status-3.md) | Required | The status of the order cancellation request. |
| `reason_code` | [`ReasonCode1`](../../doc/models/reason-code-1.md) | Required | Reason code for the bad request. |
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

