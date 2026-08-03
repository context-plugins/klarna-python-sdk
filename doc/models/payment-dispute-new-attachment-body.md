
# Payment Dispute New Attachment Body

New file attachment upload to be linked to a dispute response. This endpoint uses multipart/form-data for file uploads.

## Structure

`PaymentDisputeNewAttachmentBody`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `filename` | `str` | Optional | Optional filename for the uploaded attachment. If not provided, the original filename from the uploaded file will be used. If provided, the file extension must match the extension of the uploaded file. Maximum length is 1000 characters (excluding the file extension).<br><br>**Constraints**: *Minimum Length*: `1`, *Maximum Length*: `1000` |
| `file` | `binary` | Required | The file to upload as binary data. This field is required and must contain the actual file content. Supported file types are: PDF (.pdf), JPEG (.jpg, .jpeg), PNG (.png), and Word documents (.docx). Maximum file size is 7MB. |

## Example

```python
from klarna.models.payment_dispute_new_attachment_body import PaymentDisputeNewAttachmentBody

payment_dispute_new_attachment_body = PaymentDisputeNewAttachmentBody(
    file=None,
    filename='receipt.pdf'
)
```

