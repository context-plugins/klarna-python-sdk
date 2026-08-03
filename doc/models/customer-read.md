
# Customer Read

*This model accepts additional fields of type Any.*

## Structure

`CustomerRead`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `date_of_birth` | `str` | Optional | Customer’s date of birth. The format is ‘yyyy-mm-dd’ |
| `gender` | `str` | Optional | Customer’s gender - ‘male’ or ‘female’ |
| `organization_entity_type` | [`OrganizationEntityType`](../../doc/models/organization-entity-type.md) | Optional | Organization entity type. Only applicable for B2B customers. |
| `organization_registration_id` | `str` | Optional | Organization registration id. Only applicable for B2B customers. |
| `title` | `str` | Optional | Customer’s Title. Allowed values per country:<br>UK - "Mr", "Ms"<br>DE - "Herr", "Frau"<br>AT: "Herr, "Frau"<br>CH: de-CH: "Herr, "Frau" it-CH: "Sig.", "Sig.ra" fr-CH: "M", "Mme"<br>BE: "Dhr.", "Mevr."<br>NL: "Dhr.", "Mevr." |
| `mtype` | `str` | Optional | Type of customer in the session. If nothing is added, a B2C session will be the default. If it is a b2b-session, you should enter organization to trigger a B2B session. |
| `vat_id` | `str` | Optional | VAT ID. Only applicable for B2B customers. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.customer_read import CustomerRead
from klarna.models.organization_entity_type import OrganizationEntityType

customer_read = CustomerRead(
    date_of_birth='1978-12-31',
    gender='male',
    organization_entity_type=OrganizationEntityType.LIMITED_PARTNERSHIP,
    organization_registration_id='organization_registration_id8',
    title='Mr.',
    mtype='organization',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

