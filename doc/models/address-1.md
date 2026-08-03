
# Address 1

*This model accepts additional fields of type Any.*

## Structure

`Address1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `attention` | `str` | Optional | ‘Attn.’ (if applicable). Only applicable for B2B customers.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `city` | `str` | Optional | Customer’s city.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `country` | `str` | Optional | Customer’s country. This value overrides the purchase country if they are different. Should follow the standard of ISO 3166 alpha-2. E.g. GB, US, DE, SE.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{2,2}$` |
| `email` | `str` | Optional | Customer’s email address.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `family_name` | `str` | Optional | Customers family name in UTF-8 encoding.<br>Cannot be only numbers, must be more than 1 character.<br>Allowed special characters: -'’.<br>More information can be found [in this link](https://docs.klarna.com/klarna-payments/in-depth-knowledge/customer-data-requirements/#details-needed-per-market)<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `given_name` | `str` | Optional | Customers given name in UTF-8 encoding.<br>Cannot be only numbers, must be more than 1 character.<br>Allowed special characters: -'’.<br>More information can be found [in this link](https://docs.klarna.com/klarna-payments/in-depth-knowledge/customer-data-requirements/#details-needed-per-market)<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `organization_name` | `str` | Optional | Organization name (if applicable). Only applicable for B2B customers.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `phone` | `str` | Optional | Phone number. Preferably a mobile phone number.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `postal_code` | `str` | Optional | Customer’s postal code. Validation according to [Universal Postal Union addressing system](https://www.upu.int/en/activities/addressing/postal-addressing-systems-in-member-countries.html).<br>E.g. 12345, W1G OPW.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `10` |
| `region` | `str` | Optional | Customer’s region or state - Mandatory for US and AU market. Validations according to ISO 3166-2 format, e.g. US-OH, AU-ACT, etc.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `street_address` | `str` | Optional | Customer’s street address. Validation according to [Universal Postal Union addressing system](https://www.upu.int/en/activities/addressing/postal-addressing-systems-in-member-countries.html). Regional formatting is required, as follows:<br>UK/US/FR: 33 Cavendish Square<br>Rest of EU: De Ruijterkade 7<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `street_address_2` | `str` | Optional | Customer’s street address. Second Line.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `99` |
| `title` | `str` | Optional | Customer’s Title. Allowed values per country:<br>UK - "Mr", "Ms"<br>DE - "Herr", "Frau"<br>AT: "Herr, "Frau"<br>CH: de-CH: "Herr, "Frau" it-CH: "Sig.", "Sig.ra" fr-CH: "M", "Mme"<br>BE: "Dhr.", "Mevr."<br>NL: "Dhr.", "Mevr."<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `20` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address_1 import Address1

address_1 = Address1(
    attention='Attn',
    city='New York',
    country='US',
    email='test.sam@test.com',
    family_name='Andersson',
    given_name='Adam',
    phone='+13106683312',
    postal_code='10024-3941',
    region='US-NY',
    street_address='509 Amsterdam Ave',
    street_address_2='Floor 22 / Flat 2',
    title='Mr.',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

