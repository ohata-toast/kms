
## Security > Secure Key Manager > API v1.0ガイド

Secure Key Managerは、ユーザーデータにアクセスできる多様なAPIを提供します。クライアントは鍵の保存場所に設定した認証をパスした後に、Secure Key Managerに保存したデータを使用できます。

[APIリスト]

| Method | URI | 説明 |
|---|---|---|
| GET | /keymanager/v1.0/appkey/{appkey}/confirm | APIを呼び出したクライアント情報を提供します。|
| GET | /keymanager/v1.0/appkey/{appkey}/secrets/{keyid} | Secure Key Managerに保存した機密データを照会します。|
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/encrypt | Secure Key Managerに保存した対称鍵でデータを暗号化します。|
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/decrypt | Secure Key Managerに保存した対称鍵でデータを復号します。|
| POST | /keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/create-local-key | クライアントがローカル環境でデータの暗号化/復号に使用できるAES-256対称鍵を作成します。|
| POST | /keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/sign | Secure Key Managerに保存した非対称鍵でデータを署名します。|
| POST | /keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/verify | Secure Key Managerに保存した非対称鍵でデータと署名を検証します。|

[APIリクエストのHTTPヘッダ]

Secure Key ManagerのMACアドレス認証を使用するには、HTTPヘッダにクライアントMACアドレスを設定してリクエストする必要があります。
```
X-TOAST-CLIENT-MAC-ADDR: {MACアドレス}
```

[APIリクエストのパス変数]

| 値 | タイプ | 説明 |
|---|---|---|
| appkey | String | 使用したいデータを保存しているTOASTプロジェクトのアプリケーションキー |
| keyid | String | 使用したいデータの識別子 |

[APIレスポンスのデータ共通ヘッダ]
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
| 値 | タイプ | 説明 |
|---|---|---|
| resultCode | Number | API呼び出し結果コード値 |
| resultMessage | String | API呼び出し結果メッセージ |
| isSuccessful | Boolean | API呼び出し成否 |

### クライアント情報照会
APIを呼び出したクライアント情報を照会する時に使用します。
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
| 値 | タイプ | 説明 |
|---|---|---|
| clientIp | String | APIを呼び出したクライアントのIPアドレス |
| clientMacHeader | String |APIを呼び出したクライアントのMACアドレスヘッダ値 |
| clientSentCertificate | Boolean | APIを呼び出したクライアントが証明書を使用しているかどうか |

### 機密データ照会
Secure Key Managerに保存した機密データを照会する時に使用します。
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
| 値 | タイプ | 説明 |
|---|---|---|
| secret | String | 機密データ照会結果 |

### 対称鍵暗号化
Secure Key Managerに作成した対称鍵でデータを暗号化する時に使用します。ユーザーは32KB以下のテキストデータを転送して、Secure Key Managerに保存した対称鍵で暗号化できます。
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/encrypt
```

[Request Body]

```
{
    "plaintext": "data"
}
```
| 値 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 対称鍵で暗号化するデータ |

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
| 値 | タイプ | 説明 |
|---|---|---|
| ciphertext | String | 対称鍵でデータを暗号化した結果 |
| keyVersion | Number | APIリクエスト処理に使用した対称鍵バージョン |

## 対称鍵復号
Secure Key Managerに作成した対称鍵でデータを復号する時に使用します。ユーザーは暗号化されたテキストを転送して、Secure Key Managerに保存した対称鍵で復号できます。
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/symmetric-keys/{keyid}/decrypt
```

[Request Body]
```
{
    "ciphertext": "AAAAABzGwQniNneKXmcOLhWnxEqC1rNY+UdVb3lyeX/4wSrP"
}
```
| 値 | タイプ | 説明 |
|---|---|---|
| ciphertext | String | 対称鍵で復号するデータ |

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
| 値 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 対称鍵でデータを復号した結果 |
| keyVersion | Number | APIリクエスト処理に使用した対称鍵バージョン |

### 対称鍵で暗号化したローカル対称鍵作成
クライアントがローカル環境で使用できるAES-256対称鍵を作成する時に使用します。localKeyPlaintextは、作成した対称鍵をBase64エンコードした形式で、Base64エンコード後すぐに使用できます。localKeyCiphertextは、作成した対称鍵をSecure Key Managerに保存した対称鍵で暗号化した後にBase64エンコードした形式で、ストレージに保存する時に使用します。ストレージに保存した対称鍵は、復号APIを使用して復号した後に使用できます。
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
| 値 | タイプ | 説明 |
|---|---|---|
| localKeyPlaintext | String | Base64エンコードしたAES-256対称鍵 |
| localKeyCiphertext | String | Secure Key Managerに保存した対称鍵で暗号化した後、Base64エンコードしたAES-256対称鍵 |
| keyVersion | Number | APIリクエスト処理に使用した対称鍵バージョン |

### 非対称鍵で署名
Secure Key Managerに作成した非対称鍵で、データを署名する時に使用します。ユーザーは4KB以下のテキストデータを転送して、Secure Key Managerに保存した非対称鍵で署名できます。
```
POST https://api-keymanager.cloud.toast.com/keymanager/v1.0/appkey/{appkey}/asymmetric-keys/{keyid}/sign
```

[Request Body]
```
{
    "plaintext": "data"
}
```
| 値 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 非対称鍵で署名するデータ |

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
| 値 | タイプ | 説明 |
|---|---|---|
| signature | String | 非対称鍵でデータを署名した署名値 |
| keyVersion | Number | APIリクエスト処理に使用した非対称鍵バージョン |

### 非対称鍵でデータ検証
Secure Key Managerに作成した非対称鍵で、データを検証する時に使用します。ユーザーはデータと署名値を転送して、Secure Key Managerに保存した非対称鍵でデータが改ざんされていないかを検証できます。
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
| 値 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 非対称鍵で検証するデータ |
| signature | String | 非対称鍵でデータを署名した署名値 |

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
| 値 | タイプ | 説明 |
|---|---|---|
| result | Boolean | 非対称鍵でデータと署名値を検証した結果 |
| keyVersion | Number | APIリクエスト処理に使用した非対称鍵バージョン |
