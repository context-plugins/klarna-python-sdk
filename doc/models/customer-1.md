
# Customer 1

*This model accepts additional fields of type Any.*

## Structure

`Customer1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `customer_token` | `str` | Optional | Klarna Customer Token. This token can be used to identify a returning customer and provide a faster checkout experience. |
| `date_of_birth` | `str` | Optional | Customer’s date of birth. The format is ‘yyyy-mm-dd’ |
| `gender` | `str` | Optional | Customer’s gender - ‘male’ or ‘female’ |
| `last_four_ssn` | `str` | Optional | Last four digits of the customer's social security number. This value is available for US customers.<br><br>**Constraints**: *Pattern*: `^([0-9]{4}\|[0-9]{9})$` |
| `national_identification_number` | `str` | Optional | The customer's national identification number. This value is available for EU customers utilizing national identification numbers. |
| `organization_entity_type` | [`OrganizationEntityType`](../../doc/models/organization-entity-type.md) | Optional | Organization entity type. Only applicable for B2B customers. |
| `organization_registration_id` | `str` | Optional | Organization registration id. Only applicable for B2B customers. |
| `title` | `str` | Optional | Customer’s Title. Allowed values per country:<br>UK - "Mr", "Ms"<br>DE - "Herr", "Frau"<br>AT: "Herr, "Frau"<br>CH: de-CH: "Herr, "Frau" it-CH: "Sig.", "Sig.ra" fr-CH: "M", "Mme"<br>BE: "Dhr.", "Mevr."<br>NL: "Dhr.", "Mevr." |
| `mtype` | `str` | Optional | Type of customer in the session. If nothing is added, a B2C session will be the default. If it is a b2b-session, you should enter organization to trigger a B2B session.<br><br>**Constraints**: *Pattern*: `^(person\|organization)$` |
| `vat_id` | `str` | Optional | VAT ID. Only applicable for B2B customers. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.customer_1 import Customer1

customer_1 = Customer1(
    customer_token='36115bcd-708d-4712-8c06-976ac5817e18',
    date_of_birth='1978-12-31',
    gender='male',
    last_four_ssn='last_four_ssn4',
    national_identification_number='national_identification_number6',
    title='Mr.',
    mtype='organization',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

