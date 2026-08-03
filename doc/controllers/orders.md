# Orders

```python
orders_api = client.orders
```

## Class Name

`OrdersApi`

## Methods

* [Get Order](../../doc/controllers/orders.md#get-order)
* [Acknowledge Order](../../doc/controllers/orders.md#acknowledge-order)
* [Update Authorization](../../doc/controllers/orders.md#update-authorization)
* [Update Consumer Details](../../doc/controllers/orders.md#update-consumer-details)
* [Extend Authorization Time](../../doc/controllers/orders.md#extend-authorization-time)
* [Update Merchant References](../../doc/controllers/orders.md#update-merchant-references)
* [Release Remaining Authorization](../../doc/controllers/orders.md#release-remaining-authorization)
* [Append Order Shipping Info](../../doc/controllers/orders.md#append-order-shipping-info)
* [Cancel Order](../../doc/controllers/orders.md#cancel-order)


# Get Order

An order that has the given order id. Read more on [Retrieving order details](https://docs.klarna.com/order-management/pre-delivery/order-details/)

```python
def get_order(self,
             order_id,
             klarna_integrator=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `klarna_integrator` | `str` | Header, Optional | - |

## Response Type

**200**: Order found

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`MerchantOrderDto`](../../doc/models/merchant-order-dto.md).

## Example Usage

```python
order_id = 'order_id6'

result = orders_api.get_order(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Order not found | [`NoSuchOrderErrorMessageException`](../../doc/models/no-such-order-error-message-exception.md) |


# Acknowledge Order

Acknowledge order. Read more on [Acknowledging orders](https://docs.klarna.com/order-management/pre-delivery/acknowledge-kco-order/)

```python
def acknowledge_order(self,
                     order_id,
                     klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Order was acknowledged.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

result = orders_api.acknowledge_order(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Update not allowed. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |
| 404 | Order not found. | [`NoSuchOrderErrorMessageException`](../../doc/models/no-such-order-error-message-exception.md) |


# Update Authorization

Set new order amount and order lines. Read more on [Updating orders](https://docs.klarna.com/order-management/pre-delivery/update-order-amount/)

```python
def update_authorization(self,
                        order_id,
                        body,
                        klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `body` | [`UpdateAuthorization`](../../doc/models/update-authorization.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Authorization was updated.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type `str`.

## Example Usage

```python
order_id = 'order_id6'

body = UpdateAuthorization(
    order_amount=188,
    description='Added charger'
)

result = orders_api.update_authorization(
    order_id,
    body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Update authorization not allowed. Decision is based on order state and outcome of risk assessment. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |


# Update Consumer Details

Update shipping address. Read more on [Updating customer addresses](https://docs.klarna.com/order-management/pre-delivery/update-customer-address/)

```python
def update_consumer_details(self,
                           order_id,
                           body,
                           klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `body` | [`UpdateConsumer`](../../doc/models/update-consumer.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Order consumer details were updated.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type `str`.

## Example Usage

```python
order_id = 'order_id6'

body = UpdateConsumer()

result = orders_api.update_consumer_details(
    order_id,
    body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Update customer details not allowed. Decision is based on order state and outcome of risk assessment. Billing address cannot be updated. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |


# Extend Authorization Time

Extend authorization time endpoints provide flexibility when unexpected delays occur, however if long fulfillment periods are standard business model, then the extension of authorizations should be defined as part of the onboarding. Read more on [Extending order authorization time](https://docs.klarna.com/payments/web-payments/additional-resources/use-cases/extended-authorization-expiration/)

```python
def extend_authorization_time(self,
                             order_id,
                             klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Authorization time was extended.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

result = orders_api.extend_authorization_time(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Extension of authorization time not allowed. The order being expired or cancelled are among the possible causes. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |


# Update Merchant References

Update merchant references. Read more on [Updating merchant references](https://docs.klarna.com/order-management/pre-delivery/update-merchant-references/)

```python
def update_merchant_references(self,
                              order_id,
                              body,
                              klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `body` | [`UpdateMerchantReferences`](../../doc/models/update-merchant-references.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Order merchant references were updated.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

body = UpdateMerchantReferences()

result = orders_api.update_merchant_references(
    order_id,
    body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Can not update a cancelled order. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |


# Release Remaining Authorization

Release remaining authorization. Read more on [Releasing remaining authorization](https://docs.klarna.com/payments/after-payments/order-management/manage-orders-with-the-api/refund-orders-and-manage-authorizations/#release-order-authorization)

```python
def release_remaining_authorization(self,
                                   order_id,
                                   klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Remaining authorization was released.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type `str`.

## Example Usage

```python
order_id = 'order_id6'

result = orders_api.release_remaining_authorization(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Can not release when order is cancelled or has no captures. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |


# Append Order Shipping Info

Add shipping info to an order. Read more on [Adding shipping info](https://docs.klarna.com/order-management/manage-orders-with-the-api/view-and-change-orders/add-shipping-information/)

```python
def append_order_shipping_info(self,
                              order_id,
                              body,
                              klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `body` | [`UpdateShippingInfo`](../../doc/models/update-shipping-info.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Shipping information was appended.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

body = UpdateShippingInfo(
    shipping_info=[
        ShippingInfo(
            return_shipping_company='dhl-express',
            return_tracking_number='93456415674545679888',
            return_tracking_uri='http://shipping.example/findmypackage?93456415674545679888',
            shipping_company='dhl-express',
            shipping_method='Home',
            tracking_number='63456415674545679874',
            tracking_uri='http://shipping.example/findmypackage?63456415674545679874'
        )
    ]
)

result = orders_api.append_order_shipping_info(
    order_id,
    body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Order not found. | [`NoSuchOrderErrorMessageException`](../../doc/models/no-such-order-error-message-exception.md) |


# Cancel Order

Cancel order. Read more on [Cancelling an order](https://docs.klarna.com/order-management/pre-delivery/cancel-order/)

```python
def cancel_order(self,
                order_id,
                klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Order was cancelled.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

result = orders_api.cancel_order(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Cancel not allowed (e.g. order has captures or is closed) | [`CancelNotAllowedErrorMessageException`](../../doc/models/cancel-not-allowed-error-message-exception.md) |

