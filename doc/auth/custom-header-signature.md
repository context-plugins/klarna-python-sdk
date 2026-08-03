
# Custom Header Signature



Documentation for accessing and setting credentials for klarna_api_key.

## Auth Credentials

| Name | Type | Description | Getter |
|  --- | --- | --- | --- |
| Authorization | `str` | Use the Klarna API key as HTTP Basic Authentication credentials | `authorization` |



**Note:** Auth credentials can be set using `KlarnaApiKeyCredentials` object, passed in as named parameter `klarna_api_key_credentials` in the client initialization.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```python
from klarna.http.auth.klarna_api_key import KlarnaApiKeyCredentials
from klarna.klarna_client import KlarnaClient

client = KlarnaClient(
    klarna_api_key_credentials=KlarnaApiKeyCredentials(
        authorization='Authorization'
    )
)
```


