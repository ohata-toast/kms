
## Security > Secure Key Manager > API v1.0 Guide

Secure Key Manager provides a variety of APIs to access user data. Clients must be authenticated via key store to get access to data saved at Secure Kay Manager.

[List of APIs]

| Method | URI | Description |
|---|---|---|
| GET | /keymanager/v1.0/appkey/{appkey}/confirm | Provide information of the client who called API. |
| GET | /keymanager/v1.0/appkey/{appkey}/secrets/{keyid} | Query confidential data saved at Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/encrypt | Encrypt data with symmetric keys saved at Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/decrypt | Decrypt data with symmetric keys saved at Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/create-local-key | Create AES-256 symmetric keys available for data encryption/decryption under a local environment. |
| POST | /keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/sign | Sign data with asymmetric keys saved at Secure Key Manager. |
| POST | /keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/verify | Verify data and signature with asymmetric keys saved at Secure Key Manager. |

[HTTP Header of API Request]

To authenticate MAC address of Secure Key Manager, it is required to set client's MAC address at the HTTP header before requested.
```
X-TOAST-CLIENT-MAC-ADDR: {MAC Address}
```

[Path Variables of API Request]

| Value | Type | Description |
|---|---|---|
| appkey | String | Appkey of the TOAST project to which data in need is saved |
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
| Value | Type | Description |
|---|---|---|
| resultCode | Number | Result code value of API call |
| resultMessage | String | Result message of API call |
| isSuccessful | Boolean | If API call is successful or not |

### Query Client Information 
You may query information of the client who called API.
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
| Value | Type | Description |
|---|---|---|
| clientIp | String | IP address of the client who called API |
| clientMacHeader | String | Header value of MAC address of the client who called API |
| clientSentCertificate | Boolean | If the client who called API is using certificate or not |

### Query Confidential Data
You may query confidential data saved at Secure Key Manager.
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
| Value | Type | Description |
|---|---|---|
| secret | String | Query result of confidential data |

### Encrypt Symmetric Keys
You may encrypt data with symmetric keys generated at Secure Key Manager. 32KB or smaller text data can be delivered to be encrypted with symmetric keys saved at Secure Key Manager.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/encrypt
```

[Request Body]

```
{
    "plaintext": "data"
}
```
| Value | Type | Description |
|---|---|---|
| plaintext | String | Data to be encrypted with symmetric keys |

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
| Value | Type | Description |
|---|---|---|
| ciphertext | String | Result of data encryption with symmetric keys |
| keyVersion | Number | Symmetric key version applied to process API requests |

## Decrypt Symmetric Keys
You may decrypt data with symmetric keys generated at Secure Key Manager. Encrypted text can be delivered and decrypted with symmetric keys saved at Secure Key Manager.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/decrypt
```

[Request Body]
```
{
    "ciphertext": "AAAAABzGwQniNneKXmcOLhWnxEqC1rNY+UdVb3lyeX/4wSrP"
}
```
| Value | Type | Description |
|---|---|---|
| ciphertext | String | Data to be decrypted with asymmetric keys |

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
| Value | Type | Description |
|---|---|---|
| plaintext | String | Decryption result of data with symmetric keys |
| keyVersion | Number | Symmetric key version available to process API requests |

### Generate Local Symmetric Keys Encrypted with Symmetric Keys
Client may create AES-256 symmetric keys for a local environment. localKeyPlaintext refers to a symmetric key which is encoded in base64, and it is readily available after being decoded in base64. localKeyCiphertext refers to a symmetric key saved at Secure Key Manager, which is encrypted and then encoded in base64, and it is used to save at a storage. The symmetric key saved at storage can be decrypted by using Decrypt API to be enabled.
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
| Value | Type | Description |
|---|---|---|
| localKeyPlaintext | String | Symmetric key to AES-256 which is encoded in Base64 |
| localKeyCiphertext | String | Symmetric key to AES-256 saved at Secure Key Manager which is encrypted and then encoded in base64 |
| keyVersion | Number | Symmetric key version applied to process API request |

### Sign with Asymmetric Keys
The asymmetric key created at Secure Key Manager is used to sign data. Users can deliver 4KB or smaller text data and sign with asymmetric key saved at Secure Key Manager.
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/sign
```

[Request Body]
```
{
    "plaintext": "data"
}
```
| Value | Type | Description |
|---|---|---|
| plaintext | String | Data to sign with asymmetric keys |

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
| Value | Type | Description |
|---|---|---|
| signature | String | Signature signed for data with asymmetric key |
| keyVersion | Number | Asymmetric key version applied to process API request |

### Verify Data with Asymmetric Keys
You may verify data with asymmetric keys created at Secure Key Manager. By delivering data and signature value, user can use asymmetric keys saved at Secure Key Manager to verify that data has not been falsified.
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
| Value | Type | Description |
|---|---|---|
| plaintext | String | Data to be verified with asymmetric key |
| signature | String | Signature signed for data with asymmetric key |

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
| Value | Type | Description |
|---|---|---|
| result | Boolean | Verification result of data and signature by using asymmetric keys |
| keyVersion | Number | Asymmetric key version applied to process API request |
