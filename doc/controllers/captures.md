# Captures

```python
captures_api = client.captures
```

## Class Name

`CapturesApi`

## Methods

* [Capture Order](../../doc/controllers/captures.md#capture-order)
* [Get Captures](../../doc/controllers/captures.md#get-captures)
* [Get Capture](../../doc/controllers/captures.md#get-capture)
* [Extend Due Date](../../doc/controllers/captures.md#extend-due-date)
* [Get Options for Extend Due Date](../../doc/controllers/captures.md#get-options-for-extend-due-date)
* [Append Shipping Info](../../doc/controllers/captures.md#append-shipping-info)
* [Trigger Send Out](../../doc/controllers/captures.md#trigger-send-out)


# Capture Order

Create capture. Read more on [Capturing an order](https://docs.klarna.com/order-management/delivery/full-capture/)

```python
def capture_order(self,
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
| `body` | [`CaptureObject`](../../doc/models/capture-object.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**201**: Capture created

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

body = CaptureObject(
    captured_amount=226
)

result = captures_api.capture_order(
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
| 403 | Capture not allowed. | [`CaptureNotAllowedErrorMessageException`](../../doc/models/capture-not-allowed-error-message-exception.md) |
| 404 | Order not found. | [`NoSuchOrderErrorMessageException`](../../doc/models/no-such-order-error-message-exception.md) |


# Get Captures

List all order captures

```python
def get_captures(self,
                order_id)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |

## Response Type

**200**: Captures found.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`List[Capture]`](../../doc/models/capture.md).

## Example Usage

```python
order_id = 'order_id6'

result = captures_api.get_captures(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Order not found. | [`NoSuchOrderErrorMessageException`](../../doc/models/no-such-order-error-message-exception.md) |


# Get Capture

Retrieve the details of a capture. To learn more, refer to the [Retrieving capture details](https://docs.klarna.com/order-management/post-delivery/capture-details/) article.

```python
def get_capture(self,
               order_id,
               capture_id)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `capture_id` | `str` | Template, Required | Capture id |

## Response Type

**200**: Capture found.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`Capture`](../../doc/models/capture.md).

## Example Usage

```python
order_id = 'order_id6'

capture_id = 'capture_id2'

result = captures_api.get_capture(
    order_id,
    capture_id
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Order or capture not found. | [`NoSuchOrderErrorMessageException`](../../doc/models/no-such-order-error-message-exception.md) |


# Extend Due Date

Extend the customer's payment due date. Read more on [Extending customer due dates](https://docs.klarna.com/payments/after-payments/order-management/manage-orders-with-the-api/refund-orders-and-manage-authorizations/#extend-payment-date)

```python
def extend_due_date(self,
                   order_id,
                   capture_id,
                   body,
                   klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `capture_id` | `str` | Template, Required | Capture id |
| `body` | [`ExtendDueDateRequest`](../../doc/models/extend-due-date-request.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Due date was extended.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

capture_id = 'capture_id2'

body = ExtendDueDateRequest(
    number_of_days=74
)

result = captures_api.extend_due_date(
    order_id,
    capture_id,
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
| 403 | Extension of due date is not possible. | [`ErrorMessageDtoException`](../../doc/models/error-message-dto-exception.md) |
| 404 | Order or capture not found. | [`ErrorMessageDtoException`](../../doc/models/error-message-dto-exception.md) |


# Get Options for Extend Due Date

Get merchant fees for extension of due date due date

```python
def get_options_for_extend_due_date(self,
                                   order_id,
                                   capture_id)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `capture_id` | `str` | Template, Required | Capture id |

## Response Type

**200**: Available options found for capture.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`ExtendDueDateOptions`](../../doc/models/extend-due-date-options.md).

## Example Usage

```python
order_id = 'order_id6'

capture_id = 'capture_id2'

result = captures_api.get_options_for_extend_due_date(
    order_id,
    capture_id
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Order or capture not found. | [`ErrorMessageDtoException`](../../doc/models/error-message-dto-exception.md) |


# Append Shipping Info

Add shipping info to a capture. Read more on [Adding shipping info](https://docs.klarna.com/order-management/post-delivery/add-capture-shipping-details/)

```python
def append_shipping_info(self,
                        order_id,
                        capture_id,
                        body,
                        klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `capture_id` | `str` | Template, Required | Capture id |
| `body` | [`UpdateShippingInfo`](../../doc/models/update-shipping-info.md) | Body, Required | - |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Shipping information was appended.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

capture_id = 'capture_id2'

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

result = captures_api.append_shipping_info(
    order_id,
    capture_id,
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
| 403 | Order has no captures. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |
| 404 | Order or capture not found. | [`NoSuchOrderErrorMessageException`](../../doc/models/no-such-order-error-message-exception.md) |


# Trigger Send Out

Trigger resend of customer communication. Read more on [Resending customer communication](https://docs.klarna.com/order-management/post-delivery/trigger-customer-send-out/)

```python
def trigger_send_out(self,
                    order_id,
                    capture_id,
                    klarna_idempotency_key=None)
```

## Authentication

This endpoint requires [basicAuth](../../doc/auth/basic-authentication.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id |
| `capture_id` | `str` | Template, Required | Capture id |
| `klarna_idempotency_key` | `str` | Header, Optional | This header will guarantee the idempotency of the operation. The key should be unique and is recommended to be a UUID version 4. Retries of requests are safe to be applied in case of errors such as network errors, socket errors and timeouts. Input values of the operation are disregarded when evaluating the idempotency of the operation, only the key matters. |

## Response Type

**204**: Send out was triggered

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
order_id = 'order_id6'

capture_id = 'capture_id2'

result = captures_api.trigger_send_out(
    order_id,
    capture_id
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Order has no captures. | [`NotAllowedErrorMessageException`](../../doc/models/not-allowed-error-message-exception.md) |
| 404 | Order or capture not found. | [`NoSuchCaptureErrorMessageException`](../../doc/models/no-such-capture-error-message-exception.md) |

