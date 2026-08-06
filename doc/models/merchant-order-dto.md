
# Merchant Order Dto

Order

*This model accepts additional fields of type Any.*

## Structure

`MerchantOrderDto`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `billing_address` | [`Address`](../../doc/models/address.md) | Optional | Shipping address for the capture. |
| `captured_amount` | `int` | Optional | The total amount of all captures. In minor units. |
| `captures` | [`List[Capture]`](../../doc/models/capture.md) | Optional | List of captures for this order. |
| `created_at` | `datetime` | Optional | The time for the purchase. Formatted according to ISO 8601. |
| `customer` | [`Customer`](../../doc/models/customer.md) | Optional | Information about the customer placing the order. |
| `expires_at` | `datetime` | Optional | Order expiration time. The order can only be captured until this time. Formatted according to ISO 8601. |
| `fraud_status` | `str` | Optional | Fraud status for the order. Either ACCEPTED, PENDING or REJECTED. |
| `initial_payment_method` | [`InitialPaymentMethodDto`](../../doc/models/initial-payment-method-dto.md) | Optional | Initial payment method for this order |
| `klarna_reference` | `str` | Optional | A Klarna generated reference that is shorter than the Klarna Order Id and is used as a customer friendly reference. It is most often used as a reference when Klarna is communicating with the customer with regard to payment statuses. |
| `locale` | `str` | Optional | The customers locale. Specified according to RFC 1766. |
| `merchant_data` | `str` | Optional | Text field for storing data about the order. Set at order creation. |
| `merchant_reference_1` | `str` | Optional | The order number that the merchant should assign to the order. This is how a customer would reference the purchase they made. If supplied, it is labeled as the Order Number within post purchase communications as well as the Klarna App. |
| `merchant_reference_2` | `str` | Optional | Can be used to store your internal reference to the order. This is generally an internal reference number that merchants use as alternate identifier that matches their internal ERP or Order Management system. |
| `order_amount` | `int` | Optional | The order amount in minor units. That is the smallest currency unit available such as cent or penny. |
| `order_id` | `str` | Optional | The unique order ID. Cannot be longer than 255 characters. |
| `order_lines` | [`List[OrderLine]`](../../doc/models/order-line.md) | Optional | An array of order_line objects. Each line represents one item in the cart. |
| `original_order_amount` | `int` | Optional | The original order amount. In minor units. |
| `purchase_country` | `str` | Optional | The purchase country. Formatted according to ISO 3166-1 alpha-2. |
| `purchase_currency` | `str` | Optional | The currency for this order. Specified in ISO 4217 format. |
| `refunded_amount` | `int` | Optional | The total amount of refunded for this order. In minor units. |
| `refunds` | [`List[Refund]`](../../doc/models/refund.md) | Optional | List of refunds for this order. |
| `remaining_authorized_amount` | `int` | Optional | The remaining authorized amount for this order. To increase the `remaining_authorized_amount` the `order_amount` needs to be increased. |
| `selected_shipping_option` | [`SelectedShippingOptionDto`](../../doc/models/selected-shipping-option-dto.md) | Optional | The shipping option selected by the user. |
| `shipping_address` | [`Address`](../../doc/models/address.md) | Optional | Shipping address for the capture. |
| `shipping_info` | [`List[ShippingInfo]`](../../doc/models/shipping-info.md) | Optional | Shipping information for this order. |
| `status` | [`Status4`](../../doc/models/status-4.md) | Optional | The order status. |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import dateutil.parser
import jsonpickle

from klarna.models.address import Address
from klarna.models.capture import Capture
from klarna.models.customer import Customer
from klarna.models.merchant_order_dto import MerchantOrderDto
from klarna.models.status_4 import Status4

merchant_order_dto = MerchantOrderDto(
    billing_address=Address(
        attention='attention8',
        city='city2',
        country='country2',
        email='email8',
        family_name='family_name8',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    captured_amount=0,
    captures=[
        Capture(
            billing_address=Address(
                attention='attention8',
                city='city2',
                country='country2',
                email='email8',
                family_name='family_name8',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            capture_id='capture_id6',
            captured_amount=234,
            captured_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            description='description4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        Capture(
            billing_address=Address(
                attention='attention8',
                city='city2',
                country='country2',
                email='email8',
                family_name='family_name8',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            capture_id='capture_id6',
            captured_amount=234,
            captured_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            description='description4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        ),
        Capture(
            billing_address=Address(
                attention='attention8',
                city='city2',
                country='country2',
                email='email8',
                family_name='family_name8',
                additional_properties={
                    'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
                }
            ),
            capture_id='capture_id6',
            captured_amount=234,
            captured_at=dateutil.parser.parse('2016-03-13T12:52:32.123Z'),
            description='description4',
            additional_properties={
                'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
            }
        )
    ],
    created_at=dateutil.parser.parse('2015-11-29T10:25:40Z'),
    customer=Customer(
        date_of_birth=dateutil.parser.parse('2016-03-13').date(),
        national_identification_number='national_identification_number2',
        additional_properties={
            'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
        }
    ),
    expires_at=dateutil.parser.parse('2015-12-04T10:26:06Z'),
    fraud_status='ACCEPTED',
    klarna_reference='K4MADNY',
    locale='en-US',
    merchant_data='Order metadata',
    merchant_reference_1='10001',
    merchant_reference_2='501',
    order_id='f3392f8b-6116-4073-ab96-e330819e2c07',
    purchase_country='US',
    purchase_currency='USD',
    refunded_amount=0,
    remaining_authorized_amount=0,
    status=Status4.AUTHORIZED,
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

