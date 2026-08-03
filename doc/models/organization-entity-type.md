
# Organization Entity Type

Organization entity type. Only applicable for B2B customers.

## Enumeration

`OrganizationEntityType`

## Fields

| Name |
|  --- |
| `LIMITED_COMPANY` |
| `PUBLIC_LIMITED_COMPANY` |
| `ENTREPRENEURIAL_COMPANY` |
| `LIMITED_PARTNERSHIP_LIMITED_COMPANY` |
| `LIMITED_PARTNERSHIP` |
| `GENERAL_PARTNERSHIP` |
| `REGISTERED_SOLE_TRADER` |
| `SOLE_TRADER` |
| `CIVIL_LAW_PARTNERSHIP` |
| `PUBLIC_INSTITUTION` |
| `OTHER` |

## Example

```python
from klarna.models.organization_entity_type import OrganizationEntityType

organization_entity_type = OrganizationEntityType.PUBLIC_INSTITUTION
```

