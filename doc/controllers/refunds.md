# Refunds

```python
refunds_api = client.refunds
```

## Class Name

`RefundsApi`

## Methods

* [Refund Order](../../doc/controllers/refunds.md#refund-order)
* [Get](../../doc/controllers/refunds.md#get)


# Refund Order

Create a refund. Read more on [Refunds](https://docs.klarna.com/payments/after-payments/order-management/manage-orders-with-the-api/refund-orders-and-manage-authorizations/)

```python
def refund_order(self,
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
| `body` | [`RefundObject`](../../doc/models/refund-object.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**201**: Refund created

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type `str`.

## Example Usage

```python
order_id = 'order_id6'

body = RefundObject(
    refunded_amount=72
)

result = refunds_api.refund_order(
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
| 403 | Refund not allowed | [`RefundNotAllowedErrorMessageException`](../../doc/models/refund-not-allowed-error-message-exception.md) |
| 404 | Order not found. | [`NotFoundErrorMessageException`](../../doc/models/not-found-error-message-exception.md) |


# Get

Get refund.

```python
def get(self,
       order_id,
       refund_id)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `refund_id` | `str` | Template, Required | Refund id |

## Response Type

**200**: Refund found.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`Refund`](../../doc/models/refund.md).

## Example Usage

```python
order_id = 'order_id6'

refund_id = 'refund_id4'

result = refunds_api.get(
    order_id,
    refund_id
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Order or refund not found. | [`NotFoundErrorMessageException`](../../doc/models/not-found-error-message-exception.md) |

