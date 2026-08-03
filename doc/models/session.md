
# Session

*This model accepts additional fields of type Any.*

## Structure

`Session`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `acquiring_channel` | [`AcquiringChannel`](../../doc/models/acquiring-channel.md) | Optional | The acquiring channel in which the session takes place. Ecommerce is default unless specified. Any other values should be defined in the agreement. |
| `attachment` | [`Attachment1`](../../doc/models/attachment-1.md) | Optional | Extra Merchant Data (additional information) required for additional risk check. The required parameters will be described in the appendix of contract agreement. |
| `authorization_token` | `str` | Optional, Read-only | Authorization token. |
| `billing_address` | [`Address1`](../../doc/models/address-1.md) | Optional | Provide the billing address of the customer, if you have collected already. If not, then Klarna will collect the details inside the iFrame before authorization. |
| `client_token` | `str` | Optional, Read-only | Token to be passed to the JS client<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `4096` |
| `custom_payment_method_ids` | `List[str]` | Optional | Promo codes - The array could be used to define which of the configured payment options within a payment category (pay_later, pay_over_time, etc.) should be shown for this purchase. Discuss with the delivery manager to know about the promo codes that will be configured for your account. The feature could also be used to provide promotional offers to specific customers (eg: 0% financing). Please be informed that the usage of this feature can have commercial implications. |
| `customer` | [`Customer1`](../../doc/models/customer-1.md) | Optional | Object to provide the details of the customer making the payment. |
| `design` | `str` | Optional | Design package to use in the session. This can only by used if a custom design has been implemented for Klarna Payments and agreed upon in the agreement. It might have a financial impact. Delivery manager will provide the value for the parameter. |
| `expires_at` | `datetime` | Optional, Read-only | Session expiration date |
| `locale` | `str` | Optional | Used to define the language and region of the customer. The locale follows the format of [RFC 1766](https://datatracker.ietf.org/doc/rfc1766/), meaning its value consists of language-country.<br>Read more on **[Supported Locals and Currencies](https://docs.klarna.com/klarna-payments/in-depth-knowledge/puchase-countries-currencies-locales/)**.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{2,2}(?:-[A-Za-z]{2,2})*$` |
| `merchant_data` | `str` | Optional | Pass through field to send any information about the order to be used later for reference while retrieving the order details (max 6000 characters)<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `6000` |
| `merchant_reference_1` | `str` | Optional | Used for storing merchant's internal order number or other reference.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `merchant_reference_2` | `str` | Optional | Used for storing merchant's internal order number or other reference. The value is available in the settlement files. (max 255 characters).<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `255` |
| `merchant_urls` | [`MerchantUrls`](../../doc/models/merchant-urls.md) | Optional | Used to send in the different merchant URLs that Klarna needs at different stages of the process. |
| `options` | [`Options1`](../../doc/models/options-1.md) | Optional | Design customization options for the Klarna Payments iframe. The design options are limited to changing colors. It is not possible to change the font or other designs at the moment. |
| `order_amount` | `int` | Optional | Total amount of the order including tax and any available discounts. The value should be in non-negative minor units. Eg: 25 Euros should be 2500.<br><br>**Constraints**: `>= 0` |
| `order_lines` | [`List[OrderLine1]`](../../doc/models/order-line-1.md) | Optional | The array containing list of line items that are part of this order. Maximum of 1000 line items could be processed in a single order.<br><br>**Constraints**: *Minimum Items*: `1`, *Maximum Items*: `1000` |
| `order_tax_amount` | `int` | Optional | Total tax amount of the order. The value should be in non-negative minor units. Eg: 25 Euros should be 2500.<br><br>**Constraints**: `>= 0` |
| `payment_method_categories` | [`List[PaymentMethodCategory2]`](../../doc/models/payment-method-category-2.md) | Optional, Read-only | Available payment method categories<br><br>**Constraints**: *Unique Items Required* |
| `purchase_country` | `str` | Optional | The purchase country of the customer. The billing country always overrides purchase country if the values are different. Formatted according to ISO 3166 alpha-2 standard, e.g. GB, SE, DE, US, etc.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{2,2}$` |
| `purchase_currency` | `str` | Optional | The purchase currency of the order. Formatted according to ISO 4217 standard, e.g. USD, EUR, SEK, GBP, etc.<br><br>**Constraints**: *Pattern*: `^[A-Za-z]{3,3}$` |
| `shipping_address` | [`Address1`](../../doc/models/address-1.md) | Optional | The shipping address of the consumer. Please note that this is not needed unless the customer has explicitly chosen to enter a separate shipping address. Otherwise the billing address will be automatically cloned. |
| `status` | [`Status3`](../../doc/models/status-3.md) | Optional, Read-only | The current status of the session. Possible values: 'complete', 'incomplete' where 'complete' is set when the order has been placed. |
| `intent` | [`Intent`](../../doc/models/intent.md) | Optional | Intent for the session. The field is designed to let partners inform Klarna of the purpose of the customer’s session. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.acquiring_channel import AcquiringChannel
from klarna.models.address_1 import Address1
from klarna.models.attachment_1 import Attachment1
from klarna.models.intent import Intent
from klarna.models.session import Session
from klarna.models.status_3 import Status3

session = Session(
    acquiring_channel=AcquiringChannel.ECOMMERCE,
    attachment=Attachment1(
        body='body4',
        content_type='content_type2',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    authorization_token='authorization_token8',
    billing_address=Address1(
        attention='attention8',
        city='city2',
        country='country2',
        email='email8',
        family_name='family_name8',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    client_token='eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.ewogICJzZXNzaW9uX2lkIiA6ICIw',
    expires_at=dateutil.parser.parse('2038-01-19T03:14:07.000Z'),
    locale='en-US',
    merchant_data='{"order_specific":[{"substore":"Women\'s Fashion","product_name":"Women Sweatshirt"}]}',
    merchant_reference_1='ON4711',
    merchant_reference_2='hdt53h-zdgg6-hdaff2',
    order_amount=2000,
    order_tax_amount=333,
    purchase_country='US',
    purchase_currency='USD',
    status=Status3.COMPLETE,
    intent=Intent.BUY,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

