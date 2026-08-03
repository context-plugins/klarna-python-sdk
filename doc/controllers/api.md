# API

```python
client_api = client.client
```

## Class Name

`Api`

## Methods

* [Create Hpp Session](../../doc/controllers/api.md#create-hpp-session)
* [Get Session by Id](../../doc/controllers/api.md#get-session-by-id)
* [Disable Hpp Session](../../doc/controllers/api.md#disable-hpp-session)
* [Distribute Hpp Session](../../doc/controllers/api.md#distribute-hpp-session)
* [Create Promise](../../doc/controllers/api.md#create-promise)
* [Read Promise](../../doc/controllers/api.md#read-promise)
* [Settle Promise](../../doc/controllers/api.md#settle-promise)
* [Read Settlement](../../doc/controllers/api.md#read-settlement)
* [Read Settlement by Order Id](../../doc/controllers/api.md#read-settlement-by-order-id)
* [Postcancelorder](../../doc/controllers/api.md#postcancelorder)
* [Getcancelorder](../../doc/controllers/api.md#getcancelorder)
* [Create Credit Session](../../doc/controllers/api.md#create-credit-session)
* [Update Credit Session](../../doc/controllers/api.md#update-credit-session)
* [Read Credit Session](../../doc/controllers/api.md#read-credit-session)
* [Cancel Authorization](../../doc/controllers/api.md#cancel-authorization)
* [Create Order](../../doc/controllers/api.md#create-order)
* [Purchase Token](../../doc/controllers/api.md#purchase-token)
* [Get Payout Summary](../../doc/controllers/api.md#get-payout-summary)
* [Get Payout](../../doc/controllers/api.md#get-payout)
* [Get Payouts](../../doc/controllers/api.md#get-payouts)
* [Get Payout Report with Transactions](../../doc/controllers/api.md#get-payout-report-with-transactions)
* [Payout](../../doc/controllers/api.md#payout)
* [Get Transactions](../../doc/controllers/api.md#get-transactions)
* [Get Payouts Summary Report with Transactions](../../doc/controllers/api.md#get-payouts-summary-report-with-transactions)
* [Payouts Summary](../../doc/controllers/api.md#payouts-summary)


# Create Hpp Session

Use this API to create an HPP session after creating a payment session.
Read more on **[Create a new HPP session](https://docs.klarna.com/hosted-payment-page/api-documentation/create-session/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def create_hpp_session(self,
                      body,
                      user_agent=None)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`SessionCreationRequestV1`](../../doc/models/session-creation-request-v1.md) | Body, Required | sessionRequest |
| `user_agent` | `str` | Header, Optional | User-Agent |

## Response Type

**201**: Successfully created HPP session

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`SessionCreationResponseV1`](../../doc/models/session-creation-response-v1.md).

## Example Usage

```python
body = SessionCreationRequestV1(
    payment_session_url='One of https://api.klarna.com/payments/v1/sessions/92d97f60-7a78-46a5-8f68-c56fe52dc4af or https://api.klarna.com/checkout/v3/orders/92d97f60-7a78-46a5-8f68-c56fe52dc4af',
    profile_id='87ab3565-5e06-4006-9ada-8eedc6926703'
)

result = client_api.create_hpp_session(body)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | We were unable to create a session with the provided data. Some field constraint was violated. | `ApiException` |
| 401 | Unauthorized | `ApiException` |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | Payment session has expired. | `ApiException` |


# Get Session by Id

Use this API to read an HPP session content and it's status.
Read more on **[Read HPP session](https://docs.klarna.com/hosted-payment-page/api-documentation/read-session/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def get_session_by_id(self,
                     session_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `session_id` | `str` | Template, Required | HPP session id |

## Response Type

**200**: Session found

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`SessionResponseV1`](../../doc/models/session-response-v1.md).

## Example Usage

```python
session_id = 'session_id8'

result = client_api.get_session_by_id(session_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 401 | Unauthorized | `ApiException` |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | HPP session has expired or could not be found by provided id. | `ApiException` |


# Disable Hpp Session

Use this API to disable an HPP session if payment session had to be cancelled for any reason.
Read more on **[Disable HPP session](https://docs.klarna.com/hosted-payment-page/api-documentation/disable-session/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def disable_hpp_session(self,
                       session_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `session_id` | `str` | Template, Required | HPP session id |

## Response Type

**204**: Session was disabled

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
session_id = 'session_id8'

result = client_api.disable_hpp_session(session_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | HPP session has already been successfully completed. | `ApiException` |
| 401 | Unauthorized | `ApiException` |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | HPP session has expired or could not be found by provided id. | `ApiException` |


# Distribute Hpp Session

Use this API to distribute to the Consumer a link to the Hosted Payment Page either by e-mail or SMS after you have created an HPP session.
Read more on **[Distribute link to the HPP Session to the Consumer](https://docs.klarna.com/hosted-payment-page/api-documentation/distribute-session/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def distribute_hpp_session(self,
                          session_id,
                          body)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `session_id` | `str` | Template, Required | HPP session id |
| `body` | [`DistributionRequestV1`](../../doc/models/distribution-request-v1.md) | Body, Required | Distribution Request parameters |

## Response Type

**201**: Created

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
session_id = 'session_id8'

body = DistributionRequestV1(
    contact_information=DistributionContactV1(
        email='test@example.com',
        phone='07000212345',
        phone_country='SE'
    ),
    method=Method1.SMS,
    template=Template.INSTORE_PURCHASE
)

result = client_api.distribute_hpp_session(
    session_id,
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
| 400 | We were unable to distribute the link with the provided data. Some field constraint was violated. Or session is disabled by merchant. | `ApiException` |
| 401 | Unauthorized | `ApiException` |
| 403 | Forbidden | `ApiException` |
| 404 | HPP session not found or access token not found | `ApiException` |
| 503 | We were unable to distribute the link due to an internal error. Please try again | `ApiException` |


# Create Promise

To create a card promise, provide a purchase currency and the cards to be created. The old promise is automatically invalidated if a new promise is created for an order.

:information_source: **Note** This endpoint does not require authentication.

```python
def create_promise(self,
                  body=None)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`PromiseRequest`](../../doc/models/promise-request.md) | Body, Optional | - |

## Response Type

**201**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PromiseCreatedResponse`](../../doc/models/promise-created-response.md).

## Example Usage

```python
body = PromiseRequest(
    order_id='f3392f8b-6116-4073-ab96-e330819e2c07',
    cards=[
        CardSpecification(
            amount=10000,
            currency='USD',
            reference='yPGw6i4lR0GTcyxGpS3Q6Q==',
            fund_amount=10000
        )
    ]
)

result = client_api.create_promise(
    body=body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiException` |
| 503 | Service unavailable | `ApiException` |


# Read Promise

To get the promise resource, simply provide a promise identifier.

:information_source: **Note** This endpoint does not require authentication.

```python
def read_promise(self,
                promise_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `promise_id` | `str` | Template, Required | - |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PromiseResponse`](../../doc/models/promise-response.md).

## Example Usage

```python
promise_id = 'ee4a8e3a-9dfd-49e0-9ac8-ea2b6c76408c'

result = client_api.read_promise(promise_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Forbidden | `ApiException` |
| 404 | Not found | `ApiException` |


# Settle Promise

To create a settlement resource, provide a completed order identifier and (optionally) a promise identifier.

:information_source: **Note** This endpoint does not require authentication.

```python
def settle_promise(self,
                  body=None)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`SettlementRequest`](../../doc/models/settlement-request.md) | Body, Optional | - |

## Response Type

**201**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`SettlementResponse`](../../doc/models/settlement-response.md).

## Example Usage

```python
body = SettlementRequest(
    order_id='f3392f8b-6116-4073-ab96-e330819e2c07',
    key_id='16e4b85e-899b-4427-a39f-07a496e9515b',
    promise_id='ee4a8e3a-9dfd-49e0-9ac8-ea2b6c76408c'
)

result = client_api.settle_promise(
    body=body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiException` |
| 403 | Forbidden | `ApiException` |
| 503 | Service unavailable | `ApiException` |


# Read Settlement

To get the settlement resource, provide the settlement identifier.

:information_source: **Note** This endpoint does not require authentication.

```python
def read_settlement(self,
                   settlement_id,
                   key_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `settlement_id` | `str` | Template, Required | Unique settlement identifier. |
| `key_id` | `str` | Header, Required | Unique identifier for the public key used for encryption of the card data. |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`SettlementResponse`](../../doc/models/settlement-response.md).

## Example Usage

```python
settlement_id = 'b0ec0bbd-534c-4b1c-b28a-628bf33c3324'

key_id = 'KeyId6'

result = client_api.read_settlement(
    settlement_id,
    key_id
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Forbidden | `ApiException` |
| 404 | Not Found | `ApiException` |


# Read Settlement by Order Id

To get the order's settlement resource, provide the order identifier.

:information_source: **Note** This endpoint does not require authentication.

```python
def read_settlement_by_order_id(self,
                               order_id,
                               key_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Unique identifier for the order associated to the settlement. |
| `key_id` | `str` | Header, Required | Unique identifier for the public key used for encryption of the card data. |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`SettlementResponse`](../../doc/models/settlement-response.md).

## Example Usage

```python
order_id = 'f3392f8b-6116-4073-ab96-e330819e2c07'

key_id = 'KeyId6'

result = client_api.read_settlement_by_order_id(
    order_id,
    key_id
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Forbidden | `ApiException` |
| 404 | Not Found | `ApiException` |


# Postcancelorder

Request cancellation for an order. If the order is already cancelled, a `200` status is returned.

Otherwise, the order will be queued for cancellation with a `202` status. Actual order cancellation will happen asynchronously at a later time. You can call the corresponding GET endpoint to view the status of the request.

This cancellation endpoint is limited to the scope of the Virtual Credit Cards product. Therefore the order provided must have an associated Virtual Card Settlement, otherwise the call will fail.

:information_source: **Note** This endpoint does not require authentication.

```python
def postcancelorder(self,
                   order_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id you wish to cancel. This order must have an associated Virtual Credit Card Settlement. |

## Response Type

**200**: Order is already cancelled.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`CancelOrderRequestStatusCancelled`](../../doc/models/cancel-order-request-status-cancelled.md).

## Example Usage

```python
order_id = 'f3392f8b-6116-4073-ab96-e330819e2c07'

result = client_api.postcancelorder(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request | `ApiException` |
| 403 | You do not have permission to execute this operation. | `ApiException` |
| 404 | Order does not exist or does not have an associated Virtual Credit Card Settlement. | `ApiException` |
| 503 | Service unavailable | `ApiException` |


# Getcancelorder

Get the status of an order cancellation request. The order must have an associated Virtual Credit Card Settlement.

:information_source: **Note** This endpoint does not require authentication.

```python
def getcancelorder(self,
                  order_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `order_id` | `str` | Template, Required | Order id for which to view its cancellation status. This order must have an associated Virtual Credit Card Settlement. |

## Response Type

**200**: Successfully retrieved the status of the cancellation request for this order.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`CancelOrderRequestStatus`](../../doc/models/cancel-order-request-status.md).

## Example Usage

```python
order_id = 'f3392f8b-6116-4073-ab96-e330819e2c07'

result = client_api.getcancelorder(order_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad Request, or the order was not previously requested for cancellation by calling the POST endpoint. | [`CancelOrderRequestStatusNoRequestFoundException`](../../doc/models/cancel-order-request-status-no-request-found-exception.md) |
| 403 | You do not have permission to execute this operation. | `ApiException` |
| 404 | Order does not exist or does not have an associated Virtual Credit Card Settlement. | `ApiException` |
| 503 | Service unavailable | `ApiException` |


# Create Credit Session

Use this API call to create a Klarna Payments session.<br/>When a session is created you will receive the available `payment_method_categories` for the session, a `session_id` and a `client_token`. The `session_id` can be used to read or update the session using the REST API. The `client_token` should be passed to the browser.
Read more on **[Create a new payment session](https://docs.klarna.com/klarna-payments/integrate-with-klarna-payments/step-1-initiate-a-payment/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def create_credit_session(self,
                         body)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`SessionCreate`](../../doc/models/session-create.md) | Body, Required | session_request |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`MerchantSession`](../../doc/models/merchant-session.md).

## Example Usage

```python
body = SessionCreate(
    order_amount=2000,
    order_lines=[
        OrderLine1(
            name='Running shoe',
            quantity=1,
            total_amount=2000,
            unit_price=2500,
            image_url='https://www.exampleobjects.com/logo.png',
            merchant_data='{"customer_account_info":[{"unique_account_identifier":"test@gmail.com","account_registration_date":"2017-02-13T10:49:20Z","account_last_modified":"2019-03-13T11:45:27Z"}]}',
            product_url='https://.../AD6654412.html',
            quantity_unit='pcs',
            reference='AD6654412',
            tax_rate=2000,
            total_discount_amount=500,
            total_tax_amount=333,
            mtype=Type11.PHYSICAL
        )
    ],
    purchase_country='US',
    purchase_currency='USD',
    acquiring_channel=AcquiringChannel.ECOMMERCE,
    locale='en-US',
    merchant_data='{"order_specific":[{"substore":"Women\'s Fashion","product_name":"Women Sweatshirt"}]}',
    merchant_reference_1='ON4711',
    merchant_reference_2='hdt53h-zdgg6-hdaff2',
    order_tax_amount=333,
    intent=Intent.BUY
)

result = client_api.create_credit_session(body)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | We were unable to create a session with the provided data. Some field constraint was violated. | `ApiException` |
| 403 | You were not authorized to execute this operation. | `ApiException` |


# Update Credit Session

Use this API call to update a Klarna Payments session with new details, in case something in the order has changed and the checkout has been reloaded. Including if the consumer adds a new item to the cart or if consumer details are updated.
Read more on **[Update an existing payment session](https://docs.klarna.com/klarna-payments/other-actions/update-the-cart/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def update_credit_session(self,
                         session_id,
                         body)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `session_id` | `str` | Template, Required | session_id |
| `body` | [`Session`](../../doc/models/session.md) | Body, Required | session_request |

## Response Type

**204**: The session was updated successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
session_id = 'session_id8'

body = Session(
    acquiring_channel=AcquiringChannel.ECOMMERCE,
    locale='en-US',
    merchant_data='{"order_specific":[{"substore":"Women\'s Fashion","product_name":"Women Sweatshirt"}]}',
    merchant_reference_1='ON4711',
    merchant_reference_2='hdt53h-zdgg6-hdaff2',
    order_amount=2000,
    order_tax_amount=333,
    purchase_country='US',
    purchase_currency='USD',
    intent=Intent.BUY
)

result = client_api.update_credit_session(
    session_id,
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
| 400 | We were unable to update the session with the provided data. Some field constraint was violated. | `ApiException` |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | The session does not exist. | `ApiException` |


# Read Credit Session

Use this API call to get a Klarna Payments session. You can read the Klarna Payments session at any time after it has been created, to get information about it. This will return all data that has been collected during the session.
Read more on **[Read an existing payment session](https://docs.klarna.com/klarna-payments/other-actions/check-the-details-of-a-payment-session/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def read_credit_session(self,
                       session_id)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `session_id` | `str` | Template, Required | session_id |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`SessionRead`](../../doc/models/session-read.md).

## Example Usage

```python
session_id = 'session_id8'

result = client_api.read_credit_session(session_id)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | The session does not exist. | `ApiException` |


# Cancel Authorization

Use this API call to cancel/release an authorization. If the `authorization_token` received during a Klarna Payments won’t be used to place an order immediately you could release the authorization.
Read more on **[Cancel an existing authorization](https://docs.klarna.com/klarna-payments/other-actions/cancel-an-authorization/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def cancel_authorization(self,
                        authorization_token)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `authorization_token` | `str` | Template, Required | - |

## Response Type

**204**: The authorization was cancelled successfully.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
authorization_token = 'authorizationToken4'

result = client_api.cancel_authorization(authorization_token)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | The authorization does not exist. | `ApiException` |


# Create Order

Use this API call to create a new order. Placing an order towards Klarna means that the Klarna Payments session will be closed and that an order will be created in Klarna's system.<br/>When you have received the `authorization_token` for a successful authorization you can place the order. Among the other order details in this request, you include a URL to the confirmation page for the customer.<br/>When the Order has been successfully placed at Klarna, you need to handle it either through the Merchant Portal or using [Klarna’s Order Management API](#order-management-api).
Read more on **[Create a new order](https://docs.klarna.com/klarna-payments/integrate-with-klarna-payments/step-3-create-an-order/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def create_order(self,
                authorization_token,
                body=None)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `authorization_token` | `str` | Template, Required | - |
| `body` | [`CreateOrderRequest`](../../doc/models/create-order-request.md) | Body, Optional | - |

## Response Type

**200**: Order was successfully created.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`Order`](../../doc/models/order.md).

## Example Usage

```python
authorization_token = 'authorizationToken4'

body = CreateOrderRequest(
    order_amount=2000,
    order_lines=[
        OrderLine1(
            name='Running shoe',
            quantity=1,
            total_amount=2000,
            unit_price=2500,
            image_url='https://www.exampleobjects.com/logo.png',
            merchant_data='{"customer_account_info":[{"unique_account_identifier":"test@gmail.com","account_registration_date":"2017-02-13T10:49:20Z","account_last_modified":"2019-03-13T11:45:27Z"}]}',
            product_url='https://.../AD6654412.html',
            quantity_unit='pcs',
            reference='AD6654412',
            tax_rate=2000,
            total_discount_amount=500,
            total_tax_amount=333,
            mtype=Type11.PHYSICAL
        )
    ],
    purchase_country='US',
    purchase_currency='USD',
    auto_capture=False,
    locale='en-US',
    merchant_data='{"order_specific":[{"substore":"Women\'s Fashion","product_name":"Women Sweatshirt"}]}',
    merchant_reference_1='ON4711',
    merchant_reference_2='hdt53h-zdgg6-hdaff2',
    order_tax_amount=333
)

result = client_api.create_order(
    authorization_token,
    body=body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | We were unable to create an order with the provided data. Some field constraint was violated. | `ApiException` |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | The authorization does not exist. | `ApiException` |
| 409 | The data in the request does not match the session for the authorization. | `ApiException` |


# Purchase Token

Use this API call to create a Klarna Customer Token.<br/>After having obtained an `authorization_token` for a successful authorization, this can be used to create a purchase token instead of placing the order. Creating a Klarna Customer Token results in Klarna storing customer and payment method details.
Read more on **[Generate a customer token](https://docs.klarna.com/klarna-payments/in-depth-knowledge/customer-token/)**.

:information_source: **Note** This endpoint does not require authentication.

```python
def purchase_token(self,
                  authorization_token,
                  body=None)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `authorization_token` | `str` | Template, Required | - |
| `body` | [`CustomerTokenCreationRequest`](../../doc/models/customer-token-creation-request.md) | Body, Optional | - |

## Response Type

**200**: Token was successfully created.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`CustomerTokenCreationResponse`](../../doc/models/customer-token-creation-response.md).

## Example Usage

```python
authorization_token = 'authorizationToken4'

body = CustomerTokenCreationRequest(
    description='description4',
    locale='en-US',
    purchase_country='US',
    purchase_currency='USD'
)

result = client_api.purchase_token(
    authorization_token,
    body=body
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | We were unable to create a customer token with the provided data. Some field constraint was violated. | [`CancelNotAllowedErrorMessageException`](../../doc/models/cancel-not-allowed-error-message-exception.md) |
| 403 | You were not authorized to execute this operation. | `ApiException` |
| 404 | The authorization does not exist. | `ApiException` |
| 409 | The data in the request does not match the session for the authorization. | `ApiException` |


# Get Payout Summary

Returns a summary of payouts for each currency code in a date range.

:information_source: **Note** This endpoint does not require authentication.

```python
def get_payout_summary(self,
                      start_date,
                      end_date,
                      currency_code=None)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `start_date` | `datetime` | Query, Required | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. For example 2020-01-23 -> 2020-01-23T00:00:00Z. For this reason we recommend too use the full datetime like 2020-01-23T00:00:00Z. |
| `end_date` | `datetime` | Query, Required | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. This might lead to unwanted side effects like when the start date and end date might be the same because it would request payouts between 2020-01-23T00:00:00Z and 2020-01-23T00:00:00Z. Instead we advise to use a full datetime like 2020-01-23T23:59:59Z. |
| `currency_code` | `str` | Query, Optional | An optional currency code to filter the result for different currencies. If not provided the result returned in the response might include multiple results grouped by the currency. The currency should be provided by an ISO 4217 Currency Code like USD, EUR, AUD or GBP. |

## Response Type

**200**: Payout summaries

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`List[PayoutSummary]`](../../doc/models/payout-summary.md).

## Example Usage

```python
start_date = dateutil.parser.parse('2016-03-13T12:52:32.123Z')

end_date = dateutil.parser.parse('2016-03-13T12:52:32.123Z')

result = client_api.get_payout_summary(
    start_date,
    end_date
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Payout

Returns a specific payout based on a given payment reference.

:information_source: **Note** This endpoint does not require authentication.

```python
def get_payout(self,
              payment_reference)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_reference` | `str` | Template, Required | The reference id of the payout. Normally this reference can be found on your payment slip statement of your bank. |

## Response Type

**200**: A payout

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`Payout`](../../doc/models/payout.md).

## Example Usage

```python
payment_reference = 'payment_reference8'

result = client_api.get_payout(payment_reference)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |
| 404 | Not found | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Payouts

Returns a collection of payouts.

:information_source: **Note** This endpoint does not require authentication.

```python
def get_payouts(self,
               start_date=None,
               end_date=None,
               currency_code=None,
               size=20,
               offset=0)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `start_date` | `datetime` | Query, Optional | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. For example 2020-01-23 -> 2020-01-23T00:00:00Z. For this reason we recommend too use the full datetime like 2020-01-23T00:00:00Z. |
| `end_date` | `datetime` | Query, Optional | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. This might lead to unwanted side effects like when the start date and end date might be the same because it would request payouts between 2020-01-23T00:00:00Z and 2020-01-23T00:00:00Z. Instead we advise to use a full date time like 2020-01-23T23:59:59Z. |
| `currency_code` | `str` | Query, Optional | An optional currency code to filter the result for different currencies. If not provided the result returned in the response might include multiple results grouped by the currency. The currency should be provided by an ISO 4217 Currency Code like USD, EUR, AUD or GBP. |
| `size` | `int` | Query, Optional | How many elements to include in the result. If no value for size is provided, a default of 20 will be used. A maximum of 500 can be set<br><br>**Default**: `20`<br><br>**Constraints**: `<= 500` |
| `offset` | `int` | Query, Optional | The current offset. Describes "where" in a collection the current starts.<br><br>**Default**: `0` |

## Response Type

**200**: A collection of payouts

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`PayoutCollection`](../../doc/models/payout-collection.md).

## Example Usage

```python
size = 20

offset = 0

result = client_api.get_payouts(
    size=size,
    offset=offset
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Payout Report with Transactions

More information about this CSV format is available at:
https://docs.klarna.com/settlement-reports

:information_source: **Note** This endpoint does not require authentication.

```python
def get_payout_report_with_transactions(self,
                                       payment_reference)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_reference` | `str` | Query, Required | The reference id of the payout |

## Response Type

**200**: A payout

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
payment_reference = 'payment_reference8'

result = client_api.get_payout_report_with_transactions(payment_reference)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |
| 404 | Not found | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Payout

A single settlement summed up in pdf format

:information_source: **Note** This endpoint does not require authentication.

```python
def payout(self,
          payment_reference)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_reference` | `str` | Query, Required | The reference id of the payout |

## Response Type

**200**: A payout

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
payment_reference = 'payment_reference8'

result = client_api.payout(payment_reference)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | `ApiException` |
| 404 | Not found | `ApiException` |


# Get Transactions

Returns a collection of transactions.

:information_source: **Note** This endpoint does not require authentication.

```python
def get_transactions(self,
                    payment_reference=None,
                    order_id=None,
                    size=20,
                    offset=0)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `payment_reference` | `str` | Query, Optional | The reference id of the payout |
| `order_id` | `str` | Query, Optional | The Klarna assigned order id reference |
| `size` | `int` | Query, Optional | How many elements to include in the result. If no value for size is provided, a default of 20 will be used. A maximum of 500 can be set.<br><br>**Default**: `20`<br><br>**Constraints**: `<= 500` |
| `offset` | `int` | Query, Optional | The current offset. Describes "where" in a collection the current starts.<br><br>**Default**: `0` |

## Response Type

**200**: A collection of payouts

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `body` property of this instance returns the response data which is of type [`TransactionCollection`](../../doc/models/transaction-collection.md).

## Example Usage

```python
size = 20

offset = 0

result = client_api.get_transactions(
    size=size,
    offset=offset
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Payouts Summary Report with Transactions

More information about this CSV format is available at:
https://docs.klarna.com/settlement-reports

:information_source: **Note** This endpoint does not require authentication.

```python
def get_payouts_summary_report_with_transactions(self,
                                                start_date,
                                                end_date)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `start_date` | `datetime` | Query, Required | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. For example 2020-01-23 -> 2020-01-23T00:00:00Z. For this reason we recommend too use the full datetime like 2020-01-23T00:00:00Z. |
| `end_date` | `datetime` | Query, Required | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. This might lead to unwanted side effects like when the start date and end date might be the same because it would request payouts between 2020-01-23T00:00:00Z and 2020-01-23T00:00:00Z. Instead we advise to use a full date time like 2020-01-23T23:59:59Z. |

## Response Type

**200**: A summary of payouts

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
start_date = dateutil.parser.parse('2016-03-13T12:52:32.123Z')

end_date = dateutil.parser.parse('2016-03-13T12:52:32.123Z')

result = client_api.get_payouts_summary_report_with_transactions(
    start_date,
    end_date
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Payouts Summary

Returns a summary for all payouts between the given dates

:information_source: **Note** This endpoint does not require authentication.

```python
def payouts_summary(self,
                   start_date,
                   end_date)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `start_date` | `datetime` | Query, Required | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. For example 2020-01-23 -> 2020-01-23T00:00:00Z. For this reason we recommend too use the full datetime like 2020-01-23T00:00:00Z. |
| `end_date` | `datetime` | Query, Required | ISO 8601 date time format. This is a filter for the payout date. If no time is given then it defaults to the start of the day, ie 00:00:00. This might lead to unwanted side effects like when the start date and end date might be the same because it would request payouts between 2020-01-23T00:00:00Z and 2020-01-23T00:00:00Z. Instead we advise to use a full date time like 2020-01-23T23:59:59Z. |

## Response Type

**200**: A summary of payouts

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```python
start_date = dateutil.parser.parse('2016-03-13T12:52:32.123Z')

end_date = dateutil.parser.parse('2016-03-13T12:52:32.123Z')

result = client_api.payouts_summary(
    start_date,
    end_date
)

if result.is_success():
    print(result.body)
elif result.is_error():
    print(result.errors)
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Bad request | `ApiException` |

