
# Partner Evidence

Evidence submitted by the partner in response to the representment request. Only present in PRE_ARBITRATION, ARBITRATION, or CLOSED states when showing historical representment data, and only if the partner has responded.

## Structure

`PartnerEvidence`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `created_at` | `datetime` | Required | Timestamp in ISO 8601 with timezone<br>Valid examples:<br><br>- 2025-06-24T05:51<br>- 2025-06-24T05:51:48Z<br>- 2025-06-24T05:51:48.1Z<br>- 2025-06-24T05:51:48.12Z<br>- 2025-06-24T05:51:48.123Z |
| `additional_information` | `str` | Optional | Free-text string with additional information about the dispute response<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `500` |
| `attachments` | [`List[Attachment]`](../../doc/models/attachment.md) | Required | List of evidence files provided by the partner to support the dispute response. Partner can upload one or more files.<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `10` |

## Example

```python
import dateutil.parser

from klarna.models.attachment import Attachment
from klarna.models.partner_evidence import PartnerEvidence

partner_evidence = PartnerEvidence(
    created_at=dateutil.parser.parse('2024-01-01T12:00:00Z'),
    attachments=[
        Attachment(
            payment_dispute_attachment_id='krn:network:us1:live:payment:dispute:1234567890:attachment:1',
            description='Shipment confirmation',
            mime_type='image/jpeg',
            url='/payment/disputes/krn:network:us1:live:payment:dispute:1234567890/attachments/1/download'
        )
    ],
    additional_information='additional_information8'
)
```

