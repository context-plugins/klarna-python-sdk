
# Shipping Info

Shipping information for this capture.

*This model accepts additional fields of type Any.*

## Structure

`ShippingInfo`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `return_shipping_company` | `str` | Optional | Identifier of the shipping company for the return shipment. The value should be a valid SHIPPING_COMPANY from the [Carrier list](https://docs.klarna.com/payments/after-payments/order-management/more-actions/klarna-carrier-partner-list/).<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `return_tracking_number` | `str` | Optional | Tracking number for the return shipment. Maximum 100 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `return_tracking_uri` | `str` | Optional | URL where the customer can track the return shipment. Maximum 1024 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `shipping_company` | `str` | Optional | Identifier of the shipping company. The value should be a valid SHIPPING_COMPANY from the [Carrier list](https://docs.klarna.com/payments/after-payments/order-management/more-actions/klarna-carrier-partner-list/).<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `shipping_method` | `str` | Optional | Shipping method. Allowed values matches (PickUpStore\|Home\|BoxReg\|BoxUnreg\|PickUpPoint\|Own\|Postal\|DHLPackstation\|Digital\|Undefined\|PickUpWarehouse\|ClickCollect\|PalletDelivery)<br><br>**Constraints**: *Pattern*: `(PickUpStore\|Home\|BoxReg\|BoxUnreg\|PickUpPoint\|Own\|Postal\|DHLPackstation\|Digital\|Undefined\|PickUpWarehouse\|ClickCollect\|PalletDelivery)` |
| `tracking_number` | `str` | Optional | Tracking number for the shipment. Maximum 100 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `100` |
| `tracking_uri` | `str` | Optional | URI where the customer can track their shipment. Maximum 1024 characters.<br><br>**Constraints**: *Minimum Length*: `0`, *Maximum Length*: `1024` |
| `additional_properties` | `Dict[str, Any]` | Optional | - |

## Example

```python
import jsonpickle

from klarna.models.shipping_info import ShippingInfo

shipping_info = ShippingInfo(
    return_shipping_company='dhl-express',
    return_tracking_number='93456415674545679888',
    return_tracking_uri='http://shipping.example/findmypackage?93456415674545679888',
    shipping_company='dhl-express',
    shipping_method='Home',
    tracking_number='63456415674545679874',
    tracking_uri='http://shipping.example/findmypackage?63456415674545679874',
    additional_properties={
        'exampleAdditionalProperty': jsonpickle.decode('{"key1":"val1","key2":"val2"}')
    }
)
```

