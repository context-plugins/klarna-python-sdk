
# Getting Started with klarna

## Introduction

The Disputes API offers Klarna partners and merchants an easy way to handle customer disputes.

Use the available endpoints to:

* Get a list of disputes, filtered by various parameters.
* Get a full, detailed version of a dispute, including all the associated requests and responses.
* Respond to a dispute request.
* Download/upload a file attachment linked to a specific request response.
* Accept loss for a dispute.
* Represent (respond to) a dispute.
* Appeal a dispute decision.

Klarna merchants consuming Disputes API are authenticated via the OAuth 2.0 protocol or API keys.

Before you get started, please make sure you understand the disputes process.

### FAQ

* Why is the API returning 403?
  * Please make sure your credentials and the endpoint you're calling are correct. Klarna APIs may also respond with a 403 for invalid paths.
* GET v4/disputes returns an empty list, why?
  * Are you sure there are disputes to list?
  * Since you got through to the endpoint your client credentials are valid. Some partners or merchants may have been onboarded to the api incorrectly.
* Why am I getting an invalid date format when responding to a dispute?
  * Only the following ISO 8601 format is currently supported: `YYYY-MM-DDTHH:mm:ss.sssZ`. Please note it includes ms., Hosted Payment Page (HPP) API is a service that lets you integrate Klarna Payments without the need of hosting the web page that manages the client side of Klarna Payments.
    A complete HPP payment session will involve three of Klarna services:
* [`Klarna Payments API`](https://docs.klarna.com/api/payments/) to start a payment session.
* [`Hosted Payment Page API`](https://docs.klarna.com/api/hpp-merchant) to distribute a payment session.
* [`Order Management API`](https://docs.klarna.com/api/ordermanagement) to capture payment or refund consumer.

Read more on [Hosted payment page](https://docs.klarna.com/hosted-payment-page/)., The Merchant Card Service (MCS) API is used to settle orders with virtual credit cards.

Read more on [Merchant card service](https://docs.klarna.com/merchant-card-service/)., The Order Management API is used for handling an order after the customer has completed the purchase. It is used for all actions you need to manage your orders. Examples being: updating, capturing, reading and refunding an order.

Read more on the [Order management](https://docs.klarna.com/order-management/) process., The payments API is used to create a session to offer Klarna's payment methods as part of your checkout. As soon as the purchase is completed the order should be read and handled using the [`Order Management API`](https://docs.klarna.com/api/ordermanagement).

**Note:** Examples provided in this section includes full payloads, including all supported fields, required and optionals. In order to implement a best in class request we recommend you don't include customer details when initiating a payment session. Refer to [Initiate a payment](https://docs.klarna.com/klarna-payments/integrate-with-klarna-payments/step-1-initiate-a-payment/) section for further details.

Read more on [Klarna payments](https://docs.klarna.com/klarna-payments/)., The Settlements API helps you with the reconciliation of payments, made by Klarna to your bank account. Every payment has a unique payment_reference that can be found in the settlement reports and on your bank statement.

Read more on [Settlement reports](https://docs.klarna.com/settlement-reports/).

## Building

You must have Python `3.7+` installed on your system to install and run this SDK. This SDK package depends on other Python packages like pytest, etc. These dependencies are defined in the `requirements.txt` file that comes with the SDK. To resolve these dependencies, you can use the PIP Dependency manager. Install it by following steps at [https://pip.pypa.io/en/stable/installing/](https://pip.pypa.io/en/stable/installing/).

Python and PIP executables should be defined in your PATH. Open command prompt and type `pip --version`. This should display the version of the PIP Dependency Manager installed if your installation was successful and the paths are properly defined.

* Using command line, navigate to the directory containing the generated files (including `requirements.txt`) for the SDK.
* Run the command `pip install -r requirements.txt`. This should install all the required dependencies.

![Building SDK - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&step=installDependencies)

## Installation

The following section explains how to use the klarna library in a new project.

### 1. Open Project in an IDE

Open up a Python IDE like PyCharm. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.

![Open project in PyCharm - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&step=pyCharm)

Click on `Open` in PyCharm to browse to your generated SDK directory and then click `OK`.

![Open project in PyCharm - Step 2](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&step=openProject0)

The project files will be displayed in the side bar as follows:

![Open project in PyCharm - Step 3](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&projectName=klarna&step=openProject1)

### 2. Add a new Test Project

Create a new directory by right clicking on the solution name as shown below:

![Add a new project in PyCharm - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&projectName=klarna&step=createDirectory)

Name the directory as "test".

![Add a new project in PyCharm - Step 2](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&step=nameDirectory)

Add a python file to this project.

![Add a new project in PyCharm - Step 3](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&projectName=klarna&step=createFile)

Name it "testSDK".

![Add a new project in PyCharm - Step 4](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&projectName=klarna&step=nameFile)

In your python file you will be required to import the generated python library using the following code lines

```python
from klarna.klarna_client import KlarnaClient
```

![Add a new project in PyCharm - Step 5](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&projectName=klarna&libraryName=klarna.klarna_client&className=KlarnaClient&step=projectFiles)

After this you can write code to instantiate an API client object, get a controller object and  make API calls. Sample code is given in the subsequent sections.

### 3. Run the Test Project

To run the file within your test project, right click on your Python file inside your Test project and click on `Run`

![Run Test Project - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Klarna-Python&projectName=klarna&libraryName=klarna.klarna_client&className=KlarnaClient&step=runProject)

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| http_client_instance | `Union[Session, HttpClientProvider]` | The Http Client passed from the sdk user for making requests |
| override_http_client_configuration | `bool` | The value which determines to override properties of the passed Http Client from the sdk user |
| http_call_back | `HttpCallBack` | The callback value that is invoked before and after an HTTP call is made to an endpoint |
| timeout | `float` | The value to use for connection timeout. <br> **Default: 30** |
| max_retries | `int` | The number of times to retry an endpoint call if it fails. <br> **Default: 0** |
| backoff_factor | `float` | A backoff factor to apply between attempts after the second try. <br> **Default: 2** |
| retry_statuses | `Array of int` | The http statuses on which retry is to be done. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524, 408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| retry_methods | `Array of string` | The http methods on which retry is to be done. <br> **Default: ["GET", "PUT", "GET", "PUT"]** |
| proxy_settings | [`ProxySettings`](doc/proxy-settings.md) | Optional proxy configuration to route HTTP requests through a proxy server. |
| logging_configuration | [`LoggingConfiguration`](doc/logging-configuration.md) | The SDK logging configuration for API calls |
| klarna_api_key_credentials | [`KlarnaApiKeyCredentials`](doc/auth/custom-header-signature.md) | The credential object for Custom Header Signature |
| basic_auth_credentials | [`BasicAuthCredentials`](doc/auth/basic-authentication.md) | The credential object for Basic Authentication |

The API client can be initialized as follows:

### Code-Based Client Initialization

```python
import logging

from klarna.configuration import Environment
from klarna.http.auth.basic_auth import BasicAuthCredentials
from klarna.http.auth.klarna_api_key import KlarnaApiKeyCredentials
from klarna.klarna_client import KlarnaClient
from klarna.logging.configuration.api_logging_configuration import LoggingConfiguration
from klarna.logging.configuration.api_logging_configuration import RequestLoggingConfiguration
from klarna.logging.configuration.api_logging_configuration import ResponseLoggingConfiguration

client = KlarnaClient(
    klarna_api_key_credentials=KlarnaApiKeyCredentials(
        authorization='Authorization'
    ),
    basic_auth_credentials=BasicAuthCredentials(
        username='Username',
        password='Password'
    ),
    environment=Environment.PRODUCTION,
    logging_configuration=LoggingConfiguration(
        log_level=logging.INFO,
        request_logging_config=RequestLoggingConfiguration(
            log_body=True
        ),
        response_logging_config=ResponseLoggingConfiguration(
            log_headers=True
        )
    )
)
```

### Environment-Based Client Initialization

```python
from klarna.klarna_client import KlarnaClient

# Specify the path to your .env file if it’s located outside the project’s root directory.
client = KlarnaClient.from_environment(dotenv_path='/path/to/.env')
```

See the [Environment-Based Client Initialization](doc/environment-based-client-initialization.md) section for details.

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| PRODUCTION | **Default** EU Production API host |
| ENVIRONMENT2 | EU Playground API host |

## Authorization

This API uses the following authentication schemes.

* [`klarna_api_key (Custom Header Signature)`](doc/auth/custom-header-signature.md)
* [`basicAuth (Basic Authentication)`](doc/auth/basic-authentication.md)

## List of APIs

* [Payment Dispute API](doc/controllers/payment-dispute-api.md)
* [API](doc/controllers/api.md)
* [Orders](doc/controllers/orders.md)
* [Captures](doc/controllers/captures.md)
* [Refunds](doc/controllers/refunds.md)

## SDK Infrastructure

### Configuration

* [ProxySettings](doc/proxy-settings.md)
* [Environment-Based Client Initialization](doc/environment-based-client-initialization.md)
* [AbstractLogger](doc/abstract-logger.md)
* [LoggingConfiguration](doc/logging-configuration.md)
* [RequestLoggingConfiguration](doc/request-logging-configuration.md)
* [ResponseLoggingConfiguration](doc/response-logging-configuration.md)

### HTTP

* [HttpResponse](doc/http-response.md)
* [HttpRequest](doc/http-request.md)
* [Request](doc/request.md)

### Utilities

* [ApiResponse](doc/api-response.md)
* [ApiHelper](doc/api-helper.md)
* [HttpDateTime](doc/http-date-time.md)
* [RFC3339DateTime](doc/rfc3339-date-time.md)
* [UnixDateTime](doc/unix-date-time.md)

