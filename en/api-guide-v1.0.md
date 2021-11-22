
## Security > Secure Key Manager > API v1.0 Guide

Secure Key Manager provides various APIs to access user data. Clients must be authenticated via key store to get access to data stored in Secure Kay Manager.

[List of APIs]

| Method | URI | Description |
|---|---|---|
| GET | /keymanager/v1.0/appkey/{appkey}/confirm | Provide information of the client that called API. |
| GET | /keymanager/v1.0/appkey/{appkey}/secrets/{keyid} | Query confidential data stored in Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/encrypt | Encrypt data with the symmetric key stored in Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/decrypt | Decrypt data with the symmetric key stored in Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/create-local-key | Create AES-256 symmetric keys that can be used by a client for data encryption/decryption in local environment. |
| GET | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/symmetric-key | Query the symmetric key stored in Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/sign | Sign data with the asymmetric key stored in Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/verify | Verify data and signature with the asymmetric key stored in Secure Key Manager. |

[HTTP Header of API Request]

To use MAC address authentication of Secure Key Manager, you must make a request by setting the client's MAC address in the HTTP header.
```
X-TOAST-CLIENT-MAC-ADDR: {MAC Address}
```

[Path Variables of API Request]

| Name | Type | Description |
|---|---|---|
| appkey | String | Appkey of the NHN Cloud project where the data in need is stored |
| keyid | String | Identifier of data in need |

[Common Data Header of API Response]
```
{
    "header": {
        "resultCode": 0,
        "resultMessage": "success",
        "isSuccessful": true
    },
    "body": {
        ...
    }
}
```
| Name | Type | Description |
|---|---|---|
| resultCode | Number | Result code value of API call |
| resultMessage | String | Result message of API call |
| isSuccessful | Boolean | Whether API call is successful or not |

## Query Client Information
This API is used to query information of the client that called API.
```
GET https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/confirm
```
[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "clientIp": "0.0.0.0",
        "clientMacHeader": "00:00:00:00:00:00",
        "clientSentCerfificate": false
    }
}
```
| Name | Type | Description |
|---|---|---|
| clientIp | String | IP address of the client that called API |
| clientMacHeader | String |Header value of MAC address of the client that called API |
| clientSentCertificate | Boolean | Whether the client that called API is using certificate or not |

## Confidential Data

### Query Confidential Data
This API is used to query confidential data stored in Secure Key Manager.
```
GET https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/secrets/{keyid}
```

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "secret": "data"
    }
}
```
| Name | Type | Description |
|---|---|---|
| secret | String | Query result of confidential data |

## Symmetric Key

### Encrypt Symmetric Keys
This API is used to encrypt data with the symmetric key created in Secure Key Manager. A user can pass 32KB or smaller text data, and the data can be encrypted with the symmetric key stored in Secure Key Manager.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/encrypt
```

[Request Body]

```
{
    "plaintext": "data"
}
```
| Name | Type | Description |
|---|---|---|
| plaintext | String | Data to be encrypted with the symmetric key |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "ciphertext": "AAAAABzGwQniNneKXmcOLhWnxEqC1rNY+UdVb3lyeX/4wSrP",
        "keyVersion": 1
    }
}
```
| Name | Type | Description |
|---|---|---|
| ciphertext | String | Result of data encryption with the symmetric key |
| keyVersion | Number | Version of the symmetric key used for processing the API request |

### Decrypt Symmetric Keys
This API is used to decrypt data with the symmetric key created in Secure Key Manager. A use can pass encrypted text, and the text data can be decrypted with the symmetric key stored in Secure Key Manager.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/decrypt
```

[Request Body]
```
{
    "ciphertext": "AAAAABzGwQniNneKXmcOLhWnxEqC1rNY+UdVb3lyeX/4wSrP"
}
```
| Name | Type | Description |
|---|---|---|
| ciphertext | String | Data to be decrypted with the symmetric key |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "plaintext": "data",
        "keyVersion": 1
    }
}
```
| Name | Type | Description |
|---|---|---|
| plaintext | String | Result of data decryption with the symmetric key |
| keyVersion | Number | Version of the symmetric key used for processing the API request |

### Generate Local Symmetric Keys Encrypted with the Symmetric Key
This API is used to create AES-256 symmetric keys that a client can use in local environment. localKeyPlaintext is a base64-encoded form of the generated symmetric key, and it is readily available after base64 decoding. localKeyCiphertext is a base64-encoded form of the generated symmetric key encrypted with the symmetric key stored in Secure Key Manager, and it is used to store data in a storage. The symmetric key stored in storage can be used after being decrypted by using the decryption API.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/create-local-key
```

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "localKeyPlaintext": "srV7MWkYIfYBknkASzwSEK1Z1y9Nx0f/RMZ3MSVIjm8=",
        "localKeyCiphertext": "v1s1WkiIj3KR+AafnupNv9xcX/JhL4GUzUr8mzLRpjbGuoAwU/GgboM/6QdRRY24",
        "keyVersion": 1
    }
}
```
| Name | Type | Description |
|---|---|---|
| localKeyPlaintext | String | Base64-encoded AES-256 symmetric key |
| localKeyCiphertext | String | Base64-encoded AES-256 symmetric key encrypted with the symmetric key stored in Secure Key Manager |
| keyVersion | Number | Version of the symmetric key used for processing the API request |

### Query the Symmetric Key

You can query the symmetric key (AES-256) stored in Secure Key Manager.
```
GET https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/symmetric-key
```

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "symmetricKey": "0x00, 0x20, 0x00, 0x41, 0x00, 0x20, 0x00, 0x73, 0x00, 0x69, 0x00, 0x6d, 0x00, 0x70, 0x00, 0x6c, 0x00, 0x65, 0x00, 0x20, 0x00, 0x4a, 0x00, 0x61, 0x00, 0x76, 0x00, 0x61, 0x00, 0x2e, 0x00, 0x20"
    }
}
```
| Name | Type | Description |
|---|---|---|
|symmetricKey | String | Symmetric key data (Hex string form) |

## Asymmetric Key

### Sign with the Asymmetric Key
This API is used to sign data with the asymmetric key created in Secure Key Manager. Users can pass 245 Byte or smaller text data, and the data is signed with the asymmetric key stored in Secure Key Manager.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/sign
```

[Request Body]
```
{
    "plaintext": "data"
}
```
| Name | Type | Description |
|---|---|---|
| plaintext | String | Data to sign with the asymmetric key |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "signature": "AAAAAGI9zf831DX...",
        "keyVersion": 1
    }
}
```
| Name | Type | Description |
|---|---|---|
| signature | String | Signature value of signing the data with the asymmetric key |
| keyVersion | Number | Version of the asymmetric key used for processing the API request |

### Verify Data with the Asymmetric Key
This API is used to verify data with the asymmetric key created in Secure Key Manager. User can pass data and signature value, and use asymmetric keys stored in Secure Key Manager to verify that data has not been forged.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/verify
```

[Request Body]

```
{
    "plaintext": "data",
    "signature": "AAAAAGI9zf831DX..."
}
```
| Name | Type | Description |
|---|---|---|
| plaintext | String | Data to be verified with the asymmetric key |
| signature | String | Signature value of signing the data with the asymmetric key |

[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "result": true,
        "keyVersion": 1
    }
}
```
| Name | Type | Description |
|---|---|---|
| result | Boolean | Result of verifying data and signature value with the asymmetric key |
| keyVersion | Number | Version of the asymmetric key used for processing the API request |
