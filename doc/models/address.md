
# Address

Shipping address for the capture.

*This model accepts additional fields of type Any.*

## Structure

`Address`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `attention` | `str` | Optional | 'Attn.' - optional parameter.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `city` | `str` | Optional | City.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `200` |
| `country` | `str` | Optional | Country. ISO 3166 alpha-2. |
| `email` | `str` | Optional | E-mail address.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `family_name` | `str` | Optional | Family name.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `given_name` | `str` | Optional | Given name.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `organization_name` | `str` | Optional | Organization name (if applicable). Only applicable for B2B customers.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `phone` | `str` | Optional | Phone number.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `postal_code` | `str` | Optional | Postcode. Validation according to [Universal Postal Union addressing system](https://www.upu.int/en/activities/addressing/postal-addressing-systems-in-member-countries.html).<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `10` |
| `region` | `str` | Optional | State/Region. Required for US.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `200` |
| `street_address` | `str` | Optional | First line of street address. Validation according to [Universal Postal Union addressing system](https://www.upu.int/en/activities/addressing/postal-addressing-systems-in-member-countries.html)<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `street_address_2` | `str` | Optional | Second line of street address.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `title` | `str` | Optional | Title.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `20` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.address import Address

address = Address(
    attention='John Smith',
    city='New York',
    country='US',
    email='test.sam@test.com',
    family_name='Andersson',
    given_name='Adam',
    organization_name='Klarna',
    phone='1-555-555-5555',
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

