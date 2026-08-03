
# Payment Dispute Representment Request

Request for information towards the associated partner

## Structure

`PaymentDisputeRepresentmentRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `additional_information` | `str` | Required | Free-text string with additional information about the dispute request<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `2000` |
| `requested_at` | `datetime` | Required | Timestamp of when the representment request was created |

## Example

```python
import dateutil.parser

from klarna.models.payment_dispute_representment_request import PaymentDisputeRepresentmentRequest

payment_dispute_representment_request = PaymentDisputeRepresentmentRequest(
    additional_information='additional_information6',
    requested_at=dateutil.parser.parse('2024-01-01T12:00:00Z')
)
```

