
# Merchant Urls

*This model accepts additional fields of type Any.*

## Structure

`MerchantUrls`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `confirmation` | `str` | Optional | URL of the merchant confirmation page. The consumer will be redirected back to the confirmation page if the consumer is sent to the redirect URL after placing the order. Insert {session.id} and/or {order.id} as placeholder to connect either of those IDs to the URL(max 2000 characters).<br><br>**Constraints**: *Maximum Length*: `2000`, *Pattern*: `^https://.*` |
| `notification` | `str` | Optional | URL for notifications on pending orders. Insert {session.id} and/or {order.id} as placeholder to connect either of those IDs to the URL (max 2000 characters).<br><br>**Constraints**: *Maximum Length*: `2000`, *Pattern*: `^https://.*` |
| `push` | `str` | Optional | URL that will be requested when an order is completed. Should be different than checkout and confirmation URLs. Insert {session.id} and/or {order.id} as placeholder to connect either of those IDs to the URL (max 2000 characters).<br><br>**Constraints**: *Maximum Length*: `2000`, *Pattern*: `^https://.*` |
| `authorization` | `str` | Optional | URL for receiving the authorization token when payment is completed. Used for Authorization Callback.<br><br>**Constraints**: *Maximum Length*: `2000`, *Pattern*: `^https://.*` |
| `app_return_url` | `str` | Optional | Mobile application return URL (app scheme with no action deeplink).<br>The customer will be redirected to this URL after third party redirects or redirects to the Klarna Application.<br>It is expected to open the integrating mobile application in it's last state (no state changes or deeplink navigations).<br><br>**Constraints**: *Maximum Length*: `2000`, *Pattern*: `^(?![Hh][Tt][Tt][Pp][Ss]?:)[a-zA-Z][a-zA-Z0-9+.-]*://([a-zA-Z0-9][a-zA-Z0-9.-]*[a-zA-Z0-9])?(/[a-zA-Z0-9._~-]*)*(\?[a-zA-Z0-9._~&=-]*)?$` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.merchant_urls import MerchantUrls

merchant_urls = MerchantUrls(
    confirmation='https://www.example-url.com/confirmation',
    notification='https://www.example-url.com/notification',
    push='https://www.example-url.com/push',
    authorization='https://www.example-url.com/authorization',
    app_return_url='appName://KlarnaPayment',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

