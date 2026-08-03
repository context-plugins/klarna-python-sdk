
# Acquiring Channel

The acquiring channel in which the session takes place. Ecommerce is default unless specified. Any other values should be defined in the agreement.

## Enumeration

`AcquiringChannel`

## Fields

| Name |
|  --- |
| `ECOMMERCE` |
| `IN_STORE` |
| `TELESALES` |

## Example

```python
from klarna.models.acquiring_channel import AcquiringChannel

acquiring_channel = AcquiringChannel.IN_STORE
```

